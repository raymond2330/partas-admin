<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head,router  } from '@inertiajs/vue3';
import { defineProps, watchEffect } from 'vue';
import PrimaryButton from '@/Components/PrimaryButton.vue'
import { reactive,ref } from 'vue'
import InputLabel from '@/Components/InputLabel.vue'
import TextInput from '@/Components/TextInput.vue'


  const form=reactive({
      location: "",
  })

  const props = defineProps({
    message : String
  })

  watchEffect(() => {
      if (props.message){
          console.log(props.message)
          alert(props.message);
        }
    })
        
  function submit() {
    router.post(route("location.store"),form);
  }



</script>

<template>
    <Head title="Create Location" />

    <AuthenticatedLayout>


        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">

                <div class="overflow-hidden ma-8 w-100  bg-[#919abc] rounded-lg p-5  shadow-xs">
                    <div class="flex md:items-center m-6">
                            <form class="w-full max-w-sm"  @submit.prevent="submit">
                                <div class="md:w-1/3">
                                <InputLabel for="location" class="" value="Location"/>
                                </div>
                                <div class="block w-full text-gray-900">
                                    <TextInput  id="location"  type="text" v-model="form.location" required />
                                </div>

                                <div class=" py-3 md:w-1/3">
                                <PrimaryButton type="submit"> Submit  </PrimaryButton>
                                </div>
                            </form>
                    </div>
                </div>
            </div>
        </div>

    </AuthenticatedLayout>
</template>
