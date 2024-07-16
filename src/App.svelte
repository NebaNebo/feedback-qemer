<script>

import { writable } from "svelte/store";

let name = "";
let email = "";
let phone = "";
let Telegram = "";
let designSkills = [];
let usage = '';
let paymentMethod = '';
let heardAboutUs = '';
// debugger.log(name, email, answer, answer2, feedback, phone);

let successMessage = "";
let errorMessage = "";
let isLoading = false;
let showSubmitButton = false;
const token = writable('');

async function handleSubmit(event) {
    event.preventDefault();

    const formData = new FormData();
    formData.append("entry.1449596232", name);
    formData.append("entry.1486466929", email);
    formData.append("entry.1609330148", phone);
    formData.append("entry.1563992496", Telegram);
    formData.append("entry.40298639", designSkills);
    formData.append("entry.643182336", usage);
    formData.append("entry.1729006930", paymentMethod);
    formData.append("entry.1464605886", heardAboutUs);
    try {
      const response = await fetch(
        "https://docs.google.com/forms/d/e/1FAIpQLSejMMSsPkXvDa_8VoSaIyx-77NnWLf_L0spXOpQxY2L0jyrlg/formResponse",
        {
          method: "POST",
          mode: "no-cors",
          body: formData,


        }

      );

      if (response.ok || response.status === 0) {
        successMessage = "Thank you for your feedback!";
        errorMessage = "";
        name = "";
        email = "";
        phone = "";
      } else {



        successMessage = "";
   errorMessage = "There was an issue with your submission. Please try again.";

      }

    } catch (error) {
      successMessage = "";
      errorMessage =
        "There was an issue with your submission. Please try again.";
    }
  }



function startLoading() {
  isLoading = true;
  showSubmitButton = false;
}

  // $: isButtonDisabled = !(name && email && phone);
</script>

<nav class="flex">
  <div class="flex items-center max-w-screen-xl px-4 py-3 mx-auto jutify-center">
 <img src="logo2@4x.png" class="h-8" alt="" /> 
  </div>
</nav>

<section
  class="flex justify-center px-3 mt-2 lg:mx-9 lg:px-4"
  style="background: rgba( 0, 0, 0, 0.2 );
box-shadow: 0 8px 32px 0 rgba(12, 12, 12, 1);
backdrop-filter: blur( 4px );
-webkit-backdrop-filter: blur( 4px );
border-radius: 10px;
border: 2px solid rgba( 255, 255, 255, 0.18 );"
>
  <div
    class="grid max-w-screen-xl px-2 py-8 lg:gap-10 xl:gap-14 lg:py-16 lg:grid-cols-12"
  >
    <div class="mr-auto place-self-center lg:col-span-7">
    
      <div class="">
<img src="summer camp.svg" alt=""  class="scale-90 "/>
      <!-- <h1
      class="max-w-2xl mb-4 text-4xl leading-none tracking-tight md:text-5xl xl:text-6xl dark:text-white font-kodchasan pm"
    >
  
    Welcome to our Weekly Qemer Design Talk Feedback Form!
    </h1> -->

      <p
        class="sticky max-w-2xl mb-6 font-light opacity-60 lg:mb-8 md:text-lg lg:text-xl font-kodchasan pm"
      >
      Thank you for participating in our design talk sessions. We value your feedback and would love to hear your thoughts on how we can improve and make these sessions even more valuable for you.

      Please take a few minutes to complete this form. Your responses will help us tailor future sessions to better meet your interests and needs.
      </p>
    </div>
      <div class="flex flex-col items-start gap-6 my-3 submit-button">
        <p
        class="font-normal text-white text-1xl font-kodchasan opacity-60"
      >
        In collaboration with
      </p>
        <div class="flex gap-4">
        
          <img
            src="logo2@4x.png"
            alt=""
            class="h-8 transition-transform transform hover:scale-110"
          />
          <img
            src="/logo/hubbits1.png"
            alt=""
            class="h-8 transition-transform transform hover:scale-110"
          />
          <img
            src="/logo/Intuitio Ventures.jpg"
            alt=""
            class="h-8 transition-transform transform hover:scale-110"
          />
        </div>
      </div>

      
      <!-- <div class="flex justify-start gap-4 mx-2 mb-5 my-3over opacity-70">
        <a href="https://www.linkedin.com/company/qemer-design" class="transition-transform transform hover:scale-110">
          <i class="text-white scale-150 fa-brands fa-linkedin "></i></a>
          <a href="https://t.me/qemer_daily" class="transition-transform transform hover:scale-110"> <i class="text-white scale-150 fa-brands fa-telegram "></i></a>
        </div> -->

    </div>

    <div class=" lg:mt-0 lg:col-span-5 lg:flex">
      <div
        class="flex flex-col justify-center px-8 py-5 -mr-3 w-full m flex-shrink-0 rounded-[16px] bg-gradient-to-r from-[#ffae58] to-[#ffa200] border-1 border-[#00000055] hover:shadow-[3px_3px_0_0_#000000]  "
      >
        {#if successMessage}
          <div class="my-2 text-3xl font-semibold text-gray-900 font-kodchasan">
           <h3 class="text-xl font-semibold font-kodchasan "> <span class="text-2xl font-semibold font-kodchasan"><br> Thank you for your feedback!</span>
We appreciate your time and insights. Your input helps us improve our weekly design talk sessions and ensure they meet your needs and interests.</h3>
          </div>
          <div class="col-span-12">
            <div
              class="google-map border-[2px] shadow-md rounded-lg border-slate-800 opacity-75"
            >
        
            </div>
            <!-- <h3 class="my-2 font-semibold font-kodchasan opacity-80">
              Please mark your calendar for next Saturday, June 29, 2024.
            </h3> -->
          </div>
        {:else}
          <!-- <h1 class="text-2xl font-semibold font-kodchasan">form</h1> -->

          <form
            id="generated-form"
            class="mt-2 generated-form"
            on:submit={handleSubmit}
          >
            <div class="relative h-11 w-full min-w-[300px] mb-4">
              <input
                bind:value={name}
                name="entry.1449596232"
                placeholder=""
                class="peer text-[16px] h-full w-full border-b border-black bg-transparent pt-4 pb-1.5 font-sans text-sm font-normal text-blue-gray-700 outline outline-0 transition-all placeholder-shown:border-blue-gray-200 focus:border-gray-900 focus:outline-0 disabled:border-0 disabled:bg-blue-gray-50 placeholder:opacity-0 focus:placeholder:opacity-100 font-kodchasan font-semibold"
              />
              <label
                class="after:content[''] pointer-events-none absolute left-0 -top-1.5 flex h-full w-full select-none !overflow-visible truncate text-[16px] font-normal leading-tight text-gray-900 transition-all after:absolute after:-bottom-1.5 after:block after:w-full after:scale-x-0 after:border-b-2 after:border-gray-900 after:transition-transform after:duration-300 peer-placeholder-shown:text-sm peer-placeholder-shown:leading-[4.25] peer-placeholder-shown:text-blue-gray-500 peer-focus:text-[16px] peer-focus:leading-tight peer-focus:text-gray-900 peer-focus:after:scale-x-100 peer-focus:after:border-gray-900 peer-disabled:text-transparent peer-disabled:peer-placeholder-shown:text-blue-gray-500 font-kodchasan font-semibold"
              >
                Name
              </label>
            </div>
            <div class="relative h-11 w-full min-w-[300px] mb-4">
              <input
                bind:value={email}
                name="entry.1486466929"
                placeholder=""
                class="peer text-[16px] h-full w-full border-b border-black bg-transparent pt-4 pb-1.5 font-sans text-sm font-normal text-blue-gray-700 outline outline-0 transition-all placeholder-shown:border-blue-gray-200 focus:border-gray-900 focus:outline-0 disabled:border-0 disabled:bg-blue-gray-50 placeholder:opacity-0 focus:placeholder:opacity-100 font-kodchasan font-semibold"
              />
              <label
                class="after:content[''] pointer-events-none absolute left-0 -top-1.5 flex h-full w-full select-none !overflow-visible truncate text-[16px] font-normal leading-tight text-gray-900 transition-all after:absolute after:-bottom-1.5 after:block after:w-full after:scale-x-0 after:border-b-2 after:border-gray-900 after:transition-transform after:duration-300 peer-placeholder-shown:text-sm peer-placeholder-shown:leading-[4.25] peer-placeholder-shown:text-blue-gray-500 peer-focus:text-[16px] peer-focus:leading-tight peer-focus:text-gray-900 peer-focus:after:scale-x-100 peer-focus:after:border-gray-900 peer-disabled:text-transparent peer-disabled:peer-placeholder-shown:text-blue-gray-500 font-kodchasan font-semibold"
              >
                Email
              </label>
            </div>

            <div class="relative h-11 w-full min-w-[300px] mb-4">
              <input
                bind:value={phone}
                name="entry.1609330148"
                placeholder=""
                class="peer text-[16px] h-full w-full border-b border-black bg-transparent pt-4 pb-1.5 font-sans text-sm font-normal text-blue-gray-700 outline outline-0 transition-all placeholder-shown:border-blue-gray-200 focus:border-gray-900 focus:outline-0 disabled:border-0 disabled:bg-blue-gray-50 placeholder:opacity-0 focus:placeholder:opacity-100 font-kodchasan font-semibold"
              />
              <label
                class="after:content[''] pointer-events-none absolute left-0 -top-1.5 flex h-full w-full select-none !overflow-visible truncate text-[16px] font-normal leading-tight text-gray-900 transition-all after:absolute after:-bottom-1.5 after:block after:w-full after:scale-x-0 after:border-b-2 after:border-gray-900 after:transition-transform after:duration-300 peer-placeholder-shown:text-sm peer-placeholder-shown:leading-[4.25] peer-placeholder-shown:text-blue-gray-500 peer-focus:text-[16px] peer-focus:leading-tight peer-focus:text-gray-900 peer-focus:after:scale-x-100 peer-focus:after:border-gray-900 peer-disabled:text-transparent peer-disabled:peer-placeholder-shown:text-blue-gray-500 font-kodchasan font-semibold"
              >
                phone number
              </label>
            </div>

            <div class="relative h-11 w-full min-w-[300px] mb-4">
              <input
                bind:value={Telegram}
                name="entry.1609330148"
                placeholder=""
                class="peer text-[16px] h-full w-full border-b border-black bg-transparent pt-4 pb-1.5 font-sans text-sm font-normal text-blue-gray-700 outline outline-0 transition-all placeholder-shown:border-blue-gray-200 focus:border-gray-900 focus:outline-0 disabled:border-0 disabled:bg-blue-gray-50 placeholder:opacity-0 focus:placeholder:opacity-100 font-kodchasan font-semibold"
              />
              <label
                class="after:content[''] pointer-events-none absolute left-0 -top-1.5 flex h-full w-full select-none !overflow-visible truncate text-[16px] font-normal leading-tight text-gray-900 transition-all after:absolute after:-bottom-1.5 after:block after:w-full after:scale-x-0 after:border-b-2 after:border-gray-900 after:transition-transform after:duration-300 peer-placeholder-shown:text-sm peer-placeholder-shown:leading-[4.25] peer-placeholder-shown:text-blue-gray-500 peer-focus:text-[16px] peer-focus:leading-tight peer-focus:text-gray-900 peer-focus:after:scale-x-100 peer-focus:after:border-gray-900 peer-disabled:text-transparent peer-disabled:peer-placeholder-shown:text-blue-gray-500 font-kodchasan font-semibold"
              >
              Telegram Username
              </label>
            </div>


            <div class="mb-4 " data-item-id="1471615486">
              <p class="-mt-2 font-semibold font-kodchasan text-[#111827] my-2">
                How skilled are you in design?
                <span class="text-red-500">*</span>
              </p>
              
              <label for="Absolute0" class="flex items-center">
                <input
                  type="checkbox"
                  bind:group={designSkills}
                  value="Absolute 0"
                  id="Absolute0"
                  name="designSkills"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Absolute 0</span>
              </label>
              
              <label for="KnowTools" class="flex items-center">
                <input
                  type="checkbox"
                  bind:group={designSkills}
                  value="I know how to use the tools"
                  id="KnowTools"
                  name="designSkills"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">I know how to use the tools</span>
              </label>
              
              <label for="WorkedAsDesigner" class="flex items-center">
                <input
                  type="checkbox"
                  bind:group={designSkills}
                  value="I've worked as a Graphic Designer"
                  id="WorkedAsDesigner"
                  name="designSkills"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">I've worked as a Graphic Designer</span>
              </label>
              
              <label for="MoreThan2Years" class="flex items-center">
                <input
                  type="checkbox"
                  bind:group={designSkills}
                  value="I've scored more than 2 years"
                  id="MoreThan2Years"
                  name="designSkills"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">I've scored more than 2 years</span>
              </label>
              
            </div>







            <div class="mb-3" data-item-id="1471615487">
              <p class="-mt-2 font-semibold font-kodchasan text-[#111827] my-2">
                How do you want to use your learned skill afterwards?
              </p>
              <label for="Freelance" class="flex items-center">
                <input
                  type="radio"
                  bind:group={usage}
                  value="Freelance"
                  id="Freelance"
                  name="usage"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Freelance</span>
              </label>
            
              <label for="Employed as a designer" class="flex items-center">
                <input
                  type="radio"
                  bind:group={usage}
                  value="Employed as a designer"
                  id="Employed as a designer"
                  name="usage"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Employed as a designer</span>
              </label>
            
              <label for="Side hustle" class="flex items-center">
                <input
                  type="radio"
                  bind:group={usage}
                  value="Side hustle"
                  id="Side hustle"
                  name="usage"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Side hustle</span>
              </label>
            
              <label for="Complimentary skill" class="flex items-center">
                <input
                  type="radio"
                  bind:group={usage}
                  value="Complimentary skill"
                  id="Complimentary skill"
                  name="usage"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Complimentary skill</span>
              </label>
            </div>



<!-- ////////////////////////////////////////////////////////// -->


<div class="mb-3" data-item-id="1471615488">
  <p class="-mt-2 font-semibold font-kodchasan text-[#111827] my-2">
    Preferred Payment Method
  </p>
  <label for="AccountTransfer" class="flex items-center">
    <input
      type="radio"
      bind:group={paymentMethod}
      value="Account Transfer"
      id="AccountTransfer"
      name="paymentMethod"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Account Transfer</span>
  </label>

  <label for="Cash" class="flex items-center">
    <input
      type="radio"
      bind:group={paymentMethod}
      value="Cash"
      id="Cash"
      name="paymentMethod"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Cash</span>
  </label>

  <label for="Telebirr" class="flex items-center">
    <input
      type="radio"
      bind:group={paymentMethod}
      value="Telebirr"
      id="Telebirr"
      name="paymentMethod"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Telebirr</span>
  </label>
</div>






<div class="mb-3" data-item-id="1471615489">
  <p class="-mt-2 font-semibold font-kodchasan text-[#111827] my-2">
    Where did you hear about us?
  </p>
  <label for="Instagram" class="flex items-center">
    <input
      type="radio"
      bind:group={heardAboutUs}
      value="Instagram"
      id="Instagram"
      name="heardAboutUs"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Instagram</span>
  </label>

  <label for="Tiktok" class="flex items-center">
    <input
      type="radio"
      bind:group={heardAboutUs}
      value="Tiktok"
      id="Tiktok"
      name="heardAboutUs"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Tiktok</span>
  </label>

  <label for="Linkedin" class="flex items-center">
    <input
      type="radio"
      bind:group={heardAboutUs}
      value="Linkedin"
      id="Linkedin"
      name="heardAboutUs"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Linkedin</span>
  </label>

  <label for="Facebook" class="flex items-center">
    <input
      type="radio"
      bind:group={heardAboutUs}
      value="Facebook"
      id="Facebook"
      name="heardAboutUs"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">Facebook</span>
  </label>

  <label for="Friend" class="flex items-center">
    <input
      type="radio"
      bind:group={heardAboutUs}
      value="A friend"
      id="Friend"
      name="heardAboutUs"
      class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
    />
    <span class="ml-2 font-kodchasan">A friend</span>
  </label>
</div>









            <div class="flex flex-col items-end gap-6 my-3 submit-button">
        

            <button
            on:click={startLoading}
            type="submit"
            class=" align-center rounded-[8px] py-2.5 font-kodchasan font-bold px-5 relative inline-flex justify-center gap-x-2 text-sm tracking-[.00714em] border-2 border-black hover:-translate-y-0.5 shadow-[3px_3px_0_0_#000000] bg-yellow-200 hover:bg-yellow-300 focus:bg-yellow-400 text-black"
            
          >
            {#if isLoading}
              <div
                role="status"
                class="inline-block w-3 h-3 mt-1 border-2 border-current border-solid rounded-full align-center animate-spin border-r-transparent"
              >
                <span class="align-baseline sr-only">Loading...</span>
              </div>
              Loading
            {:else}
              <span> Submit</span>
            {/if}

      
          </button>
          <p>{successMessage}</p>
          <p>{errorMessage}</p>
          </form>
        {/if}
      </div>
    </div>
  </div>
</section>

<!-- 
<!--Footer container-->
<!-- <footer
  class="flex flex-col items-center text-center text-white">
  <div class="container pt-9">
  
    <div class="flex justify-center gap-4 mb-6 over">
    <a href="https://www.linkedin.com/company/qemer-design">
      <i class="scale-150 fa-brands fa-linkedin "></i></a>
      <a href="https://t.me/qemer_daily"> <i class="scale-150 fa-brands fa-telegram"></i></a>
    </div>
    <div class="w-full p-4 text-center bg-black/5">
      © 2024 Copyright: Qemer
    </div>
  </div>

  
</footer> 
 -->

<!--   
  <div class="flex flex-col items-center justify-center w-full h-full mt-5 lg:flex-row">
	<div class="flex flex-col px-8 py-5 w-full max-w-[430px] max-h-[1500px] flex-shrink-0 rounded-[16px] bg-gradient-to-r from-[#F1E104] to-[#F0A51F]">  dasgadgasgs</div>
<div class="flex flex-col p-3 my-5 h-[100%] ">
	
	
</div>
  </div> -->

<style>
  .pm {
    position: relative;
    text-transform: uppercase;
    font-size: 1em;
    font-weight:  15;
	letter-spacing: 2px;
  text-align: center;
	color: #f35626;
	background-image: -webkit-linear-gradient(92deg, #f35626, #feab3a);
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
	-webkit-animation: hue 10s infinite linear;
}

@-webkit-keyframes hue {
  from {
    -webkit-filter: hue-rotate(0deg);
  }
  to {
    -webkit-filter: hue-rotate(-360deg);
  }
}

</style>
