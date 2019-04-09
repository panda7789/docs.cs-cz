---
title: Netypový požadavek odpověď
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: ae3c89f9eec9b1684f8c87af200ba87ca8dec093
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101188"
---
# <a name="untyped-requestreply"></a>Netypový požadavek/odpověď
Tento příklad ukazuje, jak definovat operace kontrakty, používající třídu zpráv.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt služby definuje jednu operaci, která přijímá typ zprávy jako argument a vrátí zprávu. Operace shromažďuje všechna požadovaná data pro výpočet součtu z textu zprávy a poté odešle součet jako text v návratové zprávě.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Ve službě tato operace načte pole celých čísel předaný vstupní zprávy a pak vypočítá součet. Odeslat zprávu odpovědi, ukázka vytvoří novou zprávu s verzí odpovídající zprávu a akce a přidá vypočítaný součet jako jeho obsah. Následující ukázkový kód ukazuje to.  
  
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
  
 Klient používá kód, který je generován [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořit proxy server ve vzdálené službě. Chcete-li odeslat zprávu požadavku, klient musí mít verzi zprávy, která závisí na základním kanálu. Díky tomu se vytvoří nový <xref:System.ServiceModel.OperationContextScope> vymezený kanál proxy vytvoří, tím se vytvoří <xref:System.ServiceModel.OperationContext> s správná verze v jeho `OutgoingMessageHeaders.MessageVersion` vlastnost. Předá vstupní pole jako text zprávy s požadavkem klienta a poté vyvolá `ComputeSum` na proxy serveru. Klient pak načte součet vstupy jí předán díky přístupu `GetBody<T>` metoda u zprávy s odpovědí. Následující ukázkový kód ukazuje to.  
  
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
  
 Tato ukázka je ukázkový Web hostovaný a musí být spuštěn pouze spustitelný soubor pro klienta. Následuje ukázkový výstup na straně klienta.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Tato ukázka je Web hostovaný ukázka a podívejte se proto poskytnutý odkaz v kroku 3 a zjistit, jak sestavit a spustit ukázku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
