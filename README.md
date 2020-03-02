# CRUD Concessionária | GoLang

```golang

package main

import (
    "fmt"
    "os"
)

func Remover(s []string, index int) []string {
  return append(s[:index], s[index+1:]...)
}

func main() {

  var VerificaMenu1 string
  var ListaTotal [] string

  for ok:= true; ok; ok = true {

    fmt.Println("\n[X]Olá, bem vindo ao Crud de Concessionaria!")
    fmt.Println("[1]Cadastrar.")
    fmt.Println("[2]Apresentar.")
    fmt.Println("[3]Alterar.")
    fmt.Println("[4]Excluir.")
    fmt.Println("[5]Sair.")
    fmt.Println("[X]Escolha uma opção!")
    fmt.Scanln(&VerificaMenu1)

    if VerificaMenu1 == "1" {

      var Codigo, Nome, Ano, Combustivel, Configuração, Lugares, Tração, CadastroCompleto string

      fmt.Println("\n[X]Opção de cadastro!")

      fmt.Println("\n[X]Digite o codigo do carro:")
      fmt.Scanln(&Codigo)

      fmt.Println("\n[X]Digite o nome do carro:")
      fmt.Scanln(&Nome)
      
      fmt.Println("\n[X]Digite o ano do carro:")
      fmt.Scanln(&Ano)

      fmt.Println("\n[X]Digite o tipo do combustivel do carro:")
      fmt.Scanln(&Combustivel)

      fmt.Println("\n[X]Digite a configuração do carro:")
      fmt.Scanln(&Configuração)

      fmt.Println("\n[X]Digite a quantidade de lugares do carro:")
      fmt.Scanln(&Lugares)

      fmt.Println("\n[X]Digite o tipo de tração do carro:")
      fmt.Scanln(&Tração)

      CadastroCompleto = "Codigo: " + Codigo + " | " + "Nome: " + Nome + " | " + "Ano: " + Ano + " | " + "Combustivel: " + Combustivel + " | " + "Configuração: " + Configuração + " | " + "Lugares: " + Lugares + " | " + "Tração: " + Tração

      ListaTotal = append(ListaTotal, CadastroCompleto)

    } else if VerificaMenu1 == "2" {
      fmt.Println("\n[X]Opção de Apresentação!")

      if len(ListaTotal) == 0 {
        fmt.Println("[X]Nenhum usuário registrado!")
      } else{
        for Contador, PegaDados := range ListaTotal {
          fmt.Println("[ " + "Carro ",Contador, ": ", PegaDados + " ]")
        }
      }
    } else if VerificaMenu1 == "3" {
      var Codigo, Nome, Ano, Combustivel, Configuração, Lugares, Tração, CadastroCompleto string
      fmt.Println("\n[X]Opção de Alteração!")

      var CarroAlteração int

      if len(ListaTotal) == 0 {
        fmt.Println("[X]Nenhum usuário registrado!")
      } else {

        fmt.Println("\n[X]Digite o carro a ser alterado: ")
        fmt.Scanln(&CarroAlteração)

        var Verificador int

        for Contador := range ListaTotal{

          if Contador == CarroAlteração {
            Verificador = Verificador + 1
          }
        }

        if Verificador > 0 {

          ListaTotal[CarroAlteração] = ""
          
          fmt.Println("\n[X]Digite o codigo do carro:")
          fmt.Scanln(&Codigo)

          fmt.Println("\n[X]Digite o nome do carro:")
          fmt.Scanln(&Nome)
      
          fmt.Println("\n[X]Digite o ano do carro:")
          fmt.Scanln(&Ano)

          fmt.Println("\n[X]Digite o tipo do combustivel do carro:")
          fmt.Scanln(&Combustivel)

          fmt.Println("\n[X]Digite a configuração do carro:")
          fmt.Scanln(&Configuração)

          fmt.Println("\n[X]Digite a quantidade de lugares do carro:")
          fmt.Scanln(&Lugares)

          fmt.Println("\n[X]Digite o tipo de tração do carro:")
          fmt.Scanln(&Tração)

          CadastroCompleto = "Codigo: " + Codigo + " | " + "Nome: " + Nome + " | " + "Ano: " + Ano + " | " + "Combustivel: " + Combustivel + " | " + "Configuração: " + Configuração + " | " + "Lugares: " + Lugares + " | " + "Tração: " + Tração 

          ListaTotal[CarroAlteração] = CadastroCompleto

        } else {
          fmt.Println("\n[X]Nenhum carro encontrado nesse indice!")
        }
      }
    } else if VerificaMenu1 == "4" {

      fmt.Println("\n[X]Opção de Exclusão!")

      var CarroExclusão int

      if len(ListaTotal) == 0{
        fmt.Println("[X]Nenhum usuário registrado!")
      } else {
        fmt.Println("\n[X]Digite o carro a ser excluido: ")
        fmt.Scanln(&CarroExclusão)
      
        var Verificador int

        for Contador := range ListaTotal {

          if CarroExclusão == Contador {
            Verificador = Verificador + 1
          }
        }

        if Verificador > 0 {
          ListaTotal = Remover(ListaTotal, CarroExclusão)
          fmt.Println("\n[X]Carro Excluido!")
        } else{
          fmt.Println("\n[X]Nenhum carro encontrado nesse indice!")
        }
      }

    } else if VerificaMenu1 == "5" {
      fmt.Println("\n[X]Opção de saida. Obrigado!")
      os.Exit(0)
    } else {
      fmt.Println("\n[X]Digite uma opção valida!")
    }
  }
}

```
