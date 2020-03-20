---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143561"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="d204e-102">WebContentTypeMapper – ukázka</span><span class="sxs-lookup"><span data-stu-id="d204e-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="d204e-103">Tato ukázka ukazuje, jak mapovat nové typy obsahu na formáty textu zprávy Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d204e-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="d204e-104">Prvek <xref:System.ServiceModel.Description.WebHttpEndpoint> se zapojuje do kodéru webové zprávy, který umožňuje WCF přijímat JSON, XML nebo nezpracované binární zprávy ve stejném koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="d204e-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="d204e-105">Kodér určuje formát těla zprávy pohledem na typ obsahu HTTP požadavku.</span><span class="sxs-lookup"><span data-stu-id="d204e-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="d204e-106">Tato ukázka <xref:System.ServiceModel.Channels.WebContentTypeMapper> zavádí třídu, která umožňuje uživateli řídit mapování mezi typem obsahu a formátem těla.</span><span class="sxs-lookup"><span data-stu-id="d204e-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="d204e-107">WCF poskytuje sadu výchozí mapování pro typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="d204e-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="d204e-108">Například `application/json` mapuje na JSON a `text/xml` mapuje na XML.</span><span class="sxs-lookup"><span data-stu-id="d204e-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="d204e-109">Jakýkoli typ obsahu, který není mapován na JSON nebo XML, je mapován na nezpracovaný binární formát.</span><span class="sxs-lookup"><span data-stu-id="d204e-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="d204e-110">V některých scénářích (například nabízená řešení API) vývojář služby neřídí typ obsahu vrácený klientem.</span><span class="sxs-lookup"><span data-stu-id="d204e-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="d204e-111">Klienti mohou například vrátit JSON jako `text/javascript` namísto `application/json`.</span><span class="sxs-lookup"><span data-stu-id="d204e-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="d204e-112">V takovém případě musí vývojář služby poskytnout <xref:System.ServiceModel.Channels.WebContentTypeMapper> typ, který je odvozen od správného zpracování daného typu obsahu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d204e-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="d204e-113">Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metodu.</span><span class="sxs-lookup"><span data-stu-id="d204e-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="d204e-114">Metoda musí `contentType` vyhodnotit argument a vrátit jednu z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="d204e-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="d204e-115">Vrácení <xref:System.ServiceModel.Channels.WebContentFormat.Default> odloží na výchozí mapování kodéru webových zpráv.</span><span class="sxs-lookup"><span data-stu-id="d204e-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="d204e-116">V předchozím ukázkovém `text/javascript` kódu je typ obsahu mapován na JSON a všechna ostatní mapování zůstanou nezměněna.</span><span class="sxs-lookup"><span data-stu-id="d204e-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="d204e-117">Chcete-li `JsonContentTypeMapper` třídu použít, použijte ve svém souboru Web.config následující:</span><span class="sxs-lookup"><span data-stu-id="d204e-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d204e-118">Chcete-li ověřit požadavek na používání jsonContentTypeMapper, odeberte atribut contentTypeMapper z výše uvedeného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d204e-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="d204e-119">Při pokusu o odeslání `text/javascript` obsahu JSON se nenačte stránka klienta.</span><span class="sxs-lookup"><span data-stu-id="d204e-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d204e-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d204e-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d204e-121">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d204e-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d204e-122">Vytvořte řešení WebContentTypeMapperSample.sln, jak je popsáno v [části Vytváření ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d204e-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d204e-123">Přejděte `http://localhost/ServiceModelSamples/JCTMClientPage.htm` na (neotevírejte soubor JCTMClientPage.htm v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="d204e-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d204e-124">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d204e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d204e-125">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d204e-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d204e-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d204e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d204e-127">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d204e-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
