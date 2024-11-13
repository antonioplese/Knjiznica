<template>
  <q-page padding>
    <q-card>
      <q-card-section>
        <div class="text-h5">Pretraga knjige</div>
      </q-card-section>

      <q-card-section>
        <q-input
          v-model="searchTitle"
          placeholder="Unesi naslov knjige"
          @input="searchBook"
          outlined
          clearable
        />
      </q-card-section>

      <q-card-section>
        <q-table
          v-if="filteredBooks.length > 0"
          :rows="filteredBooks"
          :columns="columns"
          row-key="id"
          flat
        />
        <div v-else class="text-subtitle1 text-grey-7">
          Knjiga nije pronađena.
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  setup() {
    const allBooks = [
  { id: 1, title: 'Na Drini ćuprija', author: 'Ivo Andrić' },
  { id: 2, title: 'Zločin i kazna', author: 'Fjodor Dostojevski' },
  { id: 3, title: 'Prokleta avlija', author: 'Ivo Andrić' },
  { id: 4, title: 'Ana Karenjina', author: 'Lav Tolstoj' },
  { id: 5, title: 'Rat i mir', author: 'Lav Tolstoj' },
  { id: 6, title: 'Braća Karamazovi', author: 'Fjodor Dostojevski' },
  { id: 7, title: 'Idiot', author: 'Fjodor Dostojevski' },
  { id: 8, title: 'Gordana', author: 'Marija Jurić Zagorka' },
  { id: 9, title: 'Povratak Filipa Latinovicza', author: 'Miroslav Krleža' },
  { id: 10, title: 'Dundo Maroje', author: 'Marin Držić' },
  { id: 11, title: 'Oproštaj s tri trešnje', author: 'Stjepan Čuić' },
  { id: 12, title: 'Posljednji Stipančići', author: 'Vjenceslav Novak' },
  { id: 13, title: 'Opat', author: 'Walter Scott' },
  { id: 14, title: 'Lovac u žitu', author: 'J.D. Salinger' },
  { id: 15, title: 'Starac i more', author: 'Ernest Hemingway' },
  { id: 16, title: 'Ponos i predrasude', author: 'Jane Austen' },
  { id: 17, title: 'Razum i osjećaji', author: 'Jane Austen' },
  { id: 18, title: 'Zov divljine', author: 'Jack London' },
  { id: 19, title: 'Martin Eden', author: 'Jack London' },
  { id: 20, title: 'Romeo i Julija', author: 'William Shakespeare' },
  { id: 21, title: 'Hamlet', author: 'William Shakespeare' },
  { id: 22, title: 'Makbeth', author: 'William Shakespeare' },
  { id: 23, title: 'Na zapadu ništa novo', author: 'Erich Maria Remarque' },
  { id: 24, title: 'Gospodar prstenova', author: 'J.R.R. Tolkien' },
  { id: 25, title: 'Hobit', author: 'J.R.R. Tolkien' },
  { id: 26, title: 'Mali princ', author: 'Antoine de Saint-Exupéry' },
  { id: 27, title: 'Kradljivica knjiga', author: 'Markus Zusak' },
  { id: 28, title: 'Dnevnik Anne Frank', author: 'Anne Frank' },
  { id: 29, title: 'Svijet po Garpu', author: 'John Irving' },
  { id: 30, title: 'Petar Pan', author: 'James M. Barrie' }
];

const columns = [
  { name: 'id', label: 'ID', field: 'id', align: 'left' },
  { name: 'title', label: 'Naslov', field: 'title', align: 'left' },
  { name: 'author', label: 'Autor', field: 'author', align: 'left' }
];


    const searchTitle = ref('');
    
    const filteredBooks = computed(() => {
      return allBooks.filter((book) =>
        book.title.toLowerCase().includes(searchTitle.value.toLowerCase())
      );
    });

    const searchBook = () => {
      if (searchTitle.value.trim() === '') {
        return allBooks;
      }
    };

    return {
      searchTitle,
      columns,
      filteredBooks,
      searchBook,
    };
  },
};
</script>