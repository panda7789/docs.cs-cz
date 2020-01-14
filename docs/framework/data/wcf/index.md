---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: aace683b1a105445b5a3ba3de0a6a671859588b5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937446"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="03937-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="03937-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="03937-103">WCF Data Services (dříve označované jako "ADO.NET Data Services") je součástí .NET Framework, která umožňuje vytvářet služby, které používají protokol OData (Open Data Protocol) k vystavování a využívání dat prostřednictvím webu nebo intranetu, a to pomocí sémantiky opětovného [přenosu stavu (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="03937-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="03937-104">OData zpřístupňuje data jako prostředky, které jsou adresovatelné pomocí identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="03937-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="03937-105">Data se získávají a mění pomocí standardních příkazů HTTP GET, PUT, POST a DELETE.</span><span class="sxs-lookup"><span data-stu-id="03937-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="03937-106">OData používá konvence vztahů mezi entitami [model EDM (Entity Data Model)](../adonet/entity-data-model.md) k vystavení prostředků jako sady entit, které souvisejí s přidruženími.</span><span class="sxs-lookup"><span data-stu-id="03937-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="03937-107">WCF Data Services používá protokol OData k adresování a aktualizaci prostředků.</span><span class="sxs-lookup"><span data-stu-id="03937-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="03937-108">Tímto způsobem můžete získat přístup k těmto službám z libovolného klienta, který podporuje OData.</span><span class="sxs-lookup"><span data-stu-id="03937-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="03937-109">OData vám umožňuje vyžádat a zapsat data do prostředků pomocí známých formátů přenosu: Atom, sady standardů pro výměnu a aktualizaci dat jako XML a JavaScript Object Notation (JSON). Formát výměny dat založený na textu se v AJAX široce používá. vyrovnání.</span><span class="sxs-lookup"><span data-stu-id="03937-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="03937-110">WCF Data Services můžou vystavovat data, která pocházejí z různých zdrojů, jako kanály OData.</span><span class="sxs-lookup"><span data-stu-id="03937-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="03937-111">Nástroje sady Visual Studio usnadňují vytvoření služby založené na protokolu OData pomocí Entity Framework datového modelu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="03937-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="03937-112">Můžete také vytvořit kanály OData na základě tříd modulu CLR (Common Language Runtime) a dokonce i pozdě vázaných nebo netypových dat.</span><span class="sxs-lookup"><span data-stu-id="03937-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="03937-113">WCF Data Services taky obsahuje sadu klientských knihoven, jednu pro obecné .NET Framework klientské aplikace a další specificky pro aplikace založené na programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="03937-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="03937-114">Tyto klientské knihovny poskytují model programování založený na objektech při přístupu k datovému kanálu OData z prostředí, jako jsou .NET Framework a Silverlight.</span><span class="sxs-lookup"><span data-stu-id="03937-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="03937-115">Kde mám začít?</span><span class="sxs-lookup"><span data-stu-id="03937-115">Where Should I Start?</span></span>

<span data-ttu-id="03937-116">V závislosti na vašich zájmech zvažte, jak začít s WCF Data Services v jednom z následujících témat.</span><span class="sxs-lookup"><span data-stu-id="03937-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="03937-117">Chci se pustit přímo v...</span><span class="sxs-lookup"><span data-stu-id="03937-117">I want to jump right in...</span></span>

- [<span data-ttu-id="03937-118">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="03937-118">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="03937-119">Začínáme</span><span class="sxs-lookup"><span data-stu-id="03937-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="03937-120">Pouze zobrazit kód...</span><span class="sxs-lookup"><span data-stu-id="03937-120">Just show me some code...</span></span>

- [<span data-ttu-id="03937-121">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="03937-121">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="03937-122">Postupy: Provádění dotazů v datové službě</span><span class="sxs-lookup"><span data-stu-id="03937-122">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="03937-123">Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="03937-123">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="03937-124">Chci se dozvědět víc o OData...</span><span class="sxs-lookup"><span data-stu-id="03937-124">I want to know more about OData...</span></span>

- [<span data-ttu-id="03937-125">Dokument White Paper: představení OData</span><span class="sxs-lookup"><span data-stu-id="03937-125">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="03937-126">Web s otevřeným datovým protokolem</span><span class="sxs-lookup"><span data-stu-id="03937-126">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="03937-127">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="03937-127">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="03937-128">Chci se podívat na ucelené ukázky...</span><span class="sxs-lookup"><span data-stu-id="03937-128">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="03937-129">[Rychlý Start WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="03937-129">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="03937-130">OData SDK – ukázkový kód</span><span class="sxs-lookup"><span data-stu-id="03937-130">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="03937-131">Jak se integruje se sadou Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="03937-131">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="03937-132">Generování klientské knihovny datové služby</span><span class="sxs-lookup"><span data-stu-id="03937-132">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="03937-133">Vytvoření datové služby</span><span class="sxs-lookup"><span data-stu-id="03937-133">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="03937-134">Zprostředkovatel Entity Framework</span><span class="sxs-lookup"><span data-stu-id="03937-134">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="03937-135">Co s tím můžu dělat?</span><span class="sxs-lookup"><span data-stu-id="03937-135">What can I do with it?</span></span>

- [<span data-ttu-id="03937-136">Přehled</span><span class="sxs-lookup"><span data-stu-id="03937-136">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="03937-137">Scénáře aplikací</span><span class="sxs-lookup"><span data-stu-id="03937-137">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="03937-138">Chci použít LINQ...</span><span class="sxs-lookup"><span data-stu-id="03937-138">I want to use LINQ...</span></span>

- [<span data-ttu-id="03937-139">Dotazování v datové službě</span><span class="sxs-lookup"><span data-stu-id="03937-139">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="03937-140">Aspekty LINQ</span><span class="sxs-lookup"><span data-stu-id="03937-140">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="03937-141">Postupy: Provádění dotazů v datové službě</span><span class="sxs-lookup"><span data-stu-id="03937-141">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="03937-142">Pořád ještě potřebuji nějaké další informace...</span><span class="sxs-lookup"><span data-stu-id="03937-142">I still need some more information...</span></span>

- [<span data-ttu-id="03937-143">Blog týmu WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="03937-143">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="03937-144">Prostředky</span><span class="sxs-lookup"><span data-stu-id="03937-144">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="03937-145">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="03937-145">In This Section</span></span>

[<span data-ttu-id="03937-146">Přehled</span><span class="sxs-lookup"><span data-stu-id="03937-146">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="03937-147">Poskytuje přehled funkcí a funkcí, které jsou k dispozici v WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="03937-147">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="03937-148">[Co je nového v WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="03937-148">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="03937-149">Popisuje nové funkce v WCF Data Services a podporu pro nové funkce OData.</span><span class="sxs-lookup"><span data-stu-id="03937-149">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="03937-150">Začínáme</span><span class="sxs-lookup"><span data-stu-id="03937-150">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="03937-151">Popisuje, jak vystavit a využívat kanály OData pomocí WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="03937-151">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="03937-152">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="03937-152">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="03937-153">Popisuje, jak vytvořit a nakonfigurovat datovou službu, která zveřejňuje kanály OData.</span><span class="sxs-lookup"><span data-stu-id="03937-153">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="03937-154">Klientská knihovna pro WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="03937-154">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="03937-155">Popisuje použití klientských knihoven ke využívání kanálů OData z klientské aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03937-155">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="03937-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03937-156">See also</span></span>

- [<span data-ttu-id="03937-157">Převádění stavu reprezentace (REST)</span><span class="sxs-lookup"><span data-stu-id="03937-157">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
