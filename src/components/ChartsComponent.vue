<template>
  <!-- //main div  -->
  <div
    id="main-div"
    ref="mainDivRef"
    class="flex flex-col-reverse space-y-4 md:flex-col p-4 md:min-h-screen md:justify-end"
  >
    <!-- div for charts  -->
    <div
      class="flex flex-col space-y-4 md:flex-row md:justify-between md:space-y-0 md:flex-1"
    >
      <!-- first chart -->
      <div class="flex md:flex-col-reverse md:items-center md:justify-start">
        <!-- title and img  -->
        <div
          class="flex space-x-2 justify-between w-[120px] md:flex-col-reverse md:items-center md:mt-4 md:space-x-0 md:min-h-[104px] md:justify-start"
        >
          <h3>Blackblaze</h3>
          <img class="h-6 w-6" src="../imgs/icon-backblaze.png" alt="" />
        </div>

        <!-- Chart  -->
        <div
          class="flex px-4 flex-1 md:flex-col-reverse md:text-center md:flex-1 md:h-full"
        >
          <div
            v-if="isMobile"
            class="bg-gray-400 w-2 max-w-[95%] h-6 chart blackblaze md:hidden"
            :style="`width: ${widthBlackblaze}%;min-width: 2px`"
          ></div>

          <div
            v-if="!isMobile"
            class="hidden bg-gray-400 w-2 max-w-[95%] h-6 chart blackblaze md:block md:w-10"
            :style="`height: ${widthBlackblaze}%;min-height: 2px`"
          ></div>

          <span class="pl-2 md:pl-0" v-if="totalBackblazeResult <= 7"
            >{{ minBackblazeResult }} $</span
          >
          <span class="pl-2 md:pl-0" v-else>{{ totalBackblazeResult }} $ </span>
        </div>
      </div>

      <!-- second chart -->
      <div class="flex md:flex-col-reverse">
        <!-- title and img  -->
        <div
          class="flex flex-col space-y-2 w-[120px] md:flex-col-reverse md:items-center md:mt-4"
        >
          <!-- div for title and img  -->
          <div
            class="flex space-x-2 justify-between md:flex-col-reverse md:space-x-0 md:items-center"
          >
            <h3>Bunny</h3>
            <img class="h-6 w-6" src="../imgs/icon-bunny.jpg" alt="" />
          </div>

          <!-- div for labels  -->
          <div class="flex flex-col w-[80px]">
            <div class="flex justify-between">
              <label for="hdd">HDD</label>
              <input
                id="hdd"
                name="bunnyRadio"
                type="radio"
                value="hdd"
                v-model="bunnyToggler"
                checked
              />
            </div>

            <div class="flex justify-between">
              <label for="ssd">SSD</label>
              <input
                id="ssd"
                name="bunnyRadio"
                type="radio"
                value="ssd"
                v-model="bunnyToggler"
              />
            </div>
          </div>
        </div>

        <!-- Chart  -->
        <div
          class="flex px-4 flex-1 md:flex-col-reverse md:text-center md:items-center md:flex-1 md:h-full"
        >
          <div
            v-if="isMobile"
            class="bg-gray-400 w-2 max-w-[95%] h-6 chart bunny md:hidden"
            :style="`width: ${widthBunny}%;min-width: 2px`"
          ></div>

          <div
            v-if="!isMobile"
            class="hidden bg-gray-400 w-2 max-w-[95%] h-6 chart bunny md:block md:w-10"
            :style="`height: ${widthBunny}%;min-height: 2px`"
          ></div>
          <span class="pl-2 md:pl-0" v-if="totalBunnyResult > 10">
            {{ maxBunnyResult }} $
          </span>
          <span class="pl-2 md:pl-0" v-else> {{ totalBunnyResult }} $</span>
        </div>
      </div>

      <!-- third chart -->
      <div class="flex md:flex-col-reverse">
        <!-- title and img  -->
        <div
          class="flex flex-col space-y-2 w-[120px] md:flex-col-reverse md:items-center md:mt-4"
        >
          <!-- div for title and img  -->
          <div
            class="flex space-x-2 justify-between md:flex-col-reverse md:space-x-0 md:items-center"
          >
            <h3>Scaleway</h3>
            <img class="h-6 w-6" src="../imgs/icon-scaleway.png" alt="" />
          </div>
          <!-- div for labels  -->
          <div class="flex flex-col w-[80px]">
            <div class="flex justify-between">
              <label for="single">Signle</label>
              <input
                id="single"
                name="scalewayRadio"
                type="radio"
                value="single"
                v-model="scalewayToggler"
                checked
              />
            </div>

            <div class="flex justify-between">
              <label for="multi">Multi</label>
              <input
                id="multi"
                name="scalewayRadio"
                type="radio"
                value="multi"
                v-model="scalewayToggler"
              />
            </div>
          </div>
        </div>

        <!-- Chart  -->
        <div
          class="flex px-4 flex-1 md:flex-col-reverse md:text-center md:items-center md:flex-1 md:h-full"
        >
          <div
            v-if="isMobile"
            class="bg-gray-400 w-2 max-w-[90%] h-6 chart scaleway md:hidden"
            :style="`width: ${widthScaleway}%;min-width: 2px`"
          ></div>

          <div
            v-if="!isMobile"
            class="hidden bg-gray-400 w-2 max-w-[95%] h-6 chart scaleway md:block md:w-10"
            :style="`height: ${widthScaleway}%;min-height: 2px`"
          ></div>

          <span class="pl-2 md:pl-0">{{ totalScalewayResult }} $</span>
        </div>
      </div>

      <!-- fourth chart -->
      <div class="flex md:flex-col-reverse md:justify-start">
        <!-- title and img  -->
        <div
          class="flex space-x-2 justify-between w-[120px] md:space-x-0 md:flex-col-reverse md:items-center md:mt-4 md:min-h-[104px] md:justify-start"
        >
          <h3>Vultr</h3>
          <img class="h-6 w-6" src="../imgs/icon-vultr.png" alt="" />
        </div>

        <!-- Chart  -->
        <div
          class="flex px-4 flex-1 md:flex-col-reverse md:items-center md:text-center md:flex-1 md:h-full"
        >
          <div
            v-if="isMobile"
            class="bg-gray-400 w-2 max-w-[95%] h-6 chart vultr md:hidden"
            :style="`width: ${widthVultr}%;min-width: 2px`"
          ></div>

          <div
            v-if="!isMobile"
            class="hidden bg-gray-400 w-2 max-w-[95%] h-6 chart vultr md:block md:w-10"
            :style="`height: ${widthVultr}%;min-height: 2px`"
          ></div>

          <span class="pl-2 md:pl-0" v-if="totalVultrResult <= 5"> 5 $</span>
          <span class="pl-2 md:pl-0" v-else> {{ totalVultrResult }} $</span>
        </div>
      </div>
    </div>

    <!-- div for inputs  -->
    <div
      class="flex space-y-4 p-4 flex-col items-center md:w-8/12 md:mx-auto md:space-x-0 md:space-y-4 md:items-center"
    >
      <!-- STORAGE  -->
      <div class="w-1/2">
        <label class="px-4" for="storage">Storage: {{ storageValue }} GB</label>
        <input
          class="block w-full"
          v-model="storageValue"
          @input="calcStorage"
          type="range"
          id="storage"
          min="0"
          max="1000"
          step="1"
        />
      </div>

      <!-- TransfER  -->
      <div class="w-1/2">
        <label for="transfer">Transfer: {{ transferValue }} GB</label>
        <input
          class="block w-full"
          v-model="transferValue"
          @input="calcTransfer"
          type="range"
          id="transfer"
          min="0"
          max="1000"
          step="1"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, watch, onMounted } from 'vue';

const storageValue = ref(0);
const transferValue = ref(0);

//results for charts
const storageBackblazeResult = ref(0);
const storageBunnyResult = ref(0);
const storageScalewayResult = ref(0);
const storageVultrResult = ref(0);

const transferBackblazeResult = ref(0);
const transferBunnyResult = ref(0);
const transferScalewayResult = ref(0);
const transferVultrResult = ref(0);

const mainDivRef = ref(null);
const isMobile = ref(null);

//COMPUTED
const totalBackblazeResult = computed(
  () =>
    +(storageBackblazeResult.value + transferBackblazeResult.value).toFixed(2)
);

const totalBunnyResult = computed(
  () => +(storageBunnyResult.value + transferBunnyResult.value).toFixed(2)
);

const totalScalewayResult = computed(
  () => +(storageScalewayResult.value + transferScalewayResult.value).toFixed(2)
);

const totalVultrResult = computed(
  () => +(storageVultrResult.value + transferVultrResult.value).toFixed(2)
);

//togglers
const bunnyToggler = ref('hdd');
const scalewayToggler = ref('single');

// HEIGHTs
const maxWidth = 74;

const widthBlackblaze = computed(() =>
  totalBackblazeResult.value <= 7
    ? 9.45946
    : (totalBackblazeResult.value * 100) / maxWidth
);

const widthBunny = computed(() =>
  totalBunnyResult.value > 10
    ? 13.5135
    : (totalBunnyResult.value * 100) / maxWidth
);

const widthScaleway = computed(
  () => (totalScalewayResult.value * 100) / maxWidth
);

const widthVultr = computed(() =>
  totalVultrResult.value <= 5
    ? 6.75676
    : (totalVultrResult.value * 100) / maxWidth
);

//fixed payments
const minBackblazeResult = 7;
const maxBunnyResult = 10;

// FUNCTIONS
//STORAGE
const calcStorage = () => {
  calcStorageBackblaze();
  calcStorageBunny();
  calcStorageScaleway();
  calcStorageVultr();
  showTheLowestPrice();
};

const calcStorageBackblaze = () => {
  storageBackblazeResult.value = +(storageValue.value * 0.005).toFixed(2);
};

const calcStorageBunny = () => {
  if (bunnyToggler.value === 'hdd') {
    storageBunnyResult.value = +(storageValue.value * 0.01).toFixed(2);
  } else {
    storageBunnyResult.value = +(storageValue.value * 0.02).toFixed(2);
  }
};

const calcStorageScaleway = () => {
  if (scalewayToggler.value === 'single') {
    storageScalewayResult.value =
      storageValue.value <= 75
        ? 0
        : +(storageValue.value * 0.03 - 2.25).toFixed(2);
  } else {
    storageScalewayResult.value =
      storageValue.value <= 75
        ? 0
        : +(storageValue.value * 0.06 - 4.5).toFixed(2);
  }
};

const calcStorageVultr = () => {
  storageVultrResult.value = +(storageValue.value * 0.01).toFixed(2);
};

//TRANSFER
const calcTransfer = () => {
  calcTransferBackblaze();
  calcTransferBunny();
  calcTransferScaleway();
  calcTransferVultr();
  showTheLowestPrice();
};

const calcTransferBackblaze = () => {
  transferBackblazeResult.value = +(transferValue.value * 0.01).toFixed(2);
};

const calcTransferBunny = () => {
  transferBunnyResult.value = +(transferValue.value * 0.01).toFixed(2);
};

const calcTransferScaleway = () => {
  transferScalewayResult.value =
    transferValue.value <= 75
      ? 0
      : +(transferValue.value * 0.02 - 1.5).toFixed(2);
};

const calcTransferVultr = () => {
  transferVultrResult.value = +(transferValue.value * 0.01).toFixed(2);
};

const updateWidth = () => {
  if (mainDivRef.value.clientWidth >= 768) {
    isMobile.value = false;
  } else {
    isMobile.value = true;
  }
};

//FOR THE LOWEST PRICE
const showTheLowestPrice = () => {
  // HERE WE HAVE ARRAY OF all heights (numbers)
  setTimeout(() => {
    const allWidths = [
      widthBlackblaze.value,
      widthBunny.value,
      widthScaleway.value,
      widthVultr.value,
    ];

    // HERE WE HAVE DIVS of all HEIGHTS
    let allItems = document.querySelectorAll('.chart');

    allItems.forEach((item) => item.classList.remove('lowest'));

    //SORTED COPY OF NUMBERS
    const sortedCopyAllWidths = allWidths.slice(0).sort((a, b) => a - b);

    //GET the lowest items and color them
    for (let i = 0; i < allItems.length; i++) {
      if (sortedCopyAllWidths[0] === allWidths[i]) {
        allItems[i].classList.add('lowest');
      }
    }
  }, 0);
};

//WATCHERS
//BUNNY TOGGLER WATHCER
watch(
  () => bunnyToggler.value,
  () => {
    calcStorageBunny();
    showTheLowestPrice();
  }
);

//SCALEWAY TOGGLER WATHCER
watch(
  () => scalewayToggler.value,
  () => {
    calcStorageScaleway();
    showTheLowestPrice();
  }
);

//isMobile, if we change screen we will check the lowest price again
watch(
  () => isMobile.value,
  (newValue, oldValue) => {
    if (newValue !== oldValue) {
      showTheLowestPrice();
    }
  }
);

//HOOKS
onMounted(() => {
  window.addEventListener('resize', updateWidth);
  updateWidth();
  calcStorage();
  calcTransfer();
});
</script>

<style scoped>
.blackblaze.lowest {
  background-color: red;
}

.bunny.lowest {
  background-color: orange;
}

.scaleway.lowest {
  background-color: purple;
}

.vultr.lowest {
  background-color: blue;
}
</style>
