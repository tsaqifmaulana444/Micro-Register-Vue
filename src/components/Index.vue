<template>
  <div class=" flex justify-center align-middle items-center h-screen">
    <div class="bg-white sm:w-1/2 w-[80%] sm:h-[85vh] h-[120vh] rounded-md shadow-md sm:mt-0 mt-[100px]">
      <h1 class="text-center mt-8 text-[22px] font-semibold">Super Admin Registration</h1>
      <form @submit.prevent="submitForm">
        <div class="grid sm:grid-cols-2 grid-cols-1 gap-4 mt-12 px-9">
          <div class="flex flex-col mt-1">
            <label for="name">Name</label>
            <input v-model="formData.name" type="text" placeholder="Your name" id="name" class="border rounded-md h-10 px-2 text-[12px]" />
          </div>
          <div class="flex flex-col mt-1">
            <label for="email">Email</label>
            <input v-model="formData.email" type="text" placeholder="ex: test@gmail.com" id="email" class="border rounded-md h-10 px-2 text-[12px]" />
          </div>
          <div class="flex flex-col mt-1">
            <label for="phone_number">Phone Number</label>
            <input v-model="formData.phone_number" type="number" placeholder="ex: 86123456789" id="phone_number" class="border rounded-md h-10 px-2 text-[12px]" />
          </div>
          <div class="flex flex-col mt-1">
            <label for="password">Password</label>
            <input v-model="formData.password" type="password" placeholder="Use strong password" id="password" class="border rounded-md h-10 px-2 text-[12px]" />
          </div>
        </div>
        <div class="gap-4 mt-4 px-9">
          <div class="flex flex-col mt-4">
            <label for="birth_date">Birth Date</label>
            <input v-model="formData.birth_date" type="date" id="birth_date" class="border rounded-md h-10 px-2 text-[12px]" />
          </div>
          <div class="flex flex-col mt-4">
            <label for="address">Address</label>
            <input v-model="formData.address" type="text" placeholder="Your address" id="address" class="border rounded-md h-10 px-2 text-[12px]" />
          </div>
        </div>
        <div class="w-full px-9 mt-8">
          <button type="submit" class="bg-[#141414] text-white w-full h-10 rounded-md">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      formData: {
        name: '',
        email: '',
        address: '',
        phone_number: '',
        birth_date: '',
        password: ''
      }
    }
  },
  methods: {
    async submitForm() {
      console.log("data: ", this.formData)
      try {
        const response = await fetch('http://127.0.0.1:8000/api/register-super-admin', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(this.formData)
        })

        if (!response.ok) {
          throw new Error('Network response was not ok')
        }

        alert('Registration successful!')
        window.reload()
      } catch (error) {
        console.error('There was an error submitting the form:', error)
      }
    }
  }
}
</script>