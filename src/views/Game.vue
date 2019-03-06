<template>
  <v-container fluid style="min-height: 0;" grid-list-md>
    <v-layout row wrap>
      <v-flex md4>

        <v-card height="500" color="deep-purple darken-4"
        img="https://i.pinimg.com/originals/c3/35/f8/c335f88ab1e42a8f9c013e4630af2cf0.jpg" dark>
          <v-card color="transparent" v-for= "badDream in nightmare">
            <v-card-text class="headline">{{badDream}}</v-card-text>
          </v-card>
        </v-card>

      </v-flex>
      <v-flex md4>

        <v-layout column class="text-xs-center">
          <v-layout row justify-center align-center>

            <v-btn color="Nightmare" @click= "dreamerAcertou(false)">
              <v-icon>keyboard_arrow_left</v-icon> <span>Nightmare</span></v-btn>

            <v-btn color="Sweet Dreams" @click= "dreamerAcertou(true)">
              <span>Sweet Dreams</span> <v-icon>keyboard_arrow_right</v-icon></v-btn>

          </v-layout>

          <v-card height="335" img="http://www.pngall.com/wp-content/uploads/2016/09/Thought-Bubble-PNG-Image.png">
            <v-layout align-center justify-center fill-height>
              <v-card color="transparent" flat>
                <v-card-text class="headline">{{cartaJogada}}</v-card-text>
              </v-card>
            </v-layout>
          </v-card>

            <v-btn color="info" :disabled ="!mostrarBarraTempo" @click= "sortearCarta">Nova Palavra</v-btn>

            <v-btn color="error" @click= "iniciarTimer" v-if="!mostrarBarraTempo">START</v-btn>

          <v-progress-linear
            color="error"
            height="20"
            :value="progressoBarraTempo"
            v-else
          ></v-progress-linear>

        </v-layout>
      </v-flex>
      <v-flex md4>
        <v-card height="500" color="yellow lighten-4"
        img="https://s3.amazonaws.com/coursestorm/live/media/404200789a4711e88ea30e92b056efc0">
        <v-card color="transparent" v-for= "goodDream in dreams">
          <v-card-text class="headline">{{goodDream}}</v-card-text>
        </v-card>
        </v-card>
      </v-flex>
    </v-layout>

  </v-container>
</template>

<script>
export default {
  data: () => ({
    mostrarBarraTempo: false,
    deck: ["Laço", "Bola", "Caixa", "Vaca", "Nuvem", "Pintinho", "Acima", "Plugue", "Tesoura", "Anel",
       "Comida", "Mar", "Chupeta", "Pintinho", "Biscoito", "Um", "Cachos", "Guitarra", "Lâmpada", "Maçã",
       "Filha", "Uva", "Tartaruga", "Balanço", "Feio", "Golfinho", "Quadrado", "Corrida", "Orelha", "batom",
       "Fruta", "Palma", "Bigode", "Calçada", "Ônibus", "Filha", "Janela", "Cenoura", "Urso", "Limpo",
       "Galinha", "Urso", "Colher", "Ovo", "Leite", "Amarelo", "Comida", "Voar", "Gelo", "abajur",
       "Cenoura", "Prato", "Maçã", "Alface", "Garrafa", "Pato", "Carro", "Meia", "Lápis", "Ferro",
       "Velho", "Astronauta", "Borboleta", "Nuvem", "lua", "Aranha", "Cueca", "Casa", "Rua", "Kiwi",
       "Soldado", "Voar", "Coração", "Poltrona", "Bola", "Irmã", "Pulmão", "Bicicleta", "Verde", "Pepino",
       "Balão", "Closet", "Gato", "Parede", "Folha", "Olho", "Fone de Ouvido", "Camisa", "Macarrão", "Orelha",
       "Garrafa", "Macarrão", "Avó", "Cão", "Irmã", "Prédio", "Cabeça", "Urso", "Bigode", "Foguete",
       "Marte", "Estrela", "Tesoura", "Cabine", "Relógio", "Caminhão", "Chapéu", "Menina", "Branco", "Tomates",
       "Calças", "Torta", "Laranja", "Cabide", "Parafuso", "Barriga", "Vermelho", "Verde", "Colher", "Unicórnio",
       "Vampiro", "Cometa", "Celular", "Robô", "Computador", "Lanterna", "Pulmão", "Copo", "Fonte", "Unha",
       "Lente", "Lobo", "Flor", "Quadro", "Raio", "Barba", "Cereja", "Perna", "Saco", "Jardim", "Banheira",
       "Preto", "Estanho", "Tartaruga", "Água", "Avô", "Avião", "Programar", "Abóbora", "Coração", "Colher",
       "Chocolate", "Sanduíche", "Sol", "Pera", "Comida", "Estrela Cadente", "Irmão", "Novo", "Bota", "Batata Frita",
       "Saia", "Minion", "Raio", "Uva", "Futebol", "Banana", "Pimenta", "Frio", "Planeta", "Velho",
       "Pai", "Vegetais", "Mãe", "Vestido de Noiva", "Flor", "Caderno", "Anjo", "Advogado", "Médico",
       "Teto", "Vaca", "Talher", "Estudante", "Professor", "Bebida", "Refrigerante", "Jujuba", "Calcinha", "Lagarto",
       "Salto Alto", "Pintor", "Baleia", "Ursinho de Pelúcia", "Gelo", "Espada", "Dragão", "Dinossauro", "Guardanapo", "Rã",
       "Tablet", "Celular", "Computador", "Maquiagem", "Brigadeiro", "Anel", "Livro", "Mouse", "Brinquedo", "Fada",
       "Lobisomen", "Feitiçeiro", "Gato", "Cachorro", "Mesa", "Roupa", "Piano", "Violão", "Empreendedor", "Rei"],
      dreams: [],
      nightmare: [],
      cartaJogada: "Cachorro",
      timer: 120,
  }),

  computed: {
    progressoBarraTempo() {
      let porcentagem = (100*this.timer)/120
      return porcentagem
    }
  },

  methods: {
    sortearCarta() {
      const indexSorteado = Math.floor(Math.random() * this.deck.length) + 1
      const cartaSorteada = this.deck[indexSorteado]
      this.cartaJogada = cartaSorteada
    },

    dreamerAcertou(acertou){
      if (acertou == true) {
        this.dreams.push(this.cartaJogada)
      }else {
        this.nightmare.push(this.cartaJogada)
      }
    },

    limparArrays() {
      this.dreams = []
      this.nightmare = []
    },

    iniciarTimer() {
      this.mostrarBarraTempo=  true
      this.limparArrays()
      const contagemRegressivaInterval = setInterval(() => {
        this.timer -= 1
          console.log(this.timer);
        if (this.timer <= 0) {
          clearInterval(contagemRegressivaInterval)
          this.mostrarBarraTempo=false
          this.timer=10
        }
      }, 1000)
    }
  }
}
</script>
