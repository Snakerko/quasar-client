<template>
	<q-page padding class="docs-table">
    <p class="caption">Dictionaries</p>
    <addForm></addForm>
    <q-table
      :data="dicts"
      :columns="columns"
      row-key="name"
      color="primary"
    >
      <div slot="bottom" slot-scope="props" class="row flex-center fit">
        <q-btn
          round dense icon="chevron_left" color="primary" class="q-mr-md"
          :disable="props.isFirstPage"
          @click="props.prevPage"
        />
        <q-btn
          round dense icon="chevron_right" color="primary"
          :disable="props.isLastPage"
          @click="props.nextPage"
        />
      </div>
		</q-table>
	</q-page>
</template>

<script>
import axios from 'axios'
import addForm from './addForm'

export default {
	name: 'Dict',
	data () {
		return {
			dicts: [],
			columns: [
				{
					name: 'desc',
					required: true,
					label: 'name',
					align: 'left',
					field: 'name',
					sortable: true
				},
				{
					name: 'desc',
					required: true,
					label: 'synonym',
					align: 'left',
					field: 'synonyms',
					sortable: true
				},
				{
					name: 'desc',
					required: true,
					label: 'GUID',
					align: 'left',
					field: 'guid',
					sortable: true
				}
			]
		}
	},
	components: {
		addForm: addForm
	},
	mounted () {
		axios.get('http://localhost:8000/api/dict/' + this.$route.params.page)
			.then(response => (this.dicts = response.data.items))
	}
}
</script>
