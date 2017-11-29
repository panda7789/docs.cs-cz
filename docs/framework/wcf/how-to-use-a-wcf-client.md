---
title: "Postupy: Používání klienta Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: "38"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c4b0612cc18129f9f35ed3f475bca8941a20d3ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>Postupy: Používání klienta Windows Communication Foundation
Toto je poslední šesti úkoly vyžadované pro vytvoření základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace. Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.  
  
 Jednou [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy serveru bylo vytvořeno a nakonfigurováno, lze vytvořit instanci klienta a klientské aplikace můžete zkompilovat a použít ke komunikaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Toto téma popisuje postupy pro vytváření instancí a použití [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta. Tento postup provádí tři věci:  
  
1.  Vytvoří [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta.  
  
2.  Volání operace služby ze vygenerovaný proxy server.  
  
3.  Po dokončení volání operace se ukončí klienta.  
  
### <a name="to-use-a-windows-communication-foundation-client"></a>Chcete-li použít klienta Windows Communication Foundation  
  
1.  Otevřete soubor Program.cs nebo soubor Program.vb z projektu GettingStartedClient a existujícího kódu nahraďte následujícím kódem:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
                // Call the Add service operation.  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Subtract service operation.  
                value1 = 145.00D;  
                value2 = 76.54D;  
                result = client.Subtract(value1, value2);  
                Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Multiply service operation.  
                value1 = 9.00D;  
                value2 = 81.25D;  
                result = client.Multiply(value1, value2);  
                Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Divide service operation.  
                value1 = 22.00D;  
                value2 = 7.00D;  
                result = client.Divide(value1, value2);  
                Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     Všimněte si pomocí nebo importuje příkaz, který importuje GettingStartedClient.ServiceReference1. To importuje kód vygenerovaný přidat odkaz na službu v sadě Visual Studio. Kód vytvoří WCF proxy a potom volá všechny operace služby, které jsou vystavené službu kalkulačky, zavře proxy serveru a ukončí.  
  
 Teď jste dokončili kurz. Definované kontraktu služby, implementována kontrakt služby, generuje proxy server WCF, nakonfigurovat klientskou aplikaci WCF a pak použít proxy server k volání operací služby. K otestování aplikace nejprve spusťte GettingStartedHost spusťte službu a pak spusťte GettingStartedClient. Výstup z GettingStartedHost by měl vypadat takto:  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 Výstup z GettingStartedClient by měl vypadat takto:  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a>Viz také  
 [Sestavování klientů](../../../docs/framework/wcf/building-clients.md)  
 [Postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Postupy: vytvoření duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Postupy: přístup ke službám pomocí duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)
