<script setup>
import { ref } from "vue";
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
import EcosystemIcon from "./icons/IconEcosystem.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
import TodoAppVue from "./TodoApp.vue";
import FetchTodo from "./FetchTodo.vue";
import ChildComponent from "./ChildComponent.vue";
import EmitComponent from "./EmitComponent.vue";
import CounterApp from "./CounterApp.vue";

let greeting = "Hello from Father";
const childMsg = ref("No child msg yet");
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Todo App</template>
    <TodoAppVue />
  </WelcomeItem>

  <welcome-item>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Fetch Todo</template>
    <FetchTodo />
  </welcome-item>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Child Components</template>
    <h4>Props use on Father</h4>
    <ChildComponent :msg="greeting" />
    <br />
    <h4>Content from Chidren</h4>
    <ChildComponent />
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Emits</template>
    <EmitComponent @response="(msg) => (childMsg = msg)" />
    <p>{{ childMsg }}</p>
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Counter App</template>
    <counter-app />
  </WelcomeItem>
</template>
