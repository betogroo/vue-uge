<script setup lang="ts">
const colors = ['#394053', '#4E4A59', '#6E6362', '#839073', '#7CAE7A']
const biddings = [
  {
    id: 1,
    title: 'Material de Consumo',
    subtitle: 'Material de Limpeza e Higiene Pessoal',
  },
  {
    id: 2,
    title: 'Material de Consumo',
    subtitle: 'Gêneros Alimentícios',
  },
  {
    id: 3,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 4,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 5,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 6,
    title: 'Material de Consumo',
    subtitle: 'Material de Limpeza e Higiene Pessoal',
  },
  {
    id: 7,
    title: 'Material de Consumo',
    subtitle: 'Gêneros Alimentícios',
  },
  {
    id: 8,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 9,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 10,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 11,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 12,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
  {
    id: 13,
    title: 'Material de Consumo',
    subtitle: 'Material de Escritório e Papelaria',
  },
]

const getColor = (index: number) => {
  if (index < colors.length) return colors[index]
  else {
    const baseColorIndex = index % colors.length
    const variation = Math.floor(index / colors.length)
    return shadeColor(colors[baseColorIndex], variation * 40)
  }
}

const shadeColor = (color: string, percent: number) => {
  const num = parseInt(color.slice(1), 16),
    amt = Math.round(2.55 * percent),
    R = (num >> 16) + amt,
    G = ((num >> 8) & 0x00ff) + amt,
    B = (num & 0x0000ff) + amt
  return `#${(
    0x1000000 +
    (R < 255 ? (R < 1 ? 0 : R) : 255) * 0x10000 +
    (G < 255 ? (G < 1 ? 0 : G) : 255) * 0x100 +
    (B < 255 ? (B < 1 ? 0 : B) : 255)
  )
    .toString(16)
    .slice(1)
    .toUpperCase()}`
}
</script>
<template>
  <v-container class="d-flex justify-center fill-height">
    <v-row justify="center">
      <v-col
        v-for="(bidding, index) in biddings"
        :key="bidding.id"
        cols="12"
        md="4"
      >
        <v-card
          class="mx-auto rounded-lg border-dashed"
          :color="getColor(index)"
          max-width="344"
          variant="flat"
        >
          <v-card-title>{{ bidding.title }}</v-card-title>
          <v-card-subtitle>{{ bidding.subtitle }}</v-card-subtitle>
          <v-card-subtitle>Ultima Atualização</v-card-subtitle>
          <v-card-subtitle>16 itens</v-card-subtitle>
          <v-divider></v-divider>
          <v-card-subtitle>16 itens</v-card-subtitle>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
