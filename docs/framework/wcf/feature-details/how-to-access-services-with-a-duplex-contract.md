---
title: "Postupy: Přístup ke službám pomocí duplexního kontraktu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ec8b7f37dc7f04a7ddb2c6373b50e98fe41cf98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Postupy: Přístup ke službám pomocí duplexního kontraktu
Jedna z funkcí systému [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je schopnost vytvářet služby, která používá vzor duplexní zasílání zpráv. Tento vzor umožňuje službě ke komunikaci s klientem prostřednictvím zpětné volání. Toto téma ukazuje postup vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta v třídě klienta, který implementuje rozhraní zpětného volání.  
  
 Duální vazbu zpřístupní IP adresu klienta ke službě. Klient musí použít zabezpečení zajistit, že připojení jenom k službám ho vztahy důvěryhodnosti.  
  
 Kurz týkající se vytváření základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a klienta, najdete v části [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md).  
  
### <a name="to-access-a-duplex-service"></a>Pro přístup k duplexní služby  
  
1.  Vytvoření služby, který obsahuje dvě rozhraní. První rozhraní je pro službu, druhý pro zpětné volání. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Vytvoření duplexní služby, najdete v části [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
2.  Spusťte službu.  
  
3.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generovat kontrakty (rozhraní) pro klienta. Informace o tom, jak to udělat najdete v tématu [postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
4.  Implementujte rozhraní zpětného volání ve třídě klienta, jak je znázorněno v následujícím příkladu.  
  
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
  
5.  Vytvořit instanci <xref:System.ServiceModel.InstanceContext> třídy. Konstruktor vyžaduje instanci třídy klienta.  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  Vytvoření instance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pomocí konstruktoru, který vyžaduje <xref:System.ServiceModel.InstanceContext> objektu. Druhý parametr konstruktoru je název koncového bodu v konfiguračním souboru nalézt.  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  Volání metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta podle potřeby.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit třídu klienta, který přistupuje k duplexního kontraktu.  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
  
## <a name="see-also"></a>Viz také  
 [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Postupy: vytvoření klienta](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Postupy: použití třídy ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
