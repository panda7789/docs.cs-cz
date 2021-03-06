---
title: Netypový požadavek-odpověď
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 46047d1671fadb18052991451910b9056015edd2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591095"
---
# <a name="untyped-requestreply"></a>Netypový požadavek/odpověď
Tento příklad ukazuje, jak definovat kontrakty operací, které používají třídu zprávy.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka je založena na [Začínáme](getting-started-sample.md). Kontrakt služby definuje jednu operaci, která jako argument přijímá typ zprávy, a vrátí zprávu. Operace shromáždí všechna požadovaná data, aby vypočítala součet z těla zprávy, a pak odešle součet jako text v návratové zprávě.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Ve službě operace načte pole celých čísel předaných ve vstupní zprávě a pak vypočítá součet. K odeslání zprávy odpovědi ukázka vytvoří novou zprávu s příslušnou verzí a akcí zprávy a přidá vypočítanou částku jako text. Následující ukázka kódu to demonstruje.  
  
```csharp
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 Klient používá kód generovaný [nástrojem ServiceModel Metadata Utility (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vytvoření proxy serveru pro vzdálenou službu. Chcete-li odeslat zprávu požadavku, klient musí mít verzi zprávy, která závisí na základním kanálu. Proto vytvoří nový <xref:System.ServiceModel.OperationContextScope> obor s vytvořeným kanálem proxy, který vytvoří <xref:System.ServiceModel.OperationContext> správnou verzi zprávy naplněnou ve své `OutgoingMessageHeaders.MessageVersion` Vlastnosti. Klient předá vstupní pole jako tělo zprávy požadavku a potom vyvolá `ComputeSum` na proxy serveru. Klient pak načte součet předaných vstupů přístupem k `GetBody<T>` metodě ve zprávě odpovědi. Následující ukázka kódu to demonstruje.  
  
```csharp
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",
                                                       response);  
}  
```  
  
 Tato ukázka je ukázka hostovaná na webu, takže je nutné spustit pouze klientský spustitelný soubor. Následuje ukázkový výstup na klientovi.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Tato ukázka je ukázka hostovaná v rámci webu, proto zkontrolujte odkaz uvedený v kroku 3, kde zjistíte, jak sestavit a spustit ukázku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
