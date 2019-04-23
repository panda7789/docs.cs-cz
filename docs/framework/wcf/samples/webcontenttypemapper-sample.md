---
title: WebContentTypeMapper – ukázka
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 381fc4a3084b1a2620384a04de85b9085e02ae16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973509"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="b1166-102">WebContentTypeMapper – ukázka</span><span class="sxs-lookup"><span data-stu-id="b1166-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="b1166-103">Tato ukázka předvádí, jak namapovat nové typy obsahu formáty text zpráv Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b1166-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="b1166-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Element připojí kodér zprávy webové, což umožňuje WCF JSON, XML nebo Nezpracovaná binární zprávy na stejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b1166-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="b1166-105">Kodér Určuje formát těla zprávy pomocí protokolu HTTP content-type žádosti.</span><span class="sxs-lookup"><span data-stu-id="b1166-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="b1166-106">Tato ukázka představuje <xref:System.ServiceModel.Channels.WebContentTypeMapper> třídu, která umožňuje uživateli řídit mapování typu obsahu a formát těla zprávy.</span><span class="sxs-lookup"><span data-stu-id="b1166-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="b1166-107">WCF obsahuje sadu výchozích mapování pro typy obsahu.</span><span class="sxs-lookup"><span data-stu-id="b1166-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="b1166-108">Například `application/json` mapuje do formátu JSON a `text/xml` mapuje na XML.</span><span class="sxs-lookup"><span data-stu-id="b1166-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="b1166-109">Jakýkoli typ obsahu, který není namapovaný na XML nebo JSON se mapuje na nezpracovaná binární formát.</span><span class="sxs-lookup"><span data-stu-id="b1166-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="b1166-110">V některých případech (například stylu push API) služby pro vývojáře neřídí typ obsahu vrácených klienta.</span><span class="sxs-lookup"><span data-stu-id="b1166-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="b1166-111">Například klienti může vrátit JSON jako `text/javascript` místo `application/json`.</span><span class="sxs-lookup"><span data-stu-id="b1166-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="b1166-112">V takovém případě vývojářem služeb, musíte zadat typ, který je odvozen od <xref:System.ServiceModel.Channels.WebContentTypeMapper> zpracování daného typu obsahu správně, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="b1166-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b1166-113">Typ musí přepsat <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="b1166-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="b1166-114">Metoda se musí vyhodnotit `contentType` argument a návratové jednu z následujících hodnot: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, nebo <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="b1166-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="b1166-115">Vrací <xref:System.ServiceModel.Channels.WebContentFormat.Default> odloží k výchozímu mapování kodéru zpráv Web.</span><span class="sxs-lookup"><span data-stu-id="b1166-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="b1166-116">V předchozí ukázce kódu `text/javascript` obsahu typu je mapována do formátu JSON a jiných mapováních zůstanou beze změny.</span><span class="sxs-lookup"><span data-stu-id="b1166-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="b1166-117">Použít `JsonContentTypeMapper` třídy, použijte tuto v souboru Web.config:</span><span class="sxs-lookup"><span data-stu-id="b1166-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b1166-118">Chcete-li ověřit požadavky pro použití JsonContentTypeMapper, odeberte atribut contentTypeMapper z výše uvedených konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b1166-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="b1166-119">Na stránce klienta se nepodaří načíst při pokusu o použití `text/javascript` odeslat obsah JSON.</span><span class="sxs-lookup"><span data-stu-id="b1166-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b1166-120">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="b1166-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b1166-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1166-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b1166-122">Sestavte řešení WebContentTypeMapperSample.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1166-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b1166-123">Přejděte na `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (neotevírejte JCTMClientPage.htm v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="b1166-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1166-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b1166-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1166-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b1166-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b1166-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b1166-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1166-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b1166-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
