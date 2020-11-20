<script>
	import { Router, Route, navigate } from "svelte-routing";
	import Loadable from "svelte-loadable";
	
	import NavSidemenu from "./_components/NavSidemenu.svelte"
	import NavTop from "./_components/NavTop.svelte"
	
	import Login from "./Login.svelte";
	import CreateAccount from "./CreateAccount.svelte";
	import ForgotPassword from "./ForgotPassword.svelte";
	
	//This property is necessary declare to avoid ignore the Router
	let url = "";

	function lsAuth () {
		if (window.localStorage.getItem('auth')) {
			return JSON.parse(window.localStorage.getItem('auth'))
		}

		// else return their preferences
		return (false)
	}

	let auth = {
		isLogin: lsAuth(),
		isFlag: false
	}
	
	let sidemenu = {
		classBackdropShow: 'transition ease-in-out duration-150 opacity-100',
		classBackdropHide: 'transition ease-in-out duration-150 opacity-0',
		classOpen: 'transition ease-in-out duration-150 opacity-100',
		classClose: 'transition ease-in-out duration-150 opacity-0 transform -translate-x-20',
		isSidemenu: true,
		isSidemenuMobile: false
	}
	function toggleSideMenu(event) {
		sidemenu.isSidemenuMobile = event.detail.isSidemenu
	}
	function dismissSidemenu(event) {
		sidemenu.isSidemenuMobile = event.detail.isSidemenu
	}

	function handleLogin(event) {
		auth.isLogin = event.detail.isLogin
		auth.isFlag = false
		window.localStorage.setItem('auth', event.detail.isLogin)
		navigate("/dashboard", { replace: true });
	}
	function handleLogout(event) {
		auth.isLogin = event.detail.isLogin
		auth.isFlag = event.detail.isLogin
		window.localStorage.setItem('auth', event.detail.isLogin)
		navigate("/", { replace: true });
	}
	function handleLoginPage(event) {
		sidemenu.isSidemenuMobile = false
		auth.isFlag = event.detail.isLogin
	}
	function handleAaccount(event) {
		sidemenu.isSidemenuMobile = false
		auth.isFlag = event.detail.isLogin
		navigate("/pages/login", { replace: true });
	}

	if (window.localStorage.getItem('dark')) {
		if (window.localStorage.getItem('dark') === 'true') {
			window.document.body.classList.toggle('theme-dark')
		}
	}
</script>

<Router {url}>
{#if !auth.isLogin}
	<Login {auth} on:handleLogin={handleLogin} />
{:else}
	<div
		class="flex h-screen bg-gray-50 dark:bg-gray-900"
		style="display: {!auth.isFlag ? 'flex' : 'none'};"
	>
		<NavSidemenu {sidemenu} on:dismissSidemenu={dismissSidemenu} />
		<div class="flex flex-col flex-1 w-full">
			<NavTop {sidemenu} on:toggleSideMenu={toggleSideMenu} on:handleLogout={handleLogout} />

			<Route path="/dashboard">
				<Loadable loader={() => import("./pages/Dashboard.svelte")} />
			</Route>
			<Route path="/forms">
				<Loadable loader={() => import("./pages/Forms.svelte")} />
			</Route>
			<Route path="/cards">
				<Loadable loader={() => import("./pages/Cards.svelte")} />
			</Route>
			<Route path="/charts">
				<Loadable loader={() => import("./pages/Charts.svelte")} />
			</Route>
			<Route path="/buttons">
				<Loadable loader={() => import("./pages/Buttons.svelte")} />
			</Route>
			<Route path="/modals">
				<Loadable loader={() => import("./pages/Modals.svelte")} />
			</Route>
			<Route path="/tables">
				<Loadable loader={() => import("./pages/Tables.svelte")} />
			</Route>
			<Route path="/pages/404">
				<Loadable loader={() => import("./pages/Page404.svelte")} />
			</Route>
			<Route path="/pages/blank">
				<Loadable loader={() => import("./pages/Blank.svelte")} />
			</Route>
			<Route path="/">
				<Loadable loader={() => import("./pages/Home.svelte")} />
			</Route>
		</div>
	</div>

	<Route path="/pages/login">
		<Login {auth} on:handleLogin={handleLogin} on:handleLoginPage={handleLoginPage} />
	</Route>
	<Route path="/pages/create-account">
		<CreateAccount {auth} on:handleAaccount={handleAaccount} on:handleLoginPage={handleLoginPage} />
	</Route>
	<Route path="/pages/forgot-password">
		<ForgotPassword {auth} on:handleAaccount={handleAaccount} on:handleLoginPage={handleLoginPage} />
	</Route>
{/if}
	</Router>
