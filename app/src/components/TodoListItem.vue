<template>
  <div class="todo-item" :class="{ done: todoItem.completed }">
    <!-- 当todoItem为true时绑上class=done -->
    <label>
      <input type="checkbox" :checked="todoItem.completed" @click="$emit('change-state', $event)" />
      <!-- 为复选框绑定checked属性=todoIem.completed，同时绑定点击切换状态事件 -->
      {{ todoItem.content }}
      <span class="check-button"></span>
    </label>
  </div>
</template>

<script>
export default {
    name: "TodoListItem",
    props: ["todoItem"],
    // 用props接收todoList传来的todoItem
};
</script>

<style>
.todo-item {
  background: white;
  padding: 16px;
  border-radius: 8px;
  color: #626262;
}
.todo-item label {
  position: relative;
  display: flex;
  align-items: center;
}
.todo-item.done label {
    text-decoration: line-through;
    font-style: italic;
}
.todo-item label span.check-button {
  position: absolute;
  top: 0;
}
.todo-item label span.check-button::before,
.todo-item label span.check-button::after {
  content: "";
  display: block;
  position: absolute;
  width: 18px;
  height: 18px;
  border-radius: 50%;
}
.todo-item label span.check-button::before {
  border: 1px solid #b382f9;
}
.todo-item label span.check-button::after {
  transition: 0.4s;
  background: #b382f9;
  transform: translate(1px, 1px) scale(0.8);
  opacity: 0;
}
.todo-item input {
  opacity: 0;
  margin-right: 16px;
}
.todo-item input:checked + span.check-button::after {
  opacity: 1;
}
</style>