---
title: Nerozbalené zprávy
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: ea90a6355f63d5fffd0cc3c5d350f83e395c31c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591082"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="718c4-102">Nerozbalené zprávy</span><span class="sxs-lookup"><span data-stu-id="718c4-102">Unwrapped Messages</span></span>
<span data-ttu-id="718c4-103">Tento příklad ukazuje nezabalené zprávy.</span><span class="sxs-lookup"><span data-stu-id="718c4-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="718c4-104">Ve výchozím nastavení je tělo zprávy formátováno tak, že parametry operace služby jsou zabaleny.</span><span class="sxs-lookup"><span data-stu-id="718c4-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="718c4-105">Následující ukázka ukazuje `Add` zprávu požadavku `ICalculator` služby v zabaleném režimu.</span><span class="sxs-lookup"><span data-stu-id="718c4-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="718c4-106">`<Add>`Prvek v těle zprávy balí `n1` `n2` parametry a.</span><span class="sxs-lookup"><span data-stu-id="718c4-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="718c4-107">Naproti tomu následující příklad ukazuje ekvivalentní zprávu v nezabaleném režimu.</span><span class="sxs-lookup"><span data-stu-id="718c4-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
```  
  
 <span data-ttu-id="718c4-108">Nezabalená zpráva nezabalí `n1` `n2` parametry a v obsahujícím elementu, jsou přímými podřízenými elementy SOAP těla elementu.</span><span class="sxs-lookup"><span data-stu-id="718c4-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="718c4-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="718c4-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="718c4-110">V této ukázce je vytvořena nezabalená zpráva pomocí <xref:System.ServiceModel.MessageContractAttribute> typu parametru operace služby a typu vrácené hodnoty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="718c4-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="718c4-111">Aby bylo možné zobrazit zprávy odesílané a přijímané, Tato ukázka používá trasování.</span><span class="sxs-lookup"><span data-stu-id="718c4-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="718c4-112">Kromě toho byl <xref:System.ServiceModel.WSHttpBinding> nakonfigurován bez zabezpečení pro snížení počtu zpráv, které protokoluje.</span><span class="sxs-lookup"><span data-stu-id="718c4-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="718c4-113">Výsledný protokol trasování (c:\logs\Message.log) lze zobrazit pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="718c4-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="718c4-114">Chcete-li zobrazit obsah zprávy, vyberte **zprávy** v levém a pravém podokně nástroje Prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="718c4-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="718c4-115">Protokoly trasování v této ukázce jsou nakonfigurovány tak, aby se vygenerovaly do složky C:\Logs..</span><span class="sxs-lookup"><span data-stu-id="718c4-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="718c4-116">Před spuštěním ukázky vytvořte tuto složku a poskytněte uživateli síťová služba oprávnění k zápisu do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="718c4-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="718c4-117">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="718c4-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="718c4-118">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="718c4-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="718c4-119">Vytvořte adresář C:\Logs. pro protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="718c4-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="718c4-120">Udělte síťové službě uživateli oprávnění zapisovat pro tento adresář.</span><span class="sxs-lookup"><span data-stu-id="718c4-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="718c4-121">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="718c4-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="718c4-122">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="718c4-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="718c4-123">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="718c4-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="718c4-124">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="718c4-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="718c4-125">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="718c4-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="718c4-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="718c4-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
