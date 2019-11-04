---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: a259f459606c9745fe10276d967946eb675a7f5e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423801"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="5a666-102">WebContentTypeMapper – ukázka</span><span class="sxs-lookup"><span data-stu-id="5a666-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="5a666-103">Tato ukázka předvádí, jak namapovat nové typy obsahu na Windows Communication Foundation (WCF) formáty textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="5a666-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="5a666-104">Prvek <xref:System.ServiceModel.Description.WebHttpEndpoint> se zapojuje do kodéru webové zprávy, který umožňuje WCF přijímat zprávy JSON, XML nebo RAW ve stejném koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="5a666-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="5a666-105">Kodér určí formát textu zprávy na základě typu obsahu HTTP žádosti.</span><span class="sxs-lookup"><span data-stu-id="5a666-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="5a666-106">Tato ukázka zavádí třídu <xref:System.ServiceModel.Channels.WebContentTypeMapper>, která umožňuje uživateli řídit mapování mezi typem obsahu a formátem textu.</span><span class="sxs-lookup"><span data-stu-id="5a666-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="5a666-107">WCF poskytuje sadu výchozích mapování pro typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="5a666-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="5a666-108">Například `application/json` mapuje na JSON a `text/xml` mapuje na XML.</span><span class="sxs-lookup"><span data-stu-id="5a666-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="5a666-109">Jakýkoli typ obsahu, který není namapován na JSON nebo XML, je namapován na nezpracovaný binární formát.</span><span class="sxs-lookup"><span data-stu-id="5a666-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="5a666-110">V některých scénářích (například rozhraní API pro nabízené oznámení) vývojář služby neřídí typ obsahu vrácený klientem.</span><span class="sxs-lookup"><span data-stu-id="5a666-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="5a666-111">Například klienti mohou vracet JSON jako `text/javascript` místo `application/json`.</span><span class="sxs-lookup"><span data-stu-id="5a666-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="5a666-112">V tomto případě musí vývojář služby poskytnout typ, který je odvozen z <xref:System.ServiceModel.Channels.WebContentTypeMapper> pro správné zpracování daného typu obsahu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5a666-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="5a666-113">Typ musí přepsat metodu <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="5a666-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="5a666-114">Metoda musí vyhodnotit `contentType` argument a vracet jednu z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="5a666-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="5a666-115">Vrácení <xref:System.ServiceModel.Channels.WebContentFormat.Default> se odloží na výchozí mapování kodéru webových zpráv.</span><span class="sxs-lookup"><span data-stu-id="5a666-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="5a666-116">V předchozím ukázkovém kódu se `text/javascript` typ obsahu mapuje na JSON a všechna ostatní mapování zůstanou beze změny.</span><span class="sxs-lookup"><span data-stu-id="5a666-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="5a666-117">Chcete-li použít třídu `JsonContentTypeMapper`, použijte následující v souboru Web. config:</span><span class="sxs-lookup"><span data-stu-id="5a666-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5a666-118">Chcete-li ověřit požadavek na použití JsonContentTypeMapper, odeberte z výše uvedeného konfiguračního souboru atribut contentTypeMapper.</span><span class="sxs-lookup"><span data-stu-id="5a666-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="5a666-119">Při pokusu o použití `text/javascript` k odeslání obsahu JSON se stránka klienta nenačte.</span><span class="sxs-lookup"><span data-stu-id="5a666-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a666-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5a666-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5a666-121">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a666-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5a666-122">Sestavte řešení WebContentTypeMapperSample. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a666-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5a666-123">Přejděte na `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (neotevírejte JCTMClientPage. htm v prohlížeči v rámci adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="5a666-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a666-124">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="5a666-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a666-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5a666-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5a666-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="5a666-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a666-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5a666-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
