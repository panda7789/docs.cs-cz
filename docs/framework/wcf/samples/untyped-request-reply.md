---
title: Netypový požadavek odpověď
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: ef1e20bbeaf5f7a0d9eae4b921628482714c6163
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505339"
---
# <a name="untyped-requestreply"></a>Netypový požadavek/odpověď
Tento příklad znázorňuje jak definovat operace smlouvy, které použít třídu zpráv.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt služby definuje jednu operaci, která přebírá typ zprávy jako argument a vrátí zprávu. Operaci shromažďuje všechna požadovaná data pro výpočetní součet z textu zprávy a poté odešle součet jako text v návratové zprávy.  
  
```  
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Operaci na službu, načte poli celých čísel předaná vstupní zprávu a pak vypočítá součet. Odeslat zprávu odpovědi, ukázka vytvoří novou zprávu s verzí odpovídající zprávu a akci a přidá vypočítaný součet jako jeho text. Následující vzorový kód ukazuje to.  
  
```  
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
  
 Klient použije kód, který je generován [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořit proxy službě Vzdálené. Pokud chcete odeslat zprávu požadavku, klient musí mít verzi zprávy, které závisí na základní kanálu. Proto vytvoří novou <xref:System.ServiceModel.OperationContextScope> obor do kanálu proxy ji vytvořit, který vytvoří <xref:System.ServiceModel.OperationContext> verzí správné zpráv vložené do jeho `OutgoingMessageHeaders.MessageVersion` vlastnost. Klient předá vstupní pole jako text zprávy požadavku a potom se vyvolá `ComputeSum` na proxy serveru. Klient pak načte součet vstupních hodnot, je předaná přístup k `GetBody<T>` metodu na zpráva s odpovědí. Následující vzorový kód ukazuje to.  
  
```  
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
  
 Tato ukázka je ukázka webové hostované a je nutné spustit, protože pouze spustitelný soubor pro klienta. Následuje příklad výstupu na straně klienta.  
  
```  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Tato ukázka je Web hostovaný ukázka a Ano zkontrolovat odkaz uvedené v kroku 3 a zjistit, jak sestavit a spustit ukázku.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Viz také
