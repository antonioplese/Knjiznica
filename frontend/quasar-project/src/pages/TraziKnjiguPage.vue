<template>
  <q-page padding>
    <q-card>
      <q-card-section>
        <div class="text-h5">Pretraživanje knjiga</div>
      </q-card-section>

      <q-card-section>
        <q-input v-model="searchQuery" label="Pretraži knjige" filled />
        
        <q-checkbox 
          v-model="searchByAuthor" 
          label="Pretraži po autoru" 
        />
        
        <q-checkbox 
          v-model="searchByTitle" 
          label="Pretraži po naslovu" 
        />
        
        <q-btn 
          label="Traži" 
          @click="searchBooks" 
          color="primary" 
          class="q-mt-sm"
        />
      </q-card-section>

      <q-card-section>
        <q-table
          :rows="filteredBooks"
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

    const searchQuery = ref('');
    const searchByAuthor = ref(false);
    const searchByTitle = ref(false);

    const filteredBooks = computed(() => {
      if (!searchQuery.value) {
        return [];
      }

      return allBooks.filter((book) => {
        if (searchByAuthor.value && book.author.toLowerCase().includes(searchQuery.value.toLowerCase())) {
          return true;
        }
        if (searchByTitle.value && book.title.toLowerCase().includes(searchQuery.value.toLowerCase())) {
          return true;
        }
        return false;
      });
    });

    function searchBooks() {
      console.log('Searching books...');
    }

    return {
      allBooks,
      columns,
      searchQuery,
      searchByAuthor,
      searchByTitle,
      filteredBooks,
      searchBooks,
    };
  },
};
</script>
