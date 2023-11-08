# gerenciador_loja_mysql
prova prática da matéria de gerenciamento de banco de dados

create schema if not exists comercio default character set utf8; 
use comercio;

create table if not exists produto (
id_produto int unsigned not null auto_increment,
nome varchar(50) not null,
descricao varchar(200),
primary key (id_produto)
);

create table if not exists cliente (
id_cliente int unsigned not null auto_increment,
cpf varchar(100) not null,
nome varchar(50) not null,
endereco varchar(100) not null,
primary key (id_cliente)
);

create table if not exists loja (
id_loja int unsigned not null auto_increment,
nome varchar(50) not null,
cnpj varchar(20) not null,
endereco varchar(100) not null,
primary key (id_loja)
);

create table if not exists venda (
id_venda int unsigned not null auto_increment,
dia varchar(50) not null,
valor_total int unsigned not null,
venda_id_cliente int unsigned not null,
venda_id_loja int unsigned not null,
primary key (id_venda),
foreign key (venda_id_cliente) references cliente(id_cliente),
foreign key (venda_id_loja) references loja(id_loja)
);

create table if not exists produto_venda (
produto_venda_id_produto int unsigned not null,
produto_venda_id_venda int unsigned not null,
preco varchar(10) not null,
quantidade int unsigned not null,
foreign key (produto_venda_id_produto) references produto(id_produto),
foreign key (produto_venda_id_venda) references venda(id_venda)
);
 
insert into produto values (1, 'Lápis', 'Lápis com tabuada');
insert into produto values (2, 'Caneta', 'Caneta esferográfica');
insert into produto values (3, 'Borracha', 'Borracha branca');

insert into cliente values (1, '73465276212', 'Josep Camb', 'Rua dos Aflitos, 566');
insert into cliente values (2, '76345567832', 'Humber Send', 'Rua da Avaliação, 12');
insert into cliente values (3, '76753333345', 'Mark Markeu', 'Rua das Lágrimas, 11');

insert into loja values (1, 'Esperanca Ltda', '943890823901', 'Rua General');
insert into loja values (2, 'Estude Mais Ltda', '904590438541', 'Rua Marechal');
insert into loja values (3, 'Misericordia ME', '984089038543', 'Rua Capitao');

insert into venda values (1, 2019/06/23, '123.66', 1, 2);
insert into venda values (2, 2019/07/23, '34.55', 1, 3);
insert into venda values (3, 2019/08/01, '346.33', 3, 1);

insert into produto_venda values (1, 1, '45.33', 3);
insert into produto_venda values (1, 2, '34.55', 1);
insert into produto_venda values (3, 3, '30.66', 10);
