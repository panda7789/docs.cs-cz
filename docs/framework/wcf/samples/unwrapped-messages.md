---
title: Nerozbalené zprávy
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 4d6525393bb65dd6361b8d195f3a71991102daa1
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716738"
---
# <a name="unwrapped-messages"></a>Nerozbalené zprávy
Tento příklad ukazuje nezabalené zprávy. Ve výchozím nastavení je tělo zprávy formátováno tak, že parametry operace služby jsou zabaleny. Následující ukázka ukazuje zprávu žádosti o `Add` do služby `ICalculator` v zabaleném režimu.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 Prvek `<Add>` v těle zprávy balí parametry `n1` a `n2`. Naproti tomu následující příklad ukazuje ekvivalentní zprávu v nezabaleném režimu.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 Rozbalení zprávy nezalomí `n1` a `n2` parametrů v obsahujícím elementu, jsou přímými podřízenými elementy SOAP těla elementu.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 V této ukázce je vytvořena nezabalená zpráva pomocí <xref:System.ServiceModel.MessageContractAttribute> typu parametru operace služby a návratového typu hodnoty, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 Aby bylo možné zobrazit zprávy odesílané a přijímané, Tato ukázka používá trasování. Kromě toho je <xref:System.ServiceModel.WSHttpBinding> nakonfigurovaný bez zabezpečení, aby se snížil počet zpráv, které protokoluje.  
  
 Výsledný protokol trasování (c:\logs\Message.log) lze zobrazit pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Chcete-li zobrazit obsah zprávy, vyberte **zprávy** v levém a pravém podokně nástroje Prohlížeč trasování služby. Protokoly trasování v této ukázce jsou nakonfigurovány tak, aby se vygenerovaly do složky C:\Logs. Před spuštěním ukázky vytvořte tuto složku a poskytněte uživateli síťová služba oprávnění k zápisu do tohoto adresáře.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Vytvořte adresář C:\Logs. pro protokolování zpráv. Udělte síťové službě uživateli oprávnění zapisovat pro tento adresář.  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
