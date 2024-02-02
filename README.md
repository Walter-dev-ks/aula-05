# Sistema de Gerenciamento de Produtos

Este programa Java demonstra um Sistema Básico de Gerenciamento de Produtos. Ele inclui uma classe `Main` para interação do usuário e uma classe `Product` para representar produtos.

## Uso

1. Certifique-se de ter o Java instalado em sua máquina.
2. Compile e execute a classe `Main`.

```bash
javac Main.java
java Main
```

3. Siga as instruções na tela para inserir dados do produto, adicionar produtos ao estoque e remover produtos do estoque.

## Visão Geral do Código

### Classe Main (`Main.java`)

```java
import entities.Product;

import java.util.Locale;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {


        Locale.setDefault(Locale.US);
        Scanner sc = new Scanner(System.in);

        Product product;
        product = new Product();
        System.out.println("Enter product data: ");
        System.out.print("Name: ");
        product.name = sc.nextLine();
        System.out.print("Price: ");
        product.price = sc.nextDouble();
        System.out.print("Quantity in Stock: ");
        product.quantity = sc.nextInt();

        System.out.println();
        System.out.println("Product data: " + product);

        System.out.println();
        System.out.print("Enter the number products to be added in stock: ");
        int quantity = sc.nextInt();
        product.addProducts(quantity);

        System.out.println();
        System.out.println("Updated data: " + product);

        System.out.println();
        System.out.print("Enter the number products to be removed in stock: ");
        quantity = sc.nextInt();
        product.removeProducts(quantity);

        System.out.println();
        System.out.println("Updated data: " + product);

        sc.close();

    }
}
```

### Classe Product (`Product.java`)

```java
package entities;

public class Product {
    public String name;
    public double price;
    public int quantity;

    public double totalValueInStock() {
        // Calcula o valor total dos produtos em estoque
        return price * quantity;
    }

    public void addProducts(int quantity) {
        // Adiciona uma quantidade específica ao estoque
        this.quantity += quantity;
    }

    public void removeProducts(int quantity) {
        // Remove uma quantidade específica do estoque
        this.quantity -= quantity;
    }

    public String toString() {
        // Retorna uma string formatada representando o produto
        return name + ", R$ " + String.format("%.2f", this.price) +
                ", " + this.quantity + " unidades, Total: R$ " +
                String.format("%.2f", totalValueInStock());
    }
}
```

## Saída de Exemplo

```plaintext
Digite os dados do produto:
Nome: Notebook
Preço: 1200,50
Quantidade em Estoque: 5

Dados do produto: Notebook, R$ 1200,50, 5 unidades, Total: R$ 6025,00

Digite o número de produtos a serem adicionados ao estoque: 3

Dados atualizados: Notebook, R$ 1200,50, 8 unidades, Total: R$ 9618,00

Digite o número de produtos a serem removidos do estoque: 2

Dados atualizados: Notebook, R$ 1200,50, 6 unidades, Total: R$ 7212,00
```
