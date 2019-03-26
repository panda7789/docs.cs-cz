---
title: 'Kurz: Začínáme s aplikacemi Windows Communication Foundation'
description: Tyto kurzy obsahuje úvod k vytváření aplikací WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 66211cfcf2b742e43eccbefb2bc7c4bd1147b05b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408857"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="d4c20-103">Kurz: Začínáme s aplikacemi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d4c20-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="d4c20-104">Následující sérii kurzů vám představí pro Windows Communication Foundation (WCF) programovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="d4c20-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="d4c20-105">Práce prostřednictvím těchto kurzů v pořadí vám poskytne úvodní znalost kroky potřebné k vytváření aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="d4c20-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="d4c20-106">Po dokončení budete mít spuštěnou službu WCF a klienta WCF, která volá službu.</span><span class="sxs-lookup"><span data-stu-id="d4c20-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span> 

<span data-ttu-id="d4c20-107">Kurz předpokládá, že používáte jako vývojové prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4c20-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="d4c20-108">Pokud používáte jiné vývojové prostředí, ignorujte Visual Studio konkrétní pokyny.</span><span class="sxs-lookup"><span data-stu-id="d4c20-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span> 

<span data-ttu-id="d4c20-109">Ukázkové aplikace WCF, které si můžete stáhnout a použít, najdete v části [ukázky Windows Communication Foundation](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="d4c20-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="d4c20-110">Úvod k ukázkám, najdete v článku [ukázka Začínáme](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d4c20-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="d4c20-111">Další podrobné informace o vytváření služeb a klientů najdete v tématu [základní programování WCF](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="d4c20-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="d4c20-112">Kurzy WCF</span><span class="sxs-lookup"><span data-stu-id="d4c20-112">WCF tutorials</span></span>

<span data-ttu-id="d4c20-113">První tři kurzy popisují definování kontraktu služby WCF, implementaci a hostujte si ji.</span><span class="sxs-lookup"><span data-stu-id="d4c20-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="d4c20-114">Je služba, kterou vytvoříte v rámci konzolové aplikace v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="d4c20-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="d4c20-115">Můžete také hostování služeb v rámci Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d4c20-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="d4c20-116">Další informace najdete v tématu [jak: Hostování služby WCF v IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="d4c20-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="d4c20-117">I když ke konfiguraci služby v tomto kurzu použijete kódu, můžete také [konfigurace služby v konfiguračním souboru](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="d4c20-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span> 

- [<span data-ttu-id="d4c20-118">Kurz: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="d4c20-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="d4c20-119">Vytvoření kontraktu WCF pomocí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d4c20-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="d4c20-120">Tento kontrakt definuje funkci, která poskytuje služby.</span><span class="sxs-lookup"><span data-stu-id="d4c20-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="d4c20-121">Kurz: Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="d4c20-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="d4c20-122">Po definování kontraktu, je nutné implementovat s třídou služby.</span><span class="sxs-lookup"><span data-stu-id="d4c20-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="d4c20-123">Kurz: Hostování a spuštění základní služby</span><span class="sxs-lookup"><span data-stu-id="d4c20-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="d4c20-124">Konfigurace koncového bodu služby a hostovat službu v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d4c20-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="d4c20-125">Služba aktivuje musíte ji nakonfigurovat a hostování v rámci prostředí za běhu.</span><span class="sxs-lookup"><span data-stu-id="d4c20-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="d4c20-126">Toto prostředí za běhu vytvoří službu a ovládací prvky jeho kontextu a životnosti.</span><span class="sxs-lookup"><span data-stu-id="d4c20-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="d4c20-127">Z následujících dvou kurzů popisuje, jak vytvořit, nakonfigurovat, a zpřístupňuje použití klientské aplikace k volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="d4c20-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="d4c20-128">Služby publikování metadat, které definují informace, které klientská aplikace potřebuje ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="d4c20-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="d4c20-129">Visual Studio automatizuje proces přístup k tato metadata a použije je k vytvoření klientské aplikace pro službu.</span><span class="sxs-lookup"><span data-stu-id="d4c20-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="d4c20-130">Pokud se rozhodnete nepoužívat sady Visual Studio, můžete použít [nástroj ServiceModel Metadata Utility (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) místo.</span><span class="sxs-lookup"><span data-stu-id="d4c20-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="d4c20-131">Kurz: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="d4c20-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="d4c20-132">Načtěte metadata k vytvoření proxy serveru klienta WCF na službu WCF.</span><span class="sxs-lookup"><span data-stu-id="d4c20-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="d4c20-133">Načítání metadat pomocí sady Visual Studio pro přidání odkazu na službu nebo můžete použít nástroj ServiceModel Metadata Utility.</span><span class="sxs-lookup"><span data-stu-id="d4c20-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="d4c20-134">Zadáte koncový bod, který klient používá pro přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="d4c20-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="d4c20-135">Kurz: Používání klienta</span><span class="sxs-lookup"><span data-stu-id="d4c20-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="d4c20-136">Použijte proxy klienta WCF k volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="d4c20-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="d4c20-137">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d4c20-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="d4c20-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4c20-138">See also</span></span>

- [<span data-ttu-id="d4c20-139">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="d4c20-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="d4c20-140">Příručka k dokumentaci</span><span class="sxs-lookup"><span data-stu-id="d4c20-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="d4c20-141">Co je Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d4c20-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="d4c20-142">Podrobnosti o funkcích WCF</span><span class="sxs-lookup"><span data-stu-id="d4c20-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="d4c20-143">Základní programovací životní cyklus</span><span class="sxs-lookup"><span data-stu-id="d4c20-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="d4c20-144">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="d4c20-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="d4c20-145">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="d4c20-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="d4c20-146">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="d4c20-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="d4c20-147">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="d4c20-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="d4c20-148">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d4c20-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="d4c20-149">Postupy: Stažení dokumentů metadat pomocí Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="d4c20-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="d4c20-150">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d4c20-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d4c20-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d4c20-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d4c20-152">Ukázka Začínáme</span><span class="sxs-lookup"><span data-stu-id="d4c20-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="d4c20-153">Ukázky Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d4c20-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="d4c20-154">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="d4c20-154">Self-Host</span></span>](samples/self-host.md)


