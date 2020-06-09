---
title: 'Postupy: přístup ke službám pomocí duplexního kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597212"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Postupy: přístup ke službám pomocí duplexního kontraktu

Jednou z funkcí služby Windows Communication Foundation (WCF) je schopnost vytvořit službu, která používá duplexový vzor pro přenos zpráv. Tento model umožňuje službě komunikovat s klientem prostřednictvím zpětného volání. Toto téma ukazuje postup vytvoření klienta WCF v klientské třídě, která implementuje rozhraní zpětného volání.

Duální vazba zpřístupňuje IP adresu klienta ke službě. Klient by měl zabezpečení používat k zajištění toho, aby se připojil pouze ke službám, kterým důvěřuje.

Kurz týkající se vytvoření základní služby a klienta WCF najdete v tématu [Začínáme kurzu](../getting-started-tutorial.md).

## <a name="to-access-a-duplex-service"></a>Přístup k duplexní službě

1. Vytvořte službu, která obsahuje dvě rozhraní. První rozhraní je pro službu, druhým je pro zpětné volání. Další informace o vytváření duplexních služeb najdete v tématu [Postupy: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md).

2. Spusťte službu.

3. Pro generování kontraktů (rozhraní) pro klienta použijte nástroj pro dodané [metadata (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) . Informace o tom, jak to provést, najdete v tématu [Postup: Vytvoření klienta](../how-to-create-a-wcf-client.md).

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
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. Vytvořit instanci <xref:System.ServiceModel.InstanceContext> třídy. Konstruktor vyžaduje instanci klientské třídy.

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. Vytvořte instanci klienta WCF pomocí konstruktoru, který vyžaduje <xref:System.ServiceModel.InstanceContext> objekt. Druhým parametrem konstruktoru je název koncového bodu, který se nachází v konfiguračním souboru.

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. Podle potřeby zavolejte metody klienta služby WCF.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit třídu klienta, která přistupuje k oboustrannému kontraktu.

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>Viz také

- [Kurz Začínáme](../getting-started-tutorial.md)
- [Postupy: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md)
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Vytvoření klienta](../how-to-create-a-wcf-client.md)
- [Postupy: Použití objektu pro vytváření kanálů](how-to-use-the-channelfactory.md)
