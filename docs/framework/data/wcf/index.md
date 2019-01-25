---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: e203e872ac0dce10fa7119388bae2472cb7e6b44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588236"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="2d539-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="2d539-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="2d539-103">Služby WCF Data Services (dříve označované jako "Služby ADO.NET Data Services") je součástí rozhraní .NET Framework, která umožňuje vytvářet služby, které používají [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] k vystavení a zpracování dat prostřednictvím webu nebo intranetu pomocí sémantiky [ (REST) Representational state transfer](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="2d539-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="2d539-104">OData zveřejňuje data jako prostředky, které jsou adresovat pomocí identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="2d539-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="2d539-105">Data se získat přístup, změnit pomocí standardní příkazy HTTP z GET, PUT, POST a DELETE.</span><span class="sxs-lookup"><span data-stu-id="2d539-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="2d539-106">Používá relace entity konvencí OData [modelu Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) vystavit prostředky jako sady entit, které se týkají přidružení.</span><span class="sxs-lookup"><span data-stu-id="2d539-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="2d539-107">Služby WCF Data Services používá protokol OData pro adresy a aktualizaci prostředků.</span><span class="sxs-lookup"><span data-stu-id="2d539-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="2d539-108">Tímto způsobem přistupujete k těmto službám z libovolného klienta, který podporuje prostředí OData.</span><span class="sxs-lookup"><span data-stu-id="2d539-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="2d539-109">OData umožňuje vyžádat a zapisovat data do zdroje s použitím dobře známé převod formátů: Atom, sada standardů pro výměnu a aktualizace dat ve formátu XML, JavaScript Object Notation (JSON), formát dat založený na textu exchange často používají v aplikaci AJAX.</span><span class="sxs-lookup"><span data-stu-id="2d539-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>

<span data-ttu-id="2d539-110">Datové služby WCF můžete zpřístupnit data, která pochází z různých zdrojů, jako k datovým kanálům OData.</span><span class="sxs-lookup"><span data-stu-id="2d539-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="2d539-111">Nástroje sady Visual Studio usnadňují vytvoření služby založených na protokolu OData s použitím datový model ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2d539-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="2d539-112">Můžete také vytvořit na základě běžné třídy language runtime (CLR) a dokonce i s pozdní vazbou nebo netypové datové kanály OData.</span><span class="sxs-lookup"><span data-stu-id="2d539-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="2d539-113">Služby WCF Data Services obsahuje také sada klientských knihoven, jeden pro obecné klientské aplikace rozhraní .NET Framework a druhý speciálně pro aplikace založené na technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2d539-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="2d539-114">Tyto klientské knihovny poskytuje programovací model založený na objektu při přístupu z prostředí, jako je rozhraní .NET Framework a Silverlight datového kanálu OData.</span><span class="sxs-lookup"><span data-stu-id="2d539-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="2d539-115">Kde bych měl(a) začít?</span><span class="sxs-lookup"><span data-stu-id="2d539-115">Where Should I Start?</span></span>

<span data-ttu-id="2d539-116">V závislosti na vašich zájmech vezměte v úvahu Začínáme se službou WCF Data Services v jednom z následujících témat.</span><span class="sxs-lookup"><span data-stu-id="2d539-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="2d539-117">Chci pustit do práce …</span><span class="sxs-lookup"><span data-stu-id="2d539-117">I want to jump right in...</span></span>

-   [<span data-ttu-id="2d539-118">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="2d539-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="2d539-119">Začínáme</span><span class="sxs-lookup"><span data-stu-id="2d539-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [<span data-ttu-id="2d539-120">Silverlight Quickstart</span><span class="sxs-lookup"><span data-stu-id="2d539-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="2d539-121">Silverlight Quickstart pro vývoj pro Windows Phone</span><span class="sxs-lookup"><span data-stu-id="2d539-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="2d539-122">Stačí ukázat kódu...</span><span class="sxs-lookup"><span data-stu-id="2d539-122">Just show me some code...</span></span>

-   [<span data-ttu-id="2d539-123">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="2d539-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [<span data-ttu-id="2d539-124">Postupy: Spuštění dotazů v datové službě</span><span class="sxs-lookup"><span data-stu-id="2d539-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [<span data-ttu-id="2d539-125">Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="2d539-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="2d539-126">Chci vědět více o OData...</span><span class="sxs-lookup"><span data-stu-id="2d539-126">I want to know more about OData...</span></span>

 -   [<span data-ttu-id="2d539-127">Dokument White Paper: Úvod do prostředí OData</span><span class="sxs-lookup"><span data-stu-id="2d539-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="2d539-128">Otevřít web Data protokolu</span><span class="sxs-lookup"><span data-stu-id="2d539-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [<span data-ttu-id="2d539-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="2d539-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [<span data-ttu-id="2d539-130">OData: Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="2d539-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="2d539-131">Chci některé videa...</span><span class="sxs-lookup"><span data-stu-id="2d539-131">I want to watch some videos...</span></span>

-   [<span data-ttu-id="2d539-132">Průvodce pro začátečníky služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2d539-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [<span data-ttu-id="2d539-133">WCF Data Services – video pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2d539-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [<span data-ttu-id="2d539-134">OData: Vývojáři webové stránky</span><span class="sxs-lookup"><span data-stu-id="2d539-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="2d539-135">Chci zobrazit-koncové ukázky...</span><span class="sxs-lookup"><span data-stu-id="2d539-135">I want to see end-to-end samples...</span></span>

-   [<span data-ttu-id="2d539-136">Dokumentace ke službě vzorky z Galerie ukázek MSDN služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2d539-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [<span data-ttu-id="2d539-137">Další WCF Data Services – ukázky na Galerie ukázek MSDN</span><span class="sxs-lookup"><span data-stu-id="2d539-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [<span data-ttu-id="2d539-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="2d539-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="2d539-139">Jak zajistíte jejich integraci se sadou Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="2d539-139">How does it integrate with Visual Studio?</span></span>

-   [<span data-ttu-id="2d539-140">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="2d539-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [<span data-ttu-id="2d539-141">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="2d539-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [<span data-ttu-id="2d539-142">Zprostředkovatel Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2d539-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="2d539-143">Co můžu dělat s ním?</span><span class="sxs-lookup"><span data-stu-id="2d539-143">What can I do with it?</span></span>

-   [<span data-ttu-id="2d539-144">Přehled</span><span class="sxs-lookup"><span data-stu-id="2d539-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [<span data-ttu-id="2d539-145">Dokument White Paper: Úvod do prostředí OData</span><span class="sxs-lookup"><span data-stu-id="2d539-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [<span data-ttu-id="2d539-146">Scénáře aplikací</span><span class="sxs-lookup"><span data-stu-id="2d539-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

<span data-ttu-id="2d539-147">Chci používat Silverlight...</span><span class="sxs-lookup"><span data-stu-id="2d539-147">I want to use Silverlight...</span></span>

-   [<span data-ttu-id="2d539-148">Silverlight Quickstart</span><span class="sxs-lookup"><span data-stu-id="2d539-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [<span data-ttu-id="2d539-149">Datové služby WCF (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="2d539-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [<span data-ttu-id="2d539-150">Začínáme s aplikací Silverlight</span><span class="sxs-lookup"><span data-stu-id="2d539-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="2d539-151">Chci používat LINQ...</span><span class="sxs-lookup"><span data-stu-id="2d539-151">I want to use LINQ...</span></span>

-   [<span data-ttu-id="2d539-152">Dotazování v datové službě</span><span class="sxs-lookup"><span data-stu-id="2d539-152">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [<span data-ttu-id="2d539-153">Aspekty LINQ</span><span class="sxs-lookup"><span data-stu-id="2d539-153">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [<span data-ttu-id="2d539-154">Postupy: Spuštění dotazů v datové službě</span><span class="sxs-lookup"><span data-stu-id="2d539-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="2d539-155">Potřebuji ještě nějaké další informace...</span><span class="sxs-lookup"><span data-stu-id="2d539-155">I still need some more information...</span></span>

-   [<span data-ttu-id="2d539-156">Blog týmu služby WCF Data</span><span class="sxs-lookup"><span data-stu-id="2d539-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [<span data-ttu-id="2d539-157">Prostředky</span><span class="sxs-lookup"><span data-stu-id="2d539-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [<span data-ttu-id="2d539-158">Středisko pro vývojáře služby WCF Data</span><span class="sxs-lookup"><span data-stu-id="2d539-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [<span data-ttu-id="2d539-159">Otevřít web Data protokolu</span><span class="sxs-lookup"><span data-stu-id="2d539-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="2d539-160">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2d539-160">In This Section</span></span>

 [<span data-ttu-id="2d539-161">Přehled</span><span class="sxs-lookup"><span data-stu-id="2d539-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 <span data-ttu-id="2d539-162">Poskytuje přehled funkcí a možností, které jsou k dispozici ve službě WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="2d539-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

 [<span data-ttu-id="2d539-163">Co je nového ve službě WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2d539-163">What's New in WCF Data Services</span></span>](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 <span data-ttu-id="2d539-164">Popisuje nové funkce služeb WCF Data Services a podpora pro nové funkce OData.</span><span class="sxs-lookup"><span data-stu-id="2d539-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

 [<span data-ttu-id="2d539-165">Začínáme</span><span class="sxs-lookup"><span data-stu-id="2d539-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 <span data-ttu-id="2d539-166">Popisuje, jak vystavení a spotřebování informační kanály OData s použitím služeb WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="2d539-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

 [<span data-ttu-id="2d539-167">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2d539-167">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 <span data-ttu-id="2d539-168">Popisuje postup vytvoření a konfigurace datové služby, která zveřejňuje informační kanály OData.</span><span class="sxs-lookup"><span data-stu-id="2d539-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

 [<span data-ttu-id="2d539-169">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2d539-169">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 <span data-ttu-id="2d539-170">Popisuje, jak pomocí klientských knihoven využívat informačních kanálů OData z klientské aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d539-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d539-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d539-171">See also</span></span>

- [<span data-ttu-id="2d539-172">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="2d539-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
