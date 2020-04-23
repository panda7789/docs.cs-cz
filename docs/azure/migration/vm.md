---
title: Migrace ASP.NET webové aplikace do virtuálního počítače Azure
description: Zjistěte, jak migrovat ASP.NET webovou aplikaci z místního do virtuálního počítače Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072121"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="01abd-103">Migrace webové aplikace ASP.NET do virtuálního počítače Azure</span><span class="sxs-lookup"><span data-stu-id="01abd-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="01abd-104">Tento dokument poskytuje přehled o tom, jak migrovat ASP.NET webové aplikace z místního do virtuálního počítače Azure.</span><span class="sxs-lookup"><span data-stu-id="01abd-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="01abd-105">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="01abd-105">Quickstart</span></span>

<span data-ttu-id="01abd-106">Přečtěte si, jak vytvořit virtuální počítač a publikovat do něj aplikaci: [Publikování na virtuálním počítači Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="01abd-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="01abd-107">Začínáme</span><span class="sxs-lookup"><span data-stu-id="01abd-107">Get Started</span></span>

<span data-ttu-id="01abd-108">Tyto kurzy ukazují kroky k vytvoření (nebo migraci) virtuálního počítače, publikování webové aplikace do něj a další úkoly, které mohou být nutné pro podporu vaší aplikace v Azure.</span><span class="sxs-lookup"><span data-stu-id="01abd-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="01abd-109">Vytvořte virtuální počítač pro vaši ASP.NET aplikaci v Azure pomocí jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="01abd-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="01abd-110">Vytvoření nového virtuálního počítače pro ASP.NET aplikace</span><span class="sxs-lookup"><span data-stu-id="01abd-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="01abd-111">Migrace existujícího místního virtuálního počítače VMWare</span><span class="sxs-lookup"><span data-stu-id="01abd-111">Migrate an existing on-premises VMWare virtual machine</span></span>](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="01abd-112">Migrace existujícího místního virtuálního počítače Hyper-V</span><span class="sxs-lookup"><span data-stu-id="01abd-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="01abd-113">Publikování aplikace pomocí Visual Studia</span><span class="sxs-lookup"><span data-stu-id="01abd-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="01abd-114">Vytvoření zabezpečené virtuální sítě pro virtuální počítače</span><span class="sxs-lookup"><span data-stu-id="01abd-114">Create a secure virtual network for your VMs</span></span>](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="01abd-115">Vytvoření kanálu CI/CD pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="01abd-115">Create a CI/CD pipeline for your application</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="01abd-116">Přechod na škálovací sadu virtuálních aplikací pro vysokou dostupnost a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="01abd-116">Move to a VM scale set for high availability and scalability</span></span>](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="01abd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01abd-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="01abd-118">Výhody</span><span class="sxs-lookup"><span data-stu-id="01abd-118">Benefits</span></span>

<span data-ttu-id="01abd-119">Virtuální počítače nabízejí nejjednodušší cestu k migraci aplikace z místního do cloudu.</span><span class="sxs-lookup"><span data-stu-id="01abd-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="01abd-120">Umožňují replikovat stejné prostředí, které vaše aplikace používá místně, a zároveň odstraňují potřebu udržovat vlastní datová centra.</span><span class="sxs-lookup"><span data-stu-id="01abd-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="01abd-121">Škálovací sady virtuálních počítačů poskytují vysokou dostupnost a škálovatelnost pro aplikace spuštěné ve virtuálních počítačích.</span><span class="sxs-lookup"><span data-stu-id="01abd-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="01abd-122">Velikost virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="01abd-122">Virtual Machine Size</span></span>

<span data-ttu-id="01abd-123">Zvolte velikost a typ virtuálního počítače, který je nejlépe optimalizovaný pro vaši úlohu.</span><span class="sxs-lookup"><span data-stu-id="01abd-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="01abd-124">Další informace najdete v [tématu Velikosti pro virtuální počítače s Windows v Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="01abd-124">For more information, see [Sizes for Windows virtual machines in Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="01abd-125">Údržba</span><span class="sxs-lookup"><span data-stu-id="01abd-125">Maintenance</span></span>

<span data-ttu-id="01abd-126">Stejně jako místní počítač, jste zodpovědní za údržbu a aktualizaci<sup> virtuálního </sup>počítače&#42;.</span><span class="sxs-lookup"><span data-stu-id="01abd-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="01abd-127">Pokud vaše aplikace může běžet v prostředí platformy jako služba (PaaS), jako je [například Azure App Service](https://docs.microsoft.com/azure/app-service/) nebo v [kontejneru](https://docs.microsoft.com/azure/app-service/containers/), která odebere tuto potřebu.</span><span class="sxs-lookup"><span data-stu-id="01abd-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](https://docs.microsoft.com/azure/app-service/) or in a [container](https://docs.microsoft.com/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="01abd-128">*<sup>&#42;</sup> [automatické upgrady operačního systému pro škálovací sady virtuálních strojů](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) je v současné době k dispozici jako služba Preview.*</span><span class="sxs-lookup"><span data-stu-id="01abd-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="01abd-129">Virtuální sítě</span><span class="sxs-lookup"><span data-stu-id="01abd-129">Virtual Networks</span></span>

<span data-ttu-id="01abd-130">Virtuální sítě Azure umožňují:</span><span class="sxs-lookup"><span data-stu-id="01abd-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="01abd-131">Vytvoření hybridní infrastruktury, kterou ovládáte</span><span class="sxs-lookup"><span data-stu-id="01abd-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="01abd-132">Přineste si vlastní IP adresy a DNS servery</span><span class="sxs-lookup"><span data-stu-id="01abd-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="01abd-133">Vytvoření izolovaného a vysoce zabezpečeného prostředí pro vaše aplikace</span><span class="sxs-lookup"><span data-stu-id="01abd-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="01abd-134">Připojení virtuálního počítače k místní síti pomocí jedné z několika [možností připojení](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span><span class="sxs-lookup"><span data-stu-id="01abd-134">Connect your VM to your on-premises network using one of several [connectivity options](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="01abd-135">Integrace virtuálního počítače do místní sítě pomocí [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span><span class="sxs-lookup"><span data-stu-id="01abd-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="01abd-136">Chcete-li začít, podívejte se na [dokumentaci k virtuální síti](https://docs.microsoft.com/azure/virtual-network/)</span><span class="sxs-lookup"><span data-stu-id="01abd-136">To get started, see the [Virtual Network documentation](https://docs.microsoft.com/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="01abd-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="01abd-137">Active Directory</span></span>
<span data-ttu-id="01abd-138">Mnoho aplikací používá službu Active Directory pro ověřování a správu identit.</span><span class="sxs-lookup"><span data-stu-id="01abd-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="01abd-139">Azure AD Connect umožňuje integrovat místní adresáře s Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="01abd-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="01abd-140">Informace o tom, jak začít, najdete [v tématu Integrace místních adresářů pomocí služby Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="01abd-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="01abd-141">Alternativně [ExpressRoute](https://azure.microsoft.com/services/expressroute/) umožňuje vaší aplikaci přístup k místní službě Active Directory.</span><span class="sxs-lookup"><span data-stu-id="01abd-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="01abd-142">Databáze SQL</span><span class="sxs-lookup"><span data-stu-id="01abd-142">SQL Databases</span></span>

<span data-ttu-id="01abd-143">Pokud vaše aplikace používá místní databázi, vaše aplikace nebude moct mluvit s ní ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="01abd-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="01abd-144">Máte tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="01abd-144">You can either:</span></span>

- <span data-ttu-id="01abd-145">Nakonfigurujte hybridní síť, která umožňuje vaší aplikaci přístup k databázi spuštěné místně.</span><span class="sxs-lookup"><span data-stu-id="01abd-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="01abd-146">Migrujte databázi do Azure.</span><span class="sxs-lookup"><span data-stu-id="01abd-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="01abd-147">Další informace najdete [v tématu Migrace databáze serveru SQL Server do Azure](sql.md).</span><span class="sxs-lookup"><span data-stu-id="01abd-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="01abd-148">Vysoká dostupnost a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="01abd-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="01abd-149">Virtual Machine Scale Sets</span><span class="sxs-lookup"><span data-stu-id="01abd-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="01abd-150">Chcete se ujistit, že vaše aplikace je vysoce dostupná a může škálovat, migrovat image virtuálního počítače do škálovací sady virtuálních strojů Azure, abyste zlepšili dostupnost a škálovatelnost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="01abd-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="01abd-151">Škálovací sady virtuálních zařízení poskytují možnost používat existující virtuální počítač, který jste už nakonfigurovali, nebo nastavit kanál sestavení k vytvoření image s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="01abd-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="01abd-152">Další informace najdete v [tématu Nasazení aplikace ve škálovacích sadách virtuálních strojů](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="01abd-152">To get started, see [Deploy your application on virtual machine scale sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="01abd-153">Centralizované protokolování</span><span class="sxs-lookup"><span data-stu-id="01abd-153">Centralized Logging</span></span>
<span data-ttu-id="01abd-154">Při spuštění aplikace ve více instancích zvažte ukládání protokolů v centralizovaném umístění, jako je [Azure Storage](https://docs.microsoft.com/azure/storage/).</span><span class="sxs-lookup"><span data-stu-id="01abd-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](https://docs.microsoft.com/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="01abd-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="01abd-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="01abd-156">Migrace databáze SQL Serveru do Azure</span><span class="sxs-lookup"><span data-stu-id="01abd-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
