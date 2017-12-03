---
title: "Datové služby WCF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8a0ab816aa21082cf98462f5f9d7ffd20e4dcfd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="bbd66-102">Datové služby WCF 4.5</span><span class="sxs-lookup"><span data-stu-id="bbd66-102">WCF Data Services 4.5</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="bbd66-103">(dříve označované jako "ADO.NET Data Services") je součástí rozhraní .NET Framework, který umožňuje vytvářet služby, které používají [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] vystavení a spotřebování data prostřednictvím webu nebo intranetu pomocí sémantika [representational stavu Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="bbd66-103"> (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="bbd66-104">zpřístupní data jako prostředky, které jsou adresovat pomocí identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="bbd66-104"> exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="bbd66-105">Data se získat přístup a změnit pomocí standardních operací protokolu HTTP z GET, PUT, POST a odstranění.</span><span class="sxs-lookup"><span data-stu-id="bbd66-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="bbd66-106">používá pravidla vztah entit [datového modelu Entity](../../../../docs/framework/data/adonet/entity-data-model.md) vystavit prostředky jako sady entit, které jsou spojené přidružení.</span><span class="sxs-lookup"><span data-stu-id="bbd66-106"> uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="bbd66-107">používá [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokol pro adresování a aktualizaci prostředky.</span><span class="sxs-lookup"><span data-stu-id="bbd66-107"> uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="bbd66-108">Tímto způsobem můžete přistupovat z libovolného klienta, který podporuje tyto služby [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbd66-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="bbd66-109">můžete k vyžádání a zapisovat data k prostředkům pomocí známých přenos formáty: Atom, sadu standardy výměna a aktualizace dat jako soubor XML a JavaScript Object Notation (JSON) formátu exchange založený na textu dat, který je hojně používá v aplikaci AJAX.</span><span class="sxs-lookup"><span data-stu-id="bbd66-109"> enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="bbd66-110">můžou zpřístupnit data, která pochází z různých zdrojů jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály.</span><span class="sxs-lookup"><span data-stu-id="bbd66-110"> can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="bbd66-111">Nástroje sady Visual Studio vytvářet usnadňují [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě služby pomocí datový model ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="bbd66-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="bbd66-112">Můžete také vytvořit [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály na základě třídy společných language runtime (CLR) a data i pozdní vazbou nebo netypové.</span><span class="sxs-lookup"><span data-stu-id="bbd66-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="bbd66-113">také obsahuje sadu klientské knihovny, jednu pro obecné klientské aplikace rozhraní .NET Framework a druhou speciálně pro aplikace programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="bbd66-113"> also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="bbd66-114">Tyto knihovny klienta poskytují programovací model na základě objektů při přístupu [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanálu z prostředích, jako je rozhraní .NET Framework a program Silverlight.</span><span class="sxs-lookup"><span data-stu-id="bbd66-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="bbd66-115">Kde mám začít?</span><span class="sxs-lookup"><span data-stu-id="bbd66-115">Where Should I Start?</span></span>  
 <span data-ttu-id="bbd66-116">V závislosti na vašem zájmu, zvažte Začínáme s [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] v jednom z následujících témat.</span><span class="sxs-lookup"><span data-stu-id="bbd66-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="bbd66-117">Chcete rovnou...</span><span class="sxs-lookup"><span data-stu-id="bbd66-117">I want to jump right in…</span></span>  
 -   [<span data-ttu-id="bbd66-118">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="bbd66-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-119">Začínáme</span><span class="sxs-lookup"><span data-stu-id="bbd66-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-120">Rychlý start Silverlight</span><span class="sxs-lookup"><span data-stu-id="bbd66-120">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="bbd66-121">Rychlý start Silverlight pro vývoj pro Windows Phone</span><span class="sxs-lookup"><span data-stu-id="bbd66-121">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 <span data-ttu-id="bbd66-122">Právě ukázat nějaký kód...</span><span class="sxs-lookup"><span data-stu-id="bbd66-122">Just show me some code…</span></span>  
 -   [<span data-ttu-id="bbd66-123">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="bbd66-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-124">Postupy: provádění dotazů služby dat</span><span class="sxs-lookup"><span data-stu-id="bbd66-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-125">Postupy: vytvoření vazby dat na Windows Presentation Foundation elementy</span><span class="sxs-lookup"><span data-stu-id="bbd66-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 <span data-ttu-id="bbd66-126">Chci vědět více o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]...</span><span class="sxs-lookup"><span data-stu-id="bbd66-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   [<span data-ttu-id="bbd66-127">Dokument White Paper: Úvod OData</span><span class="sxs-lookup"><span data-stu-id="bbd66-127">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="bbd66-128">Otevřít web Data protokolu</span><span class="sxs-lookup"><span data-stu-id="bbd66-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="bbd66-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="bbd66-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [<span data-ttu-id="bbd66-130">OData: Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="bbd66-130">OData: Frequently Asked Questions</span></span>](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 <span data-ttu-id="bbd66-131">Chci videí, některé...</span><span class="sxs-lookup"><span data-stu-id="bbd66-131">I want to watch some videos…</span></span>  
 -   [<span data-ttu-id="bbd66-132">Průvodce začátečníka služby WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bbd66-132">Beginner's Guide to WCF Data Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [<span data-ttu-id="bbd66-133">Videa vývojáře služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bbd66-133">WCF Data Services Developer Videos</span></span>](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [<span data-ttu-id="bbd66-134">OData: Vývojáři webové stránky</span><span class="sxs-lookup"><span data-stu-id="bbd66-134">OData: Developers Web site</span></span>](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 <span data-ttu-id="bbd66-135">Chcete vidět začátku do konce ukázky</span><span class="sxs-lookup"><span data-stu-id="bbd66-135">I want to see end-to-end samples</span></span>  
 -   [<span data-ttu-id="bbd66-136">Ukázky dokumentace na MSDN ukázky Galerie služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bbd66-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [<span data-ttu-id="bbd66-137">Další WCF Data Services ukázek v Galerii ukázek webu MSDN</span><span class="sxs-lookup"><span data-stu-id="bbd66-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [<span data-ttu-id="bbd66-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="bbd66-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="bbd66-139">Jak zajistíte jejich integraci se sadou Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="bbd66-139">How does it integrate with Visual Studio?</span></span>  
 -   [<span data-ttu-id="bbd66-140">Generování dat služby klientské knihovny</span><span class="sxs-lookup"><span data-stu-id="bbd66-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-141">Vytváření datové služby</span><span class="sxs-lookup"><span data-stu-id="bbd66-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [<span data-ttu-id="bbd66-142">Zprostředkovatel Entity Framework</span><span class="sxs-lookup"><span data-stu-id="bbd66-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 <span data-ttu-id="bbd66-143">Co můžete dělat s ní?</span><span class="sxs-lookup"><span data-stu-id="bbd66-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="bbd66-144">Přehled</span><span class="sxs-lookup"><span data-stu-id="bbd66-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [<span data-ttu-id="bbd66-145">Dokument White Paper: Úvod OData</span><span class="sxs-lookup"><span data-stu-id="bbd66-145">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="bbd66-146">Scénáře aplikací</span><span class="sxs-lookup"><span data-stu-id="bbd66-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 <span data-ttu-id="bbd66-147">Chci používat Silverlight...</span><span class="sxs-lookup"><span data-stu-id="bbd66-147">I want to use Silverlight…</span></span>  
 -   [<span data-ttu-id="bbd66-148">Rychlý start Silverlight</span><span class="sxs-lookup"><span data-stu-id="bbd66-148">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="bbd66-149">Datové služby WCF (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="bbd66-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [<span data-ttu-id="bbd66-150">Začínáme s programem Silverlight</span><span class="sxs-lookup"><span data-stu-id="bbd66-150">Getting Started with Silverlight</span></span>](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 <span data-ttu-id="bbd66-151">Chcete vytvořit aplikaci pro Windows Phone...</span><span class="sxs-lookup"><span data-stu-id="bbd66-151">I want to create a Windows Phone application…</span></span>  
 -   [<span data-ttu-id="bbd66-152">Rychlý start Silverlight pro vývoj pro Windows Phone</span><span class="sxs-lookup"><span data-stu-id="bbd66-152">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [<span data-ttu-id="bbd66-153">Klient Open Data Protocol (OData) pro Windows Phone</span><span class="sxs-lookup"><span data-stu-id="bbd66-153">Open Data Protocol (OData) Client for Windows Phone</span></span>](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 <span data-ttu-id="bbd66-154">Chcete použít LINQ...</span><span class="sxs-lookup"><span data-stu-id="bbd66-154">I want to use LINQ…</span></span>  
 -   [<span data-ttu-id="bbd66-155">Dotaz na službu Data</span><span class="sxs-lookup"><span data-stu-id="bbd66-155">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-156">Aspekty LINQ</span><span class="sxs-lookup"><span data-stu-id="bbd66-156">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [<span data-ttu-id="bbd66-157">Postupy: provádění dotazů služby dat</span><span class="sxs-lookup"><span data-stu-id="bbd66-157">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 <span data-ttu-id="bbd66-158">Potřebuji některé další informace...</span><span class="sxs-lookup"><span data-stu-id="bbd66-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="bbd66-159">Blog týmu služby WCF Data</span><span class="sxs-lookup"><span data-stu-id="bbd66-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="bbd66-160">Prostředky</span><span class="sxs-lookup"><span data-stu-id="bbd66-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [<span data-ttu-id="bbd66-161">Středisku pro vývojáře WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bbd66-161">WCF Data Services Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [<span data-ttu-id="bbd66-162">Otevřít web Data protokolu</span><span class="sxs-lookup"><span data-stu-id="bbd66-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="bbd66-163">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bbd66-163">In This Section</span></span>  
 [<span data-ttu-id="bbd66-164">Přehled</span><span class="sxs-lookup"><span data-stu-id="bbd66-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="bbd66-165">Poskytuje přehled funkcí a funkcí, které jsou k dispozici v [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbd66-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="bbd66-166">Co je nového ve službě WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bbd66-166">What's New in WCF Data Services</span></span>](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 <span data-ttu-id="bbd66-167">Popisuje nové funkce [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] a podporu pro nové [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] funkce.</span><span class="sxs-lookup"><span data-stu-id="bbd66-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="bbd66-168">Začínáme</span><span class="sxs-lookup"><span data-stu-id="bbd66-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="bbd66-169">Popisuje, jak vystavení a spotřebování [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bbd66-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="bbd66-170">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="bbd66-170">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 <span data-ttu-id="bbd66-171">Popisuje, jak vytvořit a nakonfigurovat službu data, která zveřejňuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanály.</span><span class="sxs-lookup"><span data-stu-id="bbd66-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="bbd66-172">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bbd66-172">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 <span data-ttu-id="bbd66-173">Popisuje, jak pomocí klientské knihovny využívat [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informační kanály z klientské aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bbd66-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd66-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbd66-174">See Also</span></span>  
 [<span data-ttu-id="bbd66-175">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="bbd66-175">Representational State Transfer (REST)</span></span>](http://go.microsoft.com/fwlink/?LinkId=113919)
