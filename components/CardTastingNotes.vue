<template>
  <div v-if="!checkSomeProps">
    <div class="mx-auto bg-white shadow-lg rounded-lg my-32 px-4 py-4 max-w-sm">
      <div class="mb-1 tracking-wide px-4 py-4">
        <h2 class="text-gray-800 font-semibold mt-1">{{ title }}</h2>
        <div class="-mx-8 px-8">
          <div v-for="note in tastingNotes" :key="note.name">
            <div class="flex items-center mt-1">
              <div class="w-2/5 text-indigo-500 tracking-tighter capitalize">
                <span>{{ note.name }}</span>
              </div>
              <div class="w-3/5">
                <div class="bg-gray-300 w-full rounded-lg h-2">
                  <div
                    class="bg-indigo-600 rounded-lg h-2"
                    :class="note.point"
                  ></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardTastingNotes',
  props: {
    notes: { type: Object, required: true },
    title: { type: String, default: 'Tasting Notes' },
  },
  data() {
    return {
      checkSomeProps: !!(
        this.notes.bitterness === null &&
        this.notes.hoppyness === null &&
        this.notes.maltyness === null
      ),
      tastingNotes: [
        {
          name: 'bitterness',
          point: `w-${Math.round(this.notes.bitterness * 12)}/12`,
        },
        {
          name: 'hoppyness',
          point: `w-${Math.round(this.notes.hoppyness * 12)}/12`,
        },
        {
          name: 'maltyness',
          point: `w-${Math.round(this.notes.maltyness * 12)}/12`,
        },
      ],
    }
  },
}
</script>
