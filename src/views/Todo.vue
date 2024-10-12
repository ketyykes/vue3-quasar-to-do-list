<script setup>
import { ref } from "vue";
const toDoListData = ref([]);
const newToDo = ref("");
function addTodo() {
	if (newToDo.value) {
		toDoListData.value.push({
			done: false,
			content: newToDo.value,
			id: Date.now(),
		});
		newToDo.value = "";
	}
}
function removeToDo(itemId) {
	toDoListData.value = toDoListData.value.filter((item) => item.id !== itemId);
}
function finishToDo(itemId) {
	toDoListData.value.forEach((item) => {
		if (item.id === itemId) {
			item.done = !item.done;
		}
	});
}
</script>

<template>
	<q-layout view="hHh Lpr fFf">
		<q-header elevated>
			<q-toolbar>
				<q-btn flat round dense icon="menu" class="q-mr-sm" />
				<q-avatar>
					<img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
				</q-avatar>
				<q-toolbar-title>Quasar Framework</q-toolbar-title>
			</q-toolbar>
		</q-header>

		<q-page-container>
			<q-page class="q-pa-md">
				<div class="row">
					<div class="col-12 col-sm-6 offset-sm-3">
						<q-card bordered class="my-card">
							<q-card-section>
								<div class="text-h6">To Do List</div>
							</q-card-section>
							<q-card-section>
								<div>
									<q-input
										label="輸入代辦事項"
										v-model="newToDo"
										@keyup.enter="addTodo"
										maxlength="7"
									>
										<template v-slot:after>
											<q-btn
												color="primary"
												round
												dense
												flat
												size="lg"
												icon="send"
												@click="addTodo"
											>
											</q-btn>
										</template>
									</q-input>
								</div>
							</q-card-section>

							<q-separator />
							<q-card-section>
								<div
									v-for="(item, index) in toDoListData"
									:key="index"
									class="flex justify-between items-center"
								>
									<div
										:class="[
											'text-h6',
											item.done === true ? 'text-strike' : '',
										]"
									>
										{{ item.content }}
									</div>
									<div>
										<q-btn
											size="lg"
											round
											dense
											flat
											icon="task_alt"
											@click="finishToDo(item.id)"
											:text-color="item.done === true ? 'positive' : 'dark'"
										>
										</q-btn>
										<q-btn
											size="lg"
											round
											dense
											flat
											icon="delete"
											@click="removeToDo(item.id)"
											text-color="negative"
										>
										</q-btn>
									</div>
								</div>
							</q-card-section>
						</q-card>
					</div>
				</div>
			</q-page>
		</q-page-container>

		<q-footer elevated>
			<q-toolbar>
				<q-toolbar-title class="text-center">Footer</q-toolbar-title>
			</q-toolbar>
		</q-footer>
	</q-layout>
</template>
