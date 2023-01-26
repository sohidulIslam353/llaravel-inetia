<script setup>
import { ref } from 'vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Topbar from '@/Components/Topbar.vue';
import Sidebar from '@/Components/Sidebar.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/vue3';

const showingNavigationDropdown = ref(false);
</script>

<template>
    <div>
      <div>
        <div class="main-wrapper main-wrapper-1">
          <div class="navbar-bg"></div>
            <Topbar/>
            <Sidebar/>
            <slot/>
          </div>
        </div>
    </div>

</template>
