---
title: Netypováodpověď na vyžádání
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: a526837b9bccf7a6287972e482a189a53ecadaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183292"
---
# <a name="untyped-requestreply"></a>Netypový požadavek/odpověď
Tato ukázka ukazuje, jak definovat operace smlouvy, které používají Message třídy.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Servisní smlouva definuje jednu operaci, která přijímá typ zprávy jako argument a vrací zprávu. Operace shromažďuje všechna požadovaná data pro výpočet součtu z těla zprávy a potom odešle součet jako text v návratové zprávě.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Ve službě operace načte pole celá čísla předaná ve vstupní zprávě a pak vypočítá součet. Chcete-li odeslat zprávu odpovědi, ukázka vytvoří novou zprávu s příslušnou verzí zprávy a akce a přidá vypočítaný součet jako jeho tělo. Následující ukázkový kód to ukazuje.  
  
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
  
 Klient používá kód, který je generován [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření proxy vzdálené služby. Chcete-li odeslat zprávu požadavku, klient musí mít verzi zprávy, která závisí na podkladovém kanálu. Tím se vytvoří <xref:System.ServiceModel.OperationContextScope> nový rozsah proxy kanálu, který vytvořil, který vytvoří <xref:System.ServiceModel.OperationContext> s správnou `OutgoingMessageHeaders.MessageVersion` verzi zprávy naplněný v jeho vlastnosti. Klient předá vstupní pole jako tělo zprávy požadavku a `ComputeSum` potom vyvolá na proxy serveru. Klient pak načte součet vstupů, které předal `GetBody<T>` přístupem k metodě na odpovědi. Následující ukázkový kód to ukazuje.  
  
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
  
 Tato ukázka je web-hostované ukázky a proto musí být spuštěn pouze spustitelný soubor klienta. Následuje ukázkový výstup na straně klienta.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Tato ukázka je web-hostované ukázka, a tak zkontrolujte odkaz k dispozici v kroku 3, jak sestavit a spustit ukázku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
