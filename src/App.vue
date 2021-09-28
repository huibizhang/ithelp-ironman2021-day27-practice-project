<template>
  <div :class="[
      'w-screen h-screen',
      'flex flex-col',
      'items-center',
      'py-5'
    ]"
  >
    <AccordionMenuItem
      v-for="item in list.items"
      :key="list.groupName.concat('-',item.name)"
      :itemName="item.name"
    >
      <template v-slot:itemText>
        {{ item.content }}
      </template>
    </AccordionMenuItem>

    <br><br>
    <AccordionMenuItem
      v-for="link in faq.links"
      :key="faq.groupName.concat('-',link.name)"
      :itemName="link.name"
    >
      <template v-slot:itemContent>
        <div
          :class="[
            'p-3',
            'first:border-0 border-t',
            'hover:bg-gray-100 transition-all'
          ]"
          v-for="content in link.contents"
          :key="content"
        >
          {{ content }}
        </div>
      </template>
    </AccordionMenuItem>
  </div>
</template>

<script>
import AccordionMenuItem from './components/AccordionMenuItem.vue'

export default {
  data() {
    return {
      list: {
        groupName: "Abouts",
        items: [
          { name: "關於兔兔教", content: "不是邪教，但不太正常 (？)。 不過可以為你在此獻上教義 ... (住嘴！)"},
          { name: "關於 Tailwind CSS", content: "超讚了啦，不用真是太可惜了！"},
          { name: "關於手風琴", content: "流浪到淡水時有機會可以看到。"},
          { name: "關於兔兔", content: "你想知道的太多了，去擲筊問神吧！！！"}
        ]
      },
      faq: {
        groupName: "FAQ",
        links: [
          { name: "四大超商", contents: [
            "7-11","全家","萊爾富","OK",
          ]},
          { name: "付款方式", contents: [
            "現金","ATM","信用卡","LINE PAY","五倍券",
          ]},
          { name: "取貨方式", contents: [
            "宅配","超商取貨"
          ]},
        ]
      }
    }
  },
  components: {
    AccordionMenuItem,
  }
}
</script>