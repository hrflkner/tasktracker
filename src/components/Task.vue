<template>
    <div
        @dblclick="$emit('toggle-reminder', task.id)"
        :class="[
            task.reminder ? 'reminder' : '',
            'task',
            'disable-select',
            'mouse-hover',
        ]"
    >
        <h3>
            {{ task.text }}
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <div class="time-container">
            <p>{{ new Date(task.day).toDateString() }}</p>
            <p>{{ new Date(task.day).toLocaleTimeString() }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object,
    },
};
</script>

<style scope>
.fas {
    color: red;
}
.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
.task.reminder {
    border-left: 5px solid green;
}
.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.time-container {
    width: 65%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.disable-select {
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}
.mouse-hover:hover {
    background-color: rgba(38, 171, 82, 0.679);
    transition: all 0.1s ease-in-out;
}
</style>
