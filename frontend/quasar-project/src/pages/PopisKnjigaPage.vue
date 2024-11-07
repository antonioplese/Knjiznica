<template>
  <q-page padding>
    <q-card>
      <q-card-section>
        <div class="text-h5">Popis svih knjiga</div>
      </q-card-section>
      <q-card-section>
        <q-table
          :rows="allBooks"
          :columns="columns"
          row-key="id"
          flat
        />
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  setup() {
    // Dummy podaci za knjige
    const allBooks = [
      { id: 1, title: 'Na Drini ćuprija', author: 'Ivo Andrić' },
      { id: 2, title: 'Zločin i kazna', author: 'Fjodor Dostojevski' },
      { id: 3, title: 'Prokleta avlija', author: 'Ivo Andrić' },
      { id: 4, title: 'Ana Karenjina', author: 'Lav Tolstoj' },
      { id: 5, title: 'Rat i mir', author: 'Lav Tolstoj' },
    ];

    const columns = [
      { name: 'id', label: 'ID', field: 'id', align: 'left' },
      { name: 'title', label: 'Naslov', field: 'title', align: 'left' },
      { name: 'author', label: 'Autor', field: 'author', align: 'left' },
    ];

    return {
      allBooks,
      columns,
    };
  },
};
</script>
