---
title: "WebContentTypeMapper – ukázka"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27342076290ca40abefea63edcc5f5c7186c4256
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="4250b-102">WebContentTypeMapper – ukázka</span><span class="sxs-lookup"><span data-stu-id="4250b-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="4250b-103">Tento příklad znázorňuje způsob namapování nové typy obsahu ke [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formáty text zprávy.</span><span class="sxs-lookup"><span data-stu-id="4250b-103">This sample demonstrates how to map new content types to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message body formats.</span></span>  
  
 <span data-ttu-id="4250b-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Element připojí kodér zpráv Web, který umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] k přijetí JSON, XML nebo Nezpracovaná binární zprávy se stejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="4250b-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="4250b-105">Kodér formátu textu zprávy určuje prohlížením hlavičku HTTP content-type požadavku.</span><span class="sxs-lookup"><span data-stu-id="4250b-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="4250b-106">Tato ukázka představuje <xref:System.ServiceModel.Channels.WebContentTypeMapper> třídy, která umožňuje uživateli řídit mapování mezi typu obsahu a formátu textu.</span><span class="sxs-lookup"><span data-stu-id="4250b-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4250b-107">poskytuje sadu výchozích mapování pro typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="4250b-107"> provides a set of default mappings for content types.</span></span> <span data-ttu-id="4250b-108">Například `application/json` mapy do formátu JSON a `text/xml` se mapuje na XML.</span><span class="sxs-lookup"><span data-stu-id="4250b-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="4250b-109">Jakýkoli typ obsahu, který není mapován na XML nebo JSON je namapována na nezpracovaná binární formát.</span><span class="sxs-lookup"><span data-stu-id="4250b-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="4250b-110">V některých případech (například nabízené stylu API) služba vývojáře neřídí obsahu typ vrácený klientem.</span><span class="sxs-lookup"><span data-stu-id="4250b-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="4250b-111">Například klienti může vrátit formát JSON jako `text/javascript` místo `application/json`.</span><span class="sxs-lookup"><span data-stu-id="4250b-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="4250b-112">V takovém případě vývojáře služby musíte zadat typ, který je odvozen od <xref:System.ServiceModel.Channels.WebContentTypeMapper> pro zpracování obsahu daného typu správně, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4250b-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="4250b-113">Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="4250b-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="4250b-114">Metoda se musí vyhodnotit `contentType` argument a návratové jeden z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="4250b-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="4250b-115">Vrácení <xref:System.ServiceModel.Channels.WebContentFormat.Default> odkládat údaje k výchozímu mapování kodér zpráv Web.</span><span class="sxs-lookup"><span data-stu-id="4250b-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="4250b-116">V předchozím ukázkovém kódu `text/javascript` obsahu typu je namapovaná na JSON a všechny ostatní mapování zůstanou beze změny.</span><span class="sxs-lookup"><span data-stu-id="4250b-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="4250b-117">Chcete-li použít `JsonContentTypeMapper` třídy, použijte následující v souboru Web.config:</span><span class="sxs-lookup"><span data-stu-id="4250b-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4250b-118">Pokud chcete ověřit pomocí JsonContentTypeMapper požadavek, odeberte atribut contentTypeMapper z výše uvedených konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4250b-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="4250b-119">Stránku Klient nepodaří načíst při pokusu o použití `text/javascript` odeslat obsah JSON.</span><span class="sxs-lookup"><span data-stu-id="4250b-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4250b-120">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4250b-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4250b-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4250b-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4250b-122">Sestavte řešení WebContentTypeMapperSample.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4250b-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4250b-123">Přejděte na http://localhost/ServiceModelSamples/JCTMClientPage.htm (neotevírejte JCTMClientPage.htm v prohlížeči z v adresáři projektu).</span><span class="sxs-lookup"><span data-stu-id="4250b-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4250b-124">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4250b-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4250b-125">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4250b-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4250b-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4250b-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4250b-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4250b-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="4250b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4250b-128">See Also</span></span>
