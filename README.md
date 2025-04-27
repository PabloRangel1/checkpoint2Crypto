
#  Documentação - Projeto CryptoMonitor

##  Descrição Geral

**CryptoMonitor** é um aplicativo Android que consulta em tempo real o valor do Bitcoin (BTC) na plataforma **Mercado Bitcoin**, exibindo o último preço atualizado e a data da cotação.

A aplicação utiliza:

-   Kotlin
    
-   Retrofit2 (com Gson Converter)
    
-   Coroutines
    
-   Android View System (TextView, Button, Toolbar)
    

----------

##  Estrutura de Pacotes

```
carreiras.com.github.cryptomonitor
├── model
│   ├── TickerResponse.kt
│   └── Ticker.kt
├── service
│   ├── MercadoBitcoinService.kt
│   └── MercadoBitcoinServiceFactory.kt
└── MainActivity.kt

```

----------

##  Funcionalidades

-   Consulta a cotação atual do Bitcoin (BTC) usando API pública do Mercado Bitcoin.
    
-   Exibe o valor do Bitcoin formatado em moeda brasileira (R$).
    
-   Exibe a data e hora da última atualização.
    
-   Botão "Refresh" para atualizar manualmente as informações.
    
-   Tratamento de erros de resposta da API e falhas de conexão.
    

----------

## 🛠️ Tecnologias Utilizadas

-   **Kotlin** - Linguagem principal
    
-   **Retrofit2** - Cliente HTTP para Android
    
-   **GsonConverterFactory** - Conversão de JSON em objetos Kotlin
    
-   **Coroutines** - Gerenciamento de chamadas assíncronas
    
-   **AndroidX AppCompat** - Suporte visual para Toolbar e componentes modernos
    

----------

##  Detalhamento das Classes

### model

-   **TickerResponse**
    
    -   Representa a resposta completa da API contendo um objeto `Ticker`.
        
-   **Ticker**
    
    -   Contém informações específicas da cotação:
        
        -   `high` (valor máximo)
            
        -   `low` (valor mínimo)
            
        -   `vol` (volume negociado)
            
        -   `last` (último preço)
            
        -   `buy` (preço de compra)
            
        -   `sell` (preço de venda)
            
        -   `date` (timestamp da cotação)
            

### service

-   **MercadoBitcoinService**
    
    -   Interface do Retrofit que define a chamada HTTP `GET` para a rota `/api/BTC/ticker/`.
        
-   **MercadoBitcoinServiceFactory**
    
    -   Classe que cria uma instância configurada do `MercadoBitcoinService` usando Retrofit e Gson.
        

### MainActivity

-   Tela principal do app.
    
-   Configura a `Toolbar` personalizada.
    
-   Gerencia o botão de atualização.
    
-   Realiza a chamada da API utilizando coroutines.
    
-   Atualiza os `TextViews` de valor e data.
    
-   Realiza tratamento de erros HTTP e exceções.
    

----------

## 🌐 API Consumida

-   **Base URL:** `https://www.mercadobitcoin.net/`
    
-   **Endpoint:** `api/BTC/ticker/`
    
-   **Método:** `GET`
    
-   **Formato de Resposta:** JSON
    

Exemplo de resposta:

```json
{
  "ticker": {
    "high": "152000.00",
    "low": "148000.00",
    "vol": "120.5",
    "last": "150000.00",
    "buy": "149500.00",
    "sell": "150500.00",
    "date": 1618327340
  }
}

```

----------

## Fluxo de Funcionamento

1.  Usuário abre o aplicativo.
    
2.  O botão "Refresh" é exibido para consulta manual.
    
3.  Ao clicar no botão, uma chamada assíncrona é realizada à API do Mercado Bitcoin.
    
4.  Se bem-sucedida:
    
    -   O valor do Bitcoin é exibido em formato monetário brasileiro.
        
    -   A data é convertida do formato timestamp UNIX para `dd/MM/yyyy HH:mm:ss`.
        
5.  Em caso de erro:
    
    -   Um Toast é exibido mostrando a mensagem apropriada de erro.
        

----------

## 🛡️ Tratamento de Erros

-   Respostas HTTP:
    
    -   `400`: "Bad Request"
        
    -   `401`: "Unauthorized"
        
    -   `403`: "Forbidden"
        
    -   `404`: "Not Found"
        
    -   Outro: "Unknown error"
        
-   Exceções de conexão ou outras falhas são capturadas e informadas ao usuário via Toast.
    

----------
## Evidências da Execução  
  
Abaixo, uma imagem mostrando a execução do projeto:  
  

![evidencia_execucao](https://github.com/user-attachments/assets/0c417b61-4a3b-4d95-a92e-0651b7c6c7d5)


