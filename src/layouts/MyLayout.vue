<template>
	<q-layout view="lHh Lpr lFf">
		<q-layout-header>
			<q-toolbar
				color="primary"
				:glossy="$q.theme === 'mat'"
				:inverted="$q.theme === 'ios'"
			>
				<q-btn
					flat
					dense
					round
					@click="leftDrawerOpen = !leftDrawerOpen"
					aria-label="Menu"
					icon="menu"
				/>

				<q-toolbar-title>
					Quasar App
					<div slot="subtitle">Running on Quasar v{{ $q.version }}</div>
				</q-toolbar-title>
			</q-toolbar>
		</q-layout-header>

		<q-layout-drawer
			v-model="leftDrawerOpen"
			:content-class="$q.theme === 'mat' ? 'bg-grey-2' : null"
		>
			<q-list
				no-border
				link
				inset-delimiter
			>
				<q-list no-border link inset-delimiter>
					<q-list-header>Navigation</q-list-header>
					<q-item to="/" exact>
						<q-item-side icon="home" />
						<q-item-main label="Home" />
					</q-item>
				</q-list>
				<q-collapsible link indent icon="mail" label="Словари" opened>

					<q-item to="/color">
						<q-item-side icon="receipt" />
						<q-item-main label="Цвета" />
					</q-item>
					<q-item to="/brand">
						<q-item-side icon="receipt" />
						<q-item-main label="Бренды" />
					</q-item>
					<q-item to="/distributor">
						<q-item-side icon="receipt" />
						<q-item-main label="Поставщики" />
					</q-item>
					<q-item to="/season">
						<q-item-side icon="receipt" />
						<q-item-main label="Сезоны" />
					</q-item>
					<q-item to="/size">
						<q-item-side icon="receipt" />
						<q-item-main label="Размеры" />
					</q-item>

				</q-collapsible>

				<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Заказы" />
				</q-item>
				<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Отчет" />
				</q-item>
				<q-collapsible indent link icon="send" label="Галерея">
					<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Заказы" />
					</q-item>
					<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Отшивы" />
					</q-item>
					<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Marchelas couture" />
					</q-item>
				</q-collapsible>
				<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Отборы" />
				</q-item>
				<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Замена GUID" />
				</q-item>
				<q-item to="#">
						<q-item-side icon="receipt" />
						<q-item-main label="Лог" />
				</q-item>
				<q-collapsible indent link icon="drafts" label="Команды">
					<div>...content...</div>
				</q-collapsible>
			</q-list>
		</q-layout-drawer>

		<q-page-container>
			<router-view />
		</q-page-container>
	</q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
	name: 'LayoutDefault',
	data () {
		return {
			leftDrawerOpen: this.$q.platform.is.desktop
		}
	},
	methods: {
		openURL
	}
}
</script>

<style>
</style>
