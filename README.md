# ExercicioAcademicoFila
Exercício Acadêmico com o objetivo de simular uma fila de restaurante virtual. Onde foi usada uma classe de fila construída por mim mesmo; 

 
            int opçao = 1, cliente = 1, F2 = 1, F3 = 1, F4 = 1; //INICIO MAIN
            bool exec = true;
            Fila pedido = new Fila(100);
            Fila pagamento = new Fila(100);
            Fila encomenda = new Fila(100);
            while (exec)
            {
                Console.WriteLine("------------- Restaurante Dona Tita -------------");
                Console.WriteLine("1 - Inserção de cliente na fila de pedidos");
                Console.WriteLine("2 - Remoção de cliente da fila de pedidos");
                Console.WriteLine("3 - Remoção de cliente da fila de pagamentos");
                Console.WriteLine("4 - Remoção de cliente da fila de encomendas");
                Console.WriteLine("5 - Sair");

                Console.Write("\nDe acordo com o menu acima, escolha uma opção: ");
                opçao = Convert.ToInt32(Console.ReadLine());

                if (opçao == 1)
                {
                    pedido.Enfileirar(cliente);
                    Console.WriteLine("Cliente " + cliente + " ingressou na fila de pedidos.");
                    cliente++;
                    Console.ReadLine();
                    Console.Clear();
                }
                else if (opçao == 2)
                {
                    pedido.Desenfileirar();
                    pagamento.Enfileirar(F2);
                    Console.WriteLine("Cliente " + F2 + " saiu da fila de pedidos, e ingressou na fila de pagamento.");
                    F2++;
                    Console.ReadLine();
                    Console.Clear();
                }
                else if (opçao == 3)
                {
                    pagamento.Desenfileirar();
                    encomenda.Enfileirar(F3);
                    Console.WriteLine("Cliente " + F3 + " saiu da fila de pagamento, e ingressou na fila de encomenda.");
                    F3++;
                    Console.ReadLine();
                    Console.Clear();
                }
                else if (opçao == 4)
                {
                    encomenda.Desenfileirar();
                    Console.WriteLine("Cliente " + F4 + " retirou seu pedido, e saiu da fila de encomenda.");
                    F4++;
                    Console.ReadLine();
                    Console.Clear();
                }
                else
                {
                    Console.WriteLine("Até mais ...");
                    Console.ReadLine();
                    exec = false;
                }
            } //FIM MAIN
            
            private int[] vet; //INICIO CLASSE FILA
        private int inicio;
        private int fim;

        public Fila(int tam)
        {
            vet = new int[tam];
            inicio = fim = 0;
        }

        public void Enfileirar(int i)
        {
            vet[fim] = i;
            fim = (fim + 1) % vet.Length;
        }

        public int Desenfileirar()
        {
            int item = vet[inicio];
            inicio = (inicio + 1) % vet.Length;
            return item;
        }

        public bool Vazia()
        {
            return inicio == fim;
        }

        public bool Cheia()
        {
            return ((fim + 1) % vet.Length) == inicio;
        } //FIM CLASSE FILA
