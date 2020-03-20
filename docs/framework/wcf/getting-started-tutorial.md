---
title: 'Kurz: Začínáme s aplikacemi Windows Communication Foundation'
description: Tyto kurzy poskytuje úvod pro vytváření wcf aplikací.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184112"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="ab4f9-103">Kurz: Začínáme s aplikacemi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ab4f9-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="ab4f9-104">Následující série výukových programů vás seznámí s programovacím prostředím Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="ab4f9-105">Práce prostřednictvím těchto kurzů v pořadí vám poskytne úvodní pochopení kroků potřebných k vytvoření wcf aplikací.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="ab4f9-106">Po dokončení budete mít spuštěnou službu WCF a klienta WCF, který službu volá.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="ab4f9-107">Kurz předpokládá, že používáte Visual Studio jako vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="ab4f9-108">Pokud používáte jiné vývojové prostředí, ignorujte pokyny specifické pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="ab4f9-109">Ukázkové aplikace WCF, které můžete stáhnout a spustit, naleznete v [tématu Ukázky windows communication foundation](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="ab4f9-110">Úvod do vzorků najdete v tématu [Ukázka Začínáme](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="ab4f9-111">Podrobnější informace o vytváření služeb a klientů naleznete v [tématu Basic WCF programming](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="ab4f9-112">Kurzy WCF</span><span class="sxs-lookup"><span data-stu-id="ab4f9-112">WCF tutorials</span></span>

<span data-ttu-id="ab4f9-113">První tři kurzy popisují, jak definovat servisní smlouvu WCF, jak ji implementovat a jak ji hostovat.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="ab4f9-114">Služba, kterou vytvoříte, je hostována sama v rámci konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="ab4f9-115">Služby můžete hostovat také v rámci služby Microsoft Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="ab4f9-116">Další informace naleznete v [tématu How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="ab4f9-117">Přestože službu v kurzu nakonfigurujete pomocí kódu, můžete také [konfigurovat služby v konfiguračním souboru](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="ab4f9-118">Kurz: Definování smlouvy o poskytování služeb</span><span class="sxs-lookup"><span data-stu-id="ab4f9-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="ab4f9-119">Vytvoříte smlouvu WCF s uživatelem definovaným rozhraním.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="ab4f9-120">Tato smlouva definuje funkce, které služba zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="ab4f9-121">Kurz: Implementace smlouvy o poskytování služeb</span><span class="sxs-lookup"><span data-stu-id="ab4f9-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="ab4f9-122">Po definování smlouvy je nutné ji implementovat s třídou služeb.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="ab4f9-123">Kurz: Hostování a spuštění základní služby</span><span class="sxs-lookup"><span data-stu-id="ab4f9-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="ab4f9-124">Nakonfigurujte koncový bod pro službu a hostujte službu v aplikaci konzoly.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="ab4f9-125">Aby se služba stala aktivní, musíte ji nakonfigurovat a hostovat v prostředí za běhu.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="ab4f9-126">Toto prostředí run-time vytvoří službu a řídí její kontext a životnost.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="ab4f9-127">Další dva kurzy popisují, jak vytvořit, nakonfigurovat a použít klientskou aplikaci k volání operací, které služba zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="ab4f9-128">Služby publikují metadata, která definují informace, které klientská aplikace potřebuje ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="ab4f9-129">Visual Studio automatizuje proces přístupu k těmto metadatům a používá jej k vytvoření klientské aplikace pro službu.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="ab4f9-130">Pokud se rozhodnete nepoužívat Visual Studio, můžete místo toho použít [nástroj ServiceModel Metadata Utility (*Svcutil.exe*](servicemodel-metadata-utility-tool-svcutil-exe.md) ).</span><span class="sxs-lookup"><span data-stu-id="ab4f9-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="ab4f9-131">Kurz: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="ab4f9-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="ab4f9-132">Načtěte metadata pro vytvoření proxy klienta WCF ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="ab4f9-133">Metadata načtete pomocí sady Visual Studio k přidání odkazu na službu nebo můžete použít nástroj ServiceModel Metadata Utility.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="ab4f9-134">Zadáte koncový bod, který klient používá pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="ab4f9-135">Kurz: Použití klienta</span><span class="sxs-lookup"><span data-stu-id="ab4f9-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="ab4f9-136">K volání operací služby použijte proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ab4f9-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="ab4f9-137">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="ab4f9-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="ab4f9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab4f9-138">See also</span></span>

- [<span data-ttu-id="ab4f9-139">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="ab4f9-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="ab4f9-140">Průvodce dokumentací</span><span class="sxs-lookup"><span data-stu-id="ab4f9-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="ab4f9-141">Co je Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ab4f9-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="ab4f9-142">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="ab4f9-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="ab4f9-143">Základní životní cyklus programování</span><span class="sxs-lookup"><span data-stu-id="ab4f9-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="ab4f9-144">Budování klientů</span><span class="sxs-lookup"><span data-stu-id="ab4f9-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="ab4f9-145">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="ab4f9-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="ab4f9-146">Postup: Vytvoření duplexní smlouvy</span><span class="sxs-lookup"><span data-stu-id="ab4f9-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="ab4f9-147">Postup: Přístup ke službám s duplexní smlouvou</span><span class="sxs-lookup"><span data-stu-id="ab4f9-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="ab4f9-148">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ab4f9-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="ab4f9-149">Postup: Stažení dokumentů metadat pomocí nástroje Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="ab4f9-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="ab4f9-150">Postup: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ab4f9-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="ab4f9-151">Použití vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ab4f9-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ab4f9-152">Ukázka začínáme</span><span class="sxs-lookup"><span data-stu-id="ab4f9-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="ab4f9-153">Ukázky nadace Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ab4f9-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="ab4f9-154">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="ab4f9-154">Self-Host</span></span>](samples/self-host.md)
