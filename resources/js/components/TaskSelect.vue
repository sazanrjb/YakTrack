<template>
    <div>
        <multi-select v-model="selectedTask" label="name" :options="tasks"></multi-select>
        <input type="hidden" name="task_id" :value="taskId">
    </div>
</template>

<script>

    import multiSelect from 'vue-multiselect';

    export default {
        props: [
            'tasks',
            'task'
        ],
        components: {
            multiSelect: multiSelect,
        },
        data() {
            var _this = this;

            return {
                selectedTask: this.tasks.find(function (task) {
                    return task.id == _this.task;
                }),
            }
        },
        computed: {
            taskId() {
                if (this.selectedTask == null) {
                    return null;
                }

                return this.selectedTask.id;
            }
        }
    }

</script>