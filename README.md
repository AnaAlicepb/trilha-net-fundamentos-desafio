# DIO - Trilha .NET - Fundamentos
www.dio.me

## Desafio de projeto
Para este desafio, você precisará usar seus conhecimentos adquiridos no módulo de fundamentos, da trilha .NET da DIO.

## Contexto
Você foi contratado para construir um sistema para um estacionamento, que será usado para gerenciar os veículos estacionados e realizar suas operações, como por exemplo adicionar um veículo, remover um veículo (e exibir o valor cobrado durante o período) e listar os veículos.

## Proposta
Você precisará construir uma classe chamada "Estacionamento", conforme o diagrama abaixo:
![Diagrama de classe estacionamento](diagrama_classe_estacionamento.png)

A classe contém três variáveis, sendo:

**precoInicial**: Tipo decimal. É o preço cobrado para deixar seu veículo estacionado.

**precoPorHora**: Tipo decimal. É o preço por hora que o veículo permanecer estacionado.

**veiculos**: É uma lista de string, representando uma coleção de veículos estacionados. Contém apenas a placa do veículo.

A classe contém três métodos, sendo:

**AdicionarVeiculo**: Método responsável por receber uma placa digitada pelo usuário e guardar na variável **veiculos**.

**RemoverVeiculo**: Método responsável por verificar se um determinado veículo está estacionado, e caso positivo, irá pedir a quantidade de horas que ele permaneceu no estacionamento. Após isso, realiza o seguinte cálculo: **precoInicial** * **precoPorHora**, exibindo para o usuário.

**ListarVeiculos**: Lista todos os veículos presentes atualmente no estacionamento. Caso não haja nenhum, exibir a mensagem "Não há veículos estacionados".

Por último, deverá ser feito um menu interativo com as seguintes ações implementadas:
1. Cadastrar veículo
2. Remover veículo
3. Listar veículos
4. Encerrar


## Solução
O código está pela metade, e você deverá dar continuidade obedecendo as regras descritas acima, para que no final, tenhamos um programa funcional. Procure pela palavra comentada "TODO" no código, em seguida, implemente conforme as regras acima.

---

# Evolução e Melhorias Implementadas no Projeto

Além de completar as funcionalidades básicas exigidas, o sistema foi aprimorado para garantir maior **robustez**, **segurança** e **usabilidade** para o operador.

## 1. Justificativa das Melhorias na Lógica de Negócios

As alterações no código tornaram o sistema mais seguro contra falhas e mais alinhado com a lógica operacional de um estacionamento real.

### 1.1. Melhoria na Segurança e Robustez

* **Validação Robusta de Entradas (Preços e Horas):**
    * **Implementação:** Nos pontos de leitura de valores numéricos (preços no `Program.cs` e horas no `RemoverVeiculo`), o método `Convert.ToDecimal()` foi substituído por **`TryParse()`** dentro de *loops* de validação.
    * **Justificativa:** Esta técnica previne que o programa **trave** (`FormatException`) caso o operador digite texto ou caracteres inválidos. O sistema agora força a entrada de valores numéricos válidos e não-negativos, aumentando a estabilidade.

* **Padronização de Placas:**
    * **Implementação:** O método **`.ToUpper()`** foi aplicado à leitura de todas as placas.
    * **Justificativa:** Garante que todas as placas sejam armazenadas e buscadas em letras maiúsculas, **eliminando erros de busca** devido à sensibilidade de caixa (*case sensitivity*).

### 1.2. Melhoria na Usabilidade (UX) e Transação

* **Cálculo de Preço Corrigido:**
    * **Fórmula Usada:** A lógica de cálculo foi corrigida para **`precoInicial + (precoPorHora * horas)`**.
    * **Justificativa:** Esta fórmula reflete a lógica real de um estacionamento (taxa de entrada fixa + valor acumulado por tempo).

* **Fluxo de Confirmação de Saída:**
    * **Implementação:** O método `RemoverVeiculo` agora **calcula o valor, exibe-o no console e solicita uma confirmação (S/N)** ao operador antes de finalizar a remoção.
    * **Justificativa:** Adiciona uma **camada de controle** crucial. Permite que o operador veja o valor total a ser pago e, em caso de erro na contagem de horas ou contestação do cliente, digite **'N'** para **cancelar a transação**, mantendo o veículo registrado.

## 2. Estrutura e Conformidade

O sistema final está totalmente funcional, seguindo a estrutura de POO (Programação Orientada a Objetos) exigida e o menu interativo de quatro opções (Cadastrar, Remover, Listar, Encerrar) implementado no `Program.cs`.