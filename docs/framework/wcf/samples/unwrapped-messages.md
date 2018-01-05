---
title: "Nerozbalené zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6014ee5fa7f714340f7069e5b5d39e6b4146dbb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="unwrapped-messages"></a><span data-ttu-id="8ad9e-102">Nerozbalené zprávy</span><span class="sxs-lookup"><span data-stu-id="8ad9e-102">Unwrapped Messages</span></span>
<span data-ttu-id="8ad9e-103">Tento příklad znázorňuje nerozbalené zprávy.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="8ad9e-104">Ve výchozím nastavení tělo zprávy je naformátován tak, že jsou zabalené parametry, které chcete operaci služby.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="8ad9e-105">Následující ukázkové ukazuje `Add` zpráva požadavku k `ICalculator` služby v zabalené režimu.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s=http://www.w3.org/2003/05/soap-envelope  
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
  
 <span data-ttu-id="8ad9e-106">`<Add>` Zabalí element v textu zprávy `n1` a `n2` parametry.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="8ad9e-107">Naopak v následujícím příkladu vidíte ekvivalentní zpráva v rozbalenou režimu.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
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
  
 <span data-ttu-id="8ad9e-108">Rozbalená zpráva není zalomen `n1` a `n2` parametry v elementu s obsahem, jsou přímo podřízené elementu těla protokolu soap.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ad9e-109">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8ad9e-110">V této ukázce, vytvoří se rozbalenou zpráva s použitím <xref:System.ServiceModel.MessageContractAttribute> typ parametru operace služby a typ návratové hodnoty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="8ad9e-111">Abyste mohli zobrazit zprávy se odesílají a přijímají, používá tato ukázka trasování.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="8ad9e-112">Kromě toho <xref:System.ServiceModel.WSHttpBinding> nakonfigurovaný bez zabezpečení, a snížit počet zpráv protokoluje.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="8ad9e-113">Výsledný protokolu trasování (c:\logs\Message.log) lze zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8ad9e-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="8ad9e-114">Chcete-li zobrazit obsah zprávy, vyberte **zprávy** v vlevo a vpravo podokna nástroje prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="8ad9e-115">Má být vygenerován do složky, C:\LOGS jsou nakonfigurované protokoly trasování v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="8ad9e-116">Vytvořte tuto složku před spuštěním ukázky a přidělit uživateli oprávnění pro tento adresář pro zápis síťové služby.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ad9e-117">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="8ad9e-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8ad9e-118">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ad9e-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8ad9e-119">Vytvořte C:\LOGS adresář pro protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="8ad9e-120">Síťová služba zápisu oprávnění pro tento adresář uživateli přidělte.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="8ad9e-121">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ad9e-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="8ad9e-122">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8ad9e-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ad9e-123">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8ad9e-124">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8ad9e-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8ad9e-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ad9e-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8ad9e-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="8ad9e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ad9e-127">See Also</span></span>
