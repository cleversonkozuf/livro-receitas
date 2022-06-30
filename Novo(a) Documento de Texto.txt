    self.tabela_garantia.column("#3", width=80, minwidth=50, stretch=NO)
        self.tabela_garantia.column("#4", width=100, minwidth=50, stretch=NO)
        self.tabela_garantia.column("#5", width=80, minwidth=50, stretch=NO)
        self.tabela_garantia.column("#6", width=100, minwidth=50, stretch=NO)
        self.tabela_garantia.column("#7", width=100, minwidth=50, stretch=NO)
        self.tabela_garantia.place(relx=0.01, rely=0.10, relwidth=0.98, relheight=0.98)
        # barra de rolagem
        self.scrool = Scrollbar(self.tabela_garantia, orient="vertical")
        self.tabela_garantia.configure(xscrollcommand=self.scrool.set)
        self.scrool.place(relx=0.96, rely=0.05, relwidth=0.02, relheight=0.89)
        #select da tabela
        self.tabela_garantia.delete(*self.tabela_garantia.get_children())
        self.conecta_BD()
        #lista = self.cursor.execute(""" SELECT id_cliente, nome, telefone, convert(char,data_registro,3)  FROM clientes
        #ORDER BY nome ASC; """)
        lista = self.cursor.execute(""" SELECT NOME,telefone,Marca,modelo,id_smart,convert(char,data_sai,3),descricao FROM clientes 
        INNER JOIN smartphone ON id_cliente = smartphone.cod_cliente
        where data_sai >= dateadd(MONTH, -3, getdate())