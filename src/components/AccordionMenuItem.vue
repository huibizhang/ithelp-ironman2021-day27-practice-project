<template>
  <div class="w-80">
    <label
      :class="[
        'px-4 py-2',
        'border border-gray-300',
        'hover:bg-gray-100',
        'flex justify-between items-center',
        'cursor-pointer',
        'transition-all',
      ]"
    >
      <input type="checkbox" class="sr-only" v-model="checked" />
      <div 
        :class="[
          checked && 'text-green-500',
          'transition-all'
        ]"
      >
        {{ itemName }}
      </div>
      <div
        :class="[
          'w-9 h-9',
          'hover:bg-gray-200',
          'rounded-full',
          'flex justify-center items-center',
          'transition-all',
        ]"
      >
        <svg 
          xmlns="http://www.w3.org/2000/svg" 
          fill="none" viewBox="0 0 24 24" stroke="currentColor"
          :class="[
            'h-6 w-6',
            checked && '-rotate-180',
            'transition-all'
          ]"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
        </svg>
      </div>
    </label>
    <div
      :class="[
        checked ? 'max-h-[300px]' : 'max-h-0',
        'border border-t-0 border-gray-300',
        'overflow-hidden transition-all'
      ]"
    >
      <slot name="itemContent">
        <div class="p-4 text-gray-600">
          <slot name="itemText">
            內容
          </slot>
        </div>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "AccordionMenuItem",
  props: {
    itemName: {
      default: "選項",
    }
  },
  data() {
    return {
      checked: false,
    }
  },
}
</script>