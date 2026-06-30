# Estacionamento
using System;
using System.Collections.Generic;

public class Estacionamento
{
    private decimal precoInicial;
    private decimal precoHora;
    private List<string> veiculos;

    public Estacionamento(decimal precoInicial, decimal precoHora)
    {
        this.precoInicial = precoInicial;
        this.precoHora = precoHora;
        this.veiculos = new List<string>();
    }

    public void AdicionarVeiculo()
    {
        Console.Write("Digite a placa do veículo: ");
        string placa = Console.ReadLine();

        veiculos.Add(placa);
        Console.WriteLine("Veículo adicionado com sucesso!");
    }

    public void RemoverVeiculo()
    {
        Console.Write("Digite a placa do veículo: ");
        string placa = Console.ReadLine();

        if (veiculos.Contains(placa))
        {
            Console.Write("Digite a quantidade de horas estacionado: ");
            int horas = int.Parse(Console.ReadLine());

            veiculos.Remove(placa);

            decimal valorTotal = precoInicial + (precoHora * horas);

            Console.WriteLine($"Veículo removido. Valor a pagar: R$ {valorTotal}");
        }
        else
        {
            Console.WriteLine("Veículo não encontrado!");
        }
    }

    public void ListarVeiculos()
    {
        if (veiculos.Count == 0)
        {
            Console.WriteLine("Nenhum veículo estacionado.");
            return;
        }

        Console.WriteLine("Veículos estacionados:");
        foreach (string v in veiculos)
        {
            Console.WriteLine("- " + v);
        }
    }
}

using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== SISTEMA DE ESTACIONAMENTO ===");

        Console.Write("Preço inicial: ");
        decimal precoInicial = decimal.Parse(Console.ReadLine());

        Console.Write("Preço por hora: ");
        decimal precoHora = decimal.Parse(Console.ReadLine());

        Estacionamento estacionamento = new Estacionamento(precoInicial, precoHora);

        string opcao = "";

        while (opcao != "4")
        {
            Console.WriteLine("\n=== MENU ===");
            Console.WriteLine("1 - Adicionar veículo");
            Console.WriteLine("2 - Remover veículo");
            Console.WriteLine("3 - Listar veículos");
            Console.WriteLine("4 - Sair");
            Console.Write("Escolha: ");

            opcao = Console.ReadLine();

            switch (opcao)
            {
                case "1":
                    estacionamento.AdicionarVeiculo();
                    break;

                case "2":
                    estacionamento.RemoverVeiculo();
                    break;

                case "3":
                    estacionamento.ListarVeiculos();
                    break;

                case "4":
                    Console.WriteLine("Encerrando sistema...");
                    break;

                default:
                    Console.WriteLine("Opção inválida!");
                    break;
            }
        }
    }
}
