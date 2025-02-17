<template>
  <div class="bg-gray-100 flex-grow pt-6 pb-16 shadow-inner">
    <div class="max-w-screen-2xl md:px-12 mx-auto">
      <div class="flex lg:space-x-5">
        <!-- First column-->
        <div class="hidden lg:flex flex-col lg:w-1/5 space-y-5">
          <AccountNavigation></AccountNavigation>
        </div>

        <!-- Second column-->
        <div class="flex flex-col w-full lg:w-4/5 space-y-5">
          <div class="flex justify-between items-center mx-5 lg:mx-0">
            <h2 class="text-gray-800 text-3xl font-bold uppercase">Profile</h2>
          </div>
          <div class="flex flex-col bg-white shadow-sm p-6" :class="{ 'rounded border polygon-bg': !isMobile }">
            <form @submit="onSubmit" class="lg:w-1/2 flex flex-col">
              <!-- Errors block -->
              <VcAlert v-if="updateProfileError" type="error" class="mb-2" icon text>
                There was an error during profile update
              </VcAlert>

              <VcInput
                v-model="firstName"
                name="firstName"
                class="mb-4"
                label="First name"
                placeholder="First Name"
                is-required
                :error-message="errors.firstName"
              ></VcInput>

              <VcInput
                v-model="lastName"
                name="lastName"
                class="mb-4"
                label="Last name"
                placeholder="Last name"
                is-required
                :error-message="errors.lastName"
              ></VcInput>

              <VcInput
                v-model="email"
                name="email"
                class="mb-4"
                label="Email"
                placeholder="Email"
                is-disabled
              ></VcInput>

              <!-- Form actions -->
              <div class="mt-6 lg:mt-4 w-1/2 self-center lg:self-auto">
                <VcButton
                  is-submit
                  size="lg"
                  class="uppercase mt-6 lg:mt-3 w-full lg:w-48"
                  :is-waiting="!isSubmitEnabled"
                >
                  Update
                </VcButton>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { VcAlert, VcButton, VcInput } from "@/components";
import { AccountNavigation, ProfileUpdateSuccessDialog, useUser } from "@/shared/account";
import { reactive, computed, Ref, ref } from "vue";
import { breakpointsTailwind, useBreakpoints } from "@vueuse/core";
import { useForm, useField } from "vee-validate";
import * as yup from "yup";
import { usePopup } from "@/shared/popup";

const { me, loading, updateUser } = useUser();
const { openPopup } = usePopup();

const updateProfileError: Ref<boolean> = ref(false);

const schema = yup.object({
  firstName: yup.string().label("First name").required().max(64),
  lastName: yup.string().label("Last name").required().max(64),
  email: yup.string().label("Email"),
});

const { errors, handleSubmit, isSubmitting } = useForm({
  validationSchema: schema,
  initialValues: {
    firstName: me.value.contact?.firstName,
    lastName: me.value.contact?.lastName,
    email: me.value.email,
  },
});

const { value: firstName } = useField<string>("firstName");
const { value: lastName } = useField<string>("lastName");
const { value: email } = useField<string>("email");

const model = reactive({ firstName, lastName });

const breakpoints = useBreakpoints(breakpointsTailwind);

const isMobile = breakpoints.smaller("md");

// submit
const isSubmitEnabled = computed(() => !isSubmitting.value && !loading.value);

const onSubmit = handleSubmit(async () => {
  var result = await updateUser(model);
  if (result.succeeded) {
    openPopup({
      component: ProfileUpdateSuccessDialog,
    });
  } else {
    updateProfileError.value = true;
  }
});
</script>

<style scoped>
.polygons-bg {
  background-image: url(/static/images/account/addresses-bg.svg);
  background-repeat: no-repeat;
  background-position: right;
}
</style>
