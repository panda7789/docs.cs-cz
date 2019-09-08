---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 017fe2177cf824d461b4c51ea805f75b6ddbe064
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779987"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="a5be1-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="a5be1-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="a5be1-103">WCF Data Services (dříve označované jako "ADO.NET Data Services") je součástí .NET Framework, která umožňuje vytvářet služby, které používají [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] k vystavení a využívání dat prostřednictvím webu nebo intranetu, a to pomocí sémantiky opětovného [stavu prezentace. přenos (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="a5be1-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="a5be1-104">OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="a5be1-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="a5be1-105">Data se získávají a mění pomocí standardních příkazů HTTP GET, PUT, POST a DELETE.</span><span class="sxs-lookup"><span data-stu-id="a5be1-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="a5be1-106">OData používá konvence vztahů mezi entitami [model EDM (Entity Data Model)](../adonet/entity-data-model.md) k vystavení prostředků jako sady entit, které souvisejí s přidruženími.</span><span class="sxs-lookup"><span data-stu-id="a5be1-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="a5be1-107">WCF Data Services používá protokol OData k adresování a aktualizaci prostředků.</span><span class="sxs-lookup"><span data-stu-id="a5be1-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="a5be1-108">Tímto způsobem můžete získat přístup k těmto službám z libovolného klienta, který podporuje OData.</span><span class="sxs-lookup"><span data-stu-id="a5be1-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="a5be1-109">OData umožňuje vyžádat a zapsat data do prostředků pomocí známých formátů přenosu: Atom, sada standardů pro výměnu a aktualizaci dat ve formátu XML a JavaScript Object Notation (JSON), textový formát výměny dat založený na rozsáhlých aplikacích v AJAX.</span><span class="sxs-lookup"><span data-stu-id="a5be1-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="a5be1-110">WCF Data Services můžou vystavovat data, která pocházejí z různých zdrojů, jako kanály OData.</span><span class="sxs-lookup"><span data-stu-id="a5be1-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="a5be1-111">Nástroje sady Visual Studio usnadňují vytvoření služby založené na protokolu OData pomocí Entity Framework datového modelu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a5be1-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="a5be1-112">Můžete také vytvořit kanály OData na základě tříd modulu CLR (Common Language Runtime) a dokonce i pozdě vázaných nebo netypových dat.</span><span class="sxs-lookup"><span data-stu-id="a5be1-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="a5be1-113">WCF Data Services taky obsahuje sadu klientských knihoven, jednu pro obecné .NET Framework klientské aplikace a další specificky pro aplikace založené na programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a5be1-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="a5be1-114">Tyto klientské knihovny poskytují model programování založený na objektech při přístupu k datovému kanálu OData z prostředí, jako jsou .NET Framework a Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a5be1-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="a5be1-115">Kde mám začít?</span><span class="sxs-lookup"><span data-stu-id="a5be1-115">Where Should I Start?</span></span>

<span data-ttu-id="a5be1-116">V závislosti na vašich zájmech zvažte, jak začít s WCF Data Services v jednom z následujících témat.</span><span class="sxs-lookup"><span data-stu-id="a5be1-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="a5be1-117">Chci se pustit přímo v...</span><span class="sxs-lookup"><span data-stu-id="a5be1-117">I want to jump right in...</span></span>

- [<span data-ttu-id="a5be1-118">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="a5be1-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="a5be1-119">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a5be1-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

- [<span data-ttu-id="a5be1-120">Rychlý Start pro Silverlight</span><span class="sxs-lookup"><span data-stu-id="a5be1-120">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="a5be1-121">Rychlý Start k programu Silverlight pro Windows Phone vývoj</span><span class="sxs-lookup"><span data-stu-id="a5be1-121">Silverlight Quickstart for Windows Phone Development</span></span>](https://go.microsoft.com/fwlink/?LinkID=214535)

<span data-ttu-id="a5be1-122">Pouze zobrazit kód...</span><span class="sxs-lookup"><span data-stu-id="a5be1-122">Just show me some code...</span></span>

- [<span data-ttu-id="a5be1-123">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="a5be1-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="a5be1-124">Postupy: Spouštění dotazů datové služby</span><span class="sxs-lookup"><span data-stu-id="a5be1-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="a5be1-125">Postupy: Vázání dat na prvky Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a5be1-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="a5be1-126">Chci se dozvědět víc o OData...</span><span class="sxs-lookup"><span data-stu-id="a5be1-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="a5be1-127">Dokument White Paper Představujeme OData</span><span class="sxs-lookup"><span data-stu-id="a5be1-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="a5be1-128">Otevřít web datového protokolu</span><span class="sxs-lookup"><span data-stu-id="a5be1-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="a5be1-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="a5be1-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="a5be1-130">OData: Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="a5be1-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="a5be1-131">Chci sledovat některá videa...</span><span class="sxs-lookup"><span data-stu-id="a5be1-131">I want to watch some videos...</span></span>

- [<span data-ttu-id="a5be1-132">Příručka pro začátečníky k WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5be1-132">Beginner's Guide to WCF Data Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=220864)

- [<span data-ttu-id="a5be1-133">Videa pro vývojáře WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5be1-133">WCF Data Services Developer Videos</span></span>](https://go.microsoft.com/fwlink/?LinkId=220861)

- [<span data-ttu-id="a5be1-134">OData: Web pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a5be1-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="a5be1-135">Chci se podívat na ucelené ukázky...</span><span class="sxs-lookup"><span data-stu-id="a5be1-135">I want to see end-to-end samples...</span></span>

- [<span data-ttu-id="a5be1-136">Ukázka dokumentace WCF Data Services v galerii ukázek na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="a5be1-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkID=220865)

- [<span data-ttu-id="a5be1-137">Další ukázky WCF Data Services v galerii ukázek na webu MSDN</span><span class="sxs-lookup"><span data-stu-id="a5be1-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](https://go.microsoft.com/fwlink/?LinkId=220866)

- [<span data-ttu-id="a5be1-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="a5be1-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="a5be1-139">Jak se integruje se sadou Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="a5be1-139">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="a5be1-140">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="a5be1-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="a5be1-141">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="a5be1-141">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="a5be1-142">Zprostředkovatel Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a5be1-142">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="a5be1-143">Co s tím můžu dělat?</span><span class="sxs-lookup"><span data-stu-id="a5be1-143">What can I do with it?</span></span>

- [<span data-ttu-id="a5be1-144">Přehled</span><span class="sxs-lookup"><span data-stu-id="a5be1-144">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="a5be1-145">Dokument White Paper Představujeme OData</span><span class="sxs-lookup"><span data-stu-id="a5be1-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="a5be1-146">Scénáře aplikací</span><span class="sxs-lookup"><span data-stu-id="a5be1-146">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="a5be1-147">Chci použít Silverlight...</span><span class="sxs-lookup"><span data-stu-id="a5be1-147">I want to use Silverlight...</span></span>

- [<span data-ttu-id="a5be1-148">Rychlý Start pro Silverlight</span><span class="sxs-lookup"><span data-stu-id="a5be1-148">Silverlight Quickstart</span></span>](https://go.microsoft.com/fwlink/?LinkID=192782)

- [<span data-ttu-id="a5be1-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="a5be1-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- [<span data-ttu-id="a5be1-150">Začínáme s Silverlightem</span><span class="sxs-lookup"><span data-stu-id="a5be1-150">Getting Started with Silverlight</span></span>](https://go.microsoft.com/fwlink/?LinkId=148366)

<span data-ttu-id="a5be1-151">Chci použít LINQ...</span><span class="sxs-lookup"><span data-stu-id="a5be1-151">I want to use LINQ...</span></span>

- [<span data-ttu-id="a5be1-152">Dotazování v datové službě</span><span class="sxs-lookup"><span data-stu-id="a5be1-152">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="a5be1-153">Aspekty LINQ</span><span class="sxs-lookup"><span data-stu-id="a5be1-153">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="a5be1-154">Postupy: Spouštění dotazů datové služby</span><span class="sxs-lookup"><span data-stu-id="a5be1-154">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="a5be1-155">Pořád ještě potřebuji nějaké další informace...</span><span class="sxs-lookup"><span data-stu-id="a5be1-155">I still need some more information...</span></span>

- [<span data-ttu-id="a5be1-156">Blog týmu WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5be1-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="a5be1-157">Prostředky</span><span class="sxs-lookup"><span data-stu-id="a5be1-157">Resources</span></span>](wcf-data-services-resources.md)

- [<span data-ttu-id="a5be1-158">Centrum pro vývojáře WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5be1-158">WCF Data Services Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=220868)

- [<span data-ttu-id="a5be1-159">Otevřít web datového protokolu</span><span class="sxs-lookup"><span data-stu-id="a5be1-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="a5be1-160">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a5be1-160">In This Section</span></span>

[<span data-ttu-id="a5be1-161">Přehled</span><span class="sxs-lookup"><span data-stu-id="a5be1-161">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="a5be1-162">Poskytuje přehled funkcí a funkcí, které jsou k dispozici v WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="a5be1-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="a5be1-163">[Co je nového v WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="a5be1-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="a5be1-164">Popisuje nové funkce v WCF Data Services a podporu pro nové funkce OData.</span><span class="sxs-lookup"><span data-stu-id="a5be1-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="a5be1-165">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a5be1-165">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="a5be1-166">Popisuje, jak vystavit a využívat kanály OData pomocí WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="a5be1-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="a5be1-167">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5be1-167">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="a5be1-168">Popisuje, jak vytvořit a nakonfigurovat datovou službu, která zveřejňuje kanály OData.</span><span class="sxs-lookup"><span data-stu-id="a5be1-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="a5be1-169">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a5be1-169">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="a5be1-170">Popisuje použití klientských knihoven ke využívání kanálů OData z klientské aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5be1-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5be1-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5be1-171">See also</span></span>

- [<span data-ttu-id="a5be1-172">Převádění stavu reprezentace (REST)</span><span class="sxs-lookup"><span data-stu-id="a5be1-172">Representational State Transfer (REST)</span></span>](https://go.microsoft.com/fwlink/?LinkId=113919)
