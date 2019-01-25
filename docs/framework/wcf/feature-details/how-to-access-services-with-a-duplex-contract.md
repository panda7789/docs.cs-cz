---
title: 'Postupy: Přístup ke službám pomocí duplexního kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 2f83b8ac71bfc53791f7de42d127badbda0d3881
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610306"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Postupy: Přístup ke službám pomocí duplexního kontraktu

Jednu funkci Windows Communication Foundation (WCF) je schopnost vytvářet služby, která používá vzor duplexní zasílání zpráv. Tento model umožňuje služba ke komunikaci s klientem prostřednictvím zpětné volání. Toto téma popisuje kroky k vytvoření klienta WCF v třídě klienta, který implementuje rozhraní zpětného volání.

Duální vazby poskytuje IP adresu klienta do služby. Klient musí použít zabezpečení zajistit, že se připojí jenom ke službám ji vztahy důvěryhodnosti.

Kurz týkající se vytvoření klienta a basic služby WCF, najdete v tématu [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Pro přístup k duplexní služby

1. Vytvoření služby, která obsahuje dvě rozhraní. První rozhraní je pro službu, druhý zpětného volání. Další informace o vytvoření duplexní služby najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).

2. Spuštění služby.

3. Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat kontrakty (rozhraní) pro klienta. Informace o tom, jak to provést, najdete v tématu [jak: Vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).

4. Implementujte rozhraní zpětného volání ve třídě klienta, jak je znázorněno v následujícím příkladu.

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.Writeline("Equation({0})", equation)
        End Sub
    End Class
    ```

5. Vytvořit instanci <xref:System.ServiceModel.InstanceContext> třídy. Konstruktor vyžaduje instanci třídy klienta.

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. Vytvořte instanci klienta WCF pomocí konstruktoru, který se vyžaduje <xref:System.ServiceModel.InstanceContext> objektu. Druhý parametr konstruktoru je název koncového bodu v konfiguračním souboru nalezeno.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. Volání metody WCF klienta podle potřeby.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit třídu klienta, který přistupuje k duplexního kontraktu.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Viz také:

- [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Postupy: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Postupy: Používání ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
