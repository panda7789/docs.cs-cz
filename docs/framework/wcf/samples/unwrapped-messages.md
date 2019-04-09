---
title: Nerozbalené zprávy
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 30c25bf6bb8b4ffe621007c03a7e913bba4379fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125376"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="f2067-102">Nerozbalené zprávy</span><span class="sxs-lookup"><span data-stu-id="f2067-102">Unwrapped Messages</span></span>
<span data-ttu-id="f2067-103">V této ukázce nerozbalené zprávy.</span><span class="sxs-lookup"><span data-stu-id="f2067-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="f2067-104">Ve výchozím nastavení text zprávy je formátováno tak, že jsou zabaleny parametry pro operaci služby.</span><span class="sxs-lookup"><span data-stu-id="f2067-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="f2067-105">Následující ukázka znázorňuje `Add` zprávy s požadavkem na `ICalculator` služby v režimu zabalené.</span><span class="sxs-lookup"><span data-stu-id="f2067-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="f2067-106">`<Add>` Zabalí element v textu zprávy `n1` a `n2` parametry.</span><span class="sxs-lookup"><span data-stu-id="f2067-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="f2067-107">Naproti tomu následující příklad ukazuje rovnocenné zprávy v nezabalené režimu.</span><span class="sxs-lookup"><span data-stu-id="f2067-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="f2067-108">Nerozbalené zprávy není zalomen `n1` a `n2` parametry v obsahující element jsou přímé podřízené objekty daného elementu těla protokolu soap.</span><span class="sxs-lookup"><span data-stu-id="f2067-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2067-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f2067-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f2067-110">V této ukázce se vytvoří nerozbalené zprávy použitím <xref:System.ServiceModel.MessageContractAttribute> typ parametru operace služby a typ návratové hodnoty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f2067-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="f2067-111">Aby bylo možné zobrazit zprávy se odeslané a přijaté, tato ukázka používá trasování.</span><span class="sxs-lookup"><span data-stu-id="f2067-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="f2067-112">Kromě toho <xref:System.ServiceModel.WSHttpBinding> není nakonfigurovaná bez zabezpečení k omezení počtu zpráv protokoluje.</span><span class="sxs-lookup"><span data-stu-id="f2067-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="f2067-113">Výsledný protokol trasování (c:\logs\Message.log) lze zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f2067-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="f2067-114">Chcete-li zobrazit obsah zprávy, vyberte **zprávy** vlevo a vpravo podokna nástroje prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="f2067-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="f2067-115">Vygenerování do složky C:\LOGS jsou nakonfigurované protokoly trasování v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="f2067-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="f2067-116">Vytvořte tuto složku před spuštěním ukázky a přidělit uživateli oprávnění pro tento adresář k zápisu síťové služby.</span><span class="sxs-lookup"><span data-stu-id="f2067-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f2067-117">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="f2067-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f2067-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2067-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f2067-119">Vytvoření C:\LOGS adresáře pro protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="f2067-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="f2067-120">Dejte uživateli oprávnění pro tento adresář k zápisu síťové služby.</span><span class="sxs-lookup"><span data-stu-id="f2067-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="f2067-121">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2067-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f2067-122">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2067-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2067-123">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="f2067-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2067-124">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f2067-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f2067-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f2067-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2067-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f2067-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
