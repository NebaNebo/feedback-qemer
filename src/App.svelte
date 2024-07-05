<script>

import { writable } from "svelte/store";

let name = "";
let email = "";
let answer = "";
let answer2 = "";
let feedback = "";
let phone = "";

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
    formData.append("entry.643182336", answer);
    formData.append("entry.40298639", answer2);
    formData.append("entry.1729006930", feedback);
    try {
      const response = await fetch(
        "https://docs.google.com/forms/d/e/1FAIpQLSc8fALOmuaY7unjDwpprolE85ff-oFoMlLPe_w4c6y5fOaqYg/formResponse",
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
        answer = "";
        phone = "";
        answer2 = "";
feedback = "";
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
  <div class="flex items-center max-w-screen-xl p-4 mx-auto jutify-center">
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
      
      <h1
      class="max-w-2xl mb-4 text-4xl leading-none tracking-tight md:text-5xl xl:text-6xl dark:text-white font-kodchasan pm"
    >
    
    Welcome to our Weekly Qemer Design Talk Feedback Form!
    </h1>

      <p
        class="max-w-2xl mb-6 font-light text-white opacity-60 lg:mb-8 md:text-lg lg:text-xl font-kodchasan"
      >
      Thank you for participating in our design talk sessions. We value your feedback and would love to hear your thoughts on how we can improve and make these sessions even more valuable for you.

      Please take a few minutes to complete this form. Your responses will help us tailor future sessions to better meet your interests and needs.
      </p>

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
        class="flex flex-col justify-center px-8 py-5 -mr-3 w-full m flex-shrink-0 rounded-[16px] bg-gradient-to-r from-[#ffc458] to-[#543703] border-1 border-[#00000055] hover:shadow-[3px_3px_0_0_#000000]"
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

            <div class="mb-3" data-item-id="1471615486">
              <p class="-mt-2 font-semibold font-kodchasan text-[#111827] my-2">
                How would you rate this week's design talk session?
              </p>
              <label for="yes" class="flex items-center">
                <input
                  type="radio"
                  bind:group={answer2}
                  value="Excellent"
                  id="Excellent"
                  name="answer2"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan"> Excellent</span>
              </label>

              <label for="no2" class="flex items-center">
                <input
                  type="radio"
                  bind:group={answer2}
                  value="Good"
                  id="Good"
                  name="answer2"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Good</span>
              </label>
              <label for="no" class="flex items-center">
                <input
                  type="radio"
                  bind:group={answer2}
                  value="Average"
                  id="Average"
                  name="answer2"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Average</span>
              </label>

              <label for="no" class="flex items-center">
                <input
                  type="radio"
                  bind:group={answer2}
                  value="Poor"
                  id="Poor"
                  name="answer2"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Poor</span>
              </label>


              
            </div>

<!-- /////////////////////////////////////////// -->

            <div class="mb-2" data-item-id="1471615486">
              <p class="-mt-2 font-semibold font-kodchasan text-[#111827] my-2">
                How did you hear about this design talk session?
              </p>
              <label for="yes" class="flex items-center">
                <input
                  type="radio"
                  bind:group={answer}
                  value="LinkedIn"
                  id="LinkedIn"
                  name="LinkedIn"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan"> LinkedIn</span>
              </label>

              <label for="no" class="flex items-center">
                <input
                  type="radio"
                  bind:group={answer}
                  value="Telegram"
                  id="Telegram"
                  name="Telegram"
                  class="appearance-none outline-none relative cursor-pointer w-5 h-5 before:rounded-sm before:block before:absolute before:content-[''] before:w-5 before:h-5 before:rounded-sm before:border-[#111827] before:border-2 after:block after:content-[''] after:absolute after:left-1.5 after:top-0.5 after:w-2 after:h-3 after:border-black after:border-r-2 after:border-b-2 after:origin-center after:rotate-45 after:opacity-0 checked:before:bg-[#000000] checked:after:opacity-1 transition-transform transform hover:scale-110"
                />
                <span class="ml-2 font-kodchasan">Telegram</span>
              </label>
            </div>
<!-- ////////////////////////////////////////////////////////// -->


<div class="relative h-11 w-full min-w-[300px] mb-4">
  <input
    bind:value={feedback}
    name="entry.1449596232"
    placeholder=""
    class="peer text-[16px] h-full w-full border-b border-black bg-transparent pt-4 pb-1.5 font-sans text-sm font-normal text-blue-gray-700 outline outline-0 transition-all placeholder-shown:border-blue-gray-200 focus:border-gray-900 focus:outline-0 disabled:border-0 disabled:bg-blue-gray-50 placeholder:opacity-0 focus:placeholder:opacity-100 font-kodchasan font-semibold"
  />
  <label
    class="after:content[''] pointer-events-none absolute left-0 -top-1.5 flex h-full w-full select-none !overflow-visible truncate text-[16px] font-normal leading-tight text-gray-900 transition-all after:absolute after:-bottom-1.5 after:block after:w-full after:scale-x-0 after:border-b-2 after:border-gray-900 after:transition-transform after:duration-300 peer-placeholder-shown:text-sm peer-placeholder-shown:leading-[4.25] peer-placeholder-shown:text-blue-gray-500 peer-focus:text-[16px] peer-focus:leading-tight peer-focus:text-gray-900 peer-focus:after:scale-x-100 peer-focus:after:border-gray-900 peer-disabled:text-transparent peer-disabled:peer-placeholder-shown:text-blue-gray-500 font-kodchasan font-semibold"
  >
  Any additional comments or feedback:
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
    font-size: 3em;
    font-weight:  150;
	letter-spacing: 2px;
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
