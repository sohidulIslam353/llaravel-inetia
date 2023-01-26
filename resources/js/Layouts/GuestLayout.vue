<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Link } from '@inertiajs/vue3';
</script>

<template>
    <div>
      <section class="section">
        <div class="container mt-5">
          <div class="row">
            <slot/>
          </div>
        </div>
      </section>
    </div>
</template>
