<template>
  <aside :class="`${is_expanded ? 'is-expanded' : ''}`">
		<div class="menu">
        <router-link to="/signout" class="button">
				<span class="material-icons">account_circle</span>
				<span class="text">Name Lastname</span>
			</router-link>
            </div>
		<div class="menu-toggle-wrap">
			<button class="menu-toggle" @click="ToggleMenu">
				<span class="material-icons bounce">keyboard_double_arrow_right</span>
			</button>
		</div>

		<div class="menu">
			<router-link to="/" class="button">
				<span class="material-icons">home</span>
				<span class="text">Home</span>
			</router-link>
			<router-link to="/shoppinglist" class="button">
				<span class="material-icons">shopping_cart</span>
				<span class="text">Shopping list</span>
			</router-link>
			<router-link to="/liabilities" class="button">
				<span class="material-icons">local_laundry_service</span>
				<span class="text">Liabilities</span>
			</router-link>
			<router-link to="/messages" class="button">
				<span class="material-icons">email</span>
				<span class="text">Messages</span>
			</router-link>
			<router-link to="/cars" class="button">
				<span class="material-icons">time_to_leave</span>
				<span class="text">Cars</span>
			</router-link>
			<router-link to="/obligations" class="button">
				<span class="material-icons">calendar_month</span>
				<span class="text">Obligations</span>
			</router-link>
			<router-link to="/bills" class="button">
				<span class="material-icons">savings</span>
				<span class="text">Bills</span>
			</router-link>
			<router-link to="/lunchs" class="button">
				<span class="material-icons">local_dining</span>
				<span class="text">Lunch</span>
			</router-link>
		</div>

		<div class="flex"></div>
		
		<div class="menu">
			<router-link to="/settings" class="button">
				<span class="material-icons">settings</span>
				<span class="text">Settings</span>
			</router-link>
		</div>
	</aside>
</template>

<script setup>
import { ref } from 'vue'

const is_expanded = ref(localStorage.getItem("is_expanded") === "true")
const ToggleMenu = () => {
    
	is_expanded.value = !is_expanded.value
	setTimeout(null, 1000);
	localStorage.setItem("is_expanded", is_expanded.value)
}
</script>

<style lang="scss" scoped>
 aside {
	display: flex;
	flex-direction: column;
	background-color: var(--fresh);
	color: var(--light);
	width: calc(2rem + 32px);
	overflow: hidden;
	min-height: 100vh;
	padding: 1rem;
	transition: 0.2s ease-in-out;
	.flex {
		flex: 1 1 0%;
	}
	
	.menu-toggle-wrap {
		display: flex;
		justify-content: flex-end;
		margin-bottom: 1rem;
		position: relative;
		top: 0;
		transition: 0.2s ease-in-out;
		.menu-toggle {
			transition: 0.3s ease-in-out;
            .bounce {
                position:relative;
                
                margin-top:0px;
                margin-left:0px;
                height:50px;
                width:50px;
                animation:bounce 1s infinite;
            }
    
            @keyframes bounce {
                0%       {left:5px; }
                25%, 75% {left:15px; }
                50%      {left:20px; }
                100%     {left: 0;}
            }
            
			.material-icons {
				font-size: 2rem;
				color: var(--light);
				transition: 0.2s ease-out;
			}
			
			&:hover {
				.material-icons {
					color: var(--sunshine);
					transform: translateX(0.5rem);
				}
			}
		}
	}
    button{
        background-color: var(--fresh);
        border: none;
    }   

	h3, .button .text {
		opacity: 0;
		transition: opacity 0.8s ease-in-out;
	}
	h3 {
		color: var(--sunshine);
		font-size: 0.875rem;
		margin-bottom: 0.5rem;
		text-transform: uppercase;
        text-align: center;
	}
	.menu {
		margin: 0 -1rem;
		.button {
			display: flex;
			align-items: center;
			text-decoration: none;
			transition: 0.2s ease-in-out;
			padding: 0.5rem 1rem;
			.material-icons {
				font-size: 2rem;
				color: var(--light);
				transition: 0.2s ease-in-out;
			}
			.text {
				color: var(--light);
				transition: 0.2s ease-in-out;
			}
			&:hover {
				background-color: var(--vermillion);
				.material-icons, .text {
					color: var(--light);
				}
			}
			&.router-link-exact-active {
				background-color: var(--vermillion);
				border-right: 5px solid var(--sunshine);
				.material-icons, .text {
					color: var(--light);
				}
			}
		}
	}
	
	&.is-expanded {
		width: var(--sidebar-width);
        	
			
			.menu-toggle {
				transform: rotate(180deg);
                transition: 0.3s;
			}
		
		h3, .button .text {
			opacity: 1;
		}
		.button {
			.material-icons {
				margin-right: 1rem;
			}
		}
		
	}
	@media (min--width: 896px) {
		position: absolute;
		z-index: 99;
	}
}
</style>