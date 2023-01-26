<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
      <Head title="Log in" />
       <div class="col-12 col-sm-8 offset-sm-2 col-md-6 offset-md-3 col-lg-6 offset-lg-3 col-xl-4 offset-xl-4">
            <div class="card card-primary">
              <div class="card-header">
                <h4>Login</h4>
              </div>
              <div class="card-body">
                <form @submit.prevent="submit" class="needs-validation" >
                  <div class="form-group">
                    <label for="email">Email</label>
                    <TextInput
                        id="email"
                        type="email"
                        class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-2 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
                        v-model="form.email"
                        required
                        autofocus
                        autocomplete="username"
                        placeholder="Email address"
                      />

                      <InputError class="mt-2"  :message="form.errors.email" />
                  </div>
                  <div class="form-group">
                    <div class="d-block">
                      <label for="password" class="control-label">Password</label>
                      <div class="float-right">
                        <Link
                            v-if="canResetPassword"
                            :href="route('password.request')"
                            class="underline text-sm text-gray-600 hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                        >
                            Forgot your password?
                        </Link>
                      </div>
                    </div>
                    <TextInput
                            id="password"
                            type="password"
                            class="relative block w-full appearance-none rounded-none rounded-t-md border border-gray-300 px-3 py-2 text-gray-900 placeholder-gray-500 focus:z-10 focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
                            v-model="form.password"
                            required
                            autocomplete="current-password"
                            placeholder="Password"
                        />

                <InputError class="mt-2" :message="form.errors.password" />
                  </div>
                  <div class="form-group">
                    <div class="custom-control custom-checkbox">
                      <Checkbox name="remember" v-model:checked="form.remember" />
                      <label class="ml-2" for="remember-me">Remember Me</label>
                    </div>
                  </div>
                  <div class="form-group">
                    <button type="submit" class="btn btn-primary btn-lg btn-block" tabindex="4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                      Login
                    </button>
                  </div>
                </form>
              
              </div>
            </div>

          </div>
       
    </GuestLayout>
</template>
