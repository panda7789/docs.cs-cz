---
title: Migrace webové aplikace v ASP.NET do virtuálního počítače Azure
description: Naučte se migrovat webovou aplikaci v ASP.NET z místního prostředí na virtuální počítač Azure.
ms.topic: how-to
ms.date: 06/20/2020
ms.openlocfilehash: 5ef340d020b72bebe46fe598fe68e7d02d0c0363
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174241"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a><span data-ttu-id="04bcc-103">Migrace webové aplikace v ASP.NET na virtuální počítač Azure</span><span class="sxs-lookup"><span data-stu-id="04bcc-103">Migrate an ASP.NET Web application to an Azure Virtual Machine</span></span>

<span data-ttu-id="04bcc-104">Tento dokument poskytuje přehled o tom, jak migrovat webovou aplikaci v ASP.NET z místního prostředí na virtuální počítač Azure.</span><span class="sxs-lookup"><span data-stu-id="04bcc-104">This document provides an overview of how to migrate an ASP.NET web application from on-premises to an Azure Virtual Machine.</span></span>

## <a name="quickstart"></a><span data-ttu-id="04bcc-105">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="04bcc-105">Quickstart</span></span>

<span data-ttu-id="04bcc-106">Zjistěte, jak vytvořit virtuální počítač a jak do něj publikovat aplikaci: [publikování na virtuálním počítači Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)</span><span class="sxs-lookup"><span data-stu-id="04bcc-106">Learn how to create a virtual machine and publish your app to it: [Publish to an Azure VM](https://tutorials.visualstudio.com/aspnet-vm/intro)</span></span>

## <a name="get-started"></a><span data-ttu-id="04bcc-107">Začínáme</span><span class="sxs-lookup"><span data-stu-id="04bcc-107">Get Started</span></span>

<span data-ttu-id="04bcc-108">Tyto kurzy ukazují kroky pro vytvoření (nebo migraci) virtuálního počítače, publikování webové aplikace a další úkoly, které mohou být požadovány pro podporu vaší aplikace v Azure.</span><span class="sxs-lookup"><span data-stu-id="04bcc-108">These tutorials demonstrate the steps to create (or migrate) a virtual machine, publish your web application to it, and other tasks that may be required to support your application in Azure.</span></span>

- <span data-ttu-id="04bcc-109">Vytvořte virtuální počítač pro aplikaci ASP.NET v Azure pomocí jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="04bcc-109">Create a virtual machine for your ASP.NET application in Azure using one of the following options:</span></span>
  - [<span data-ttu-id="04bcc-110">Vytvoření nového virtuálního počítače pro aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="04bcc-110">Create a new virtual machine for ASP.NET Applications</span></span>](https://go.microsoft.com/fwlink/?linkid=863237)
  - [<span data-ttu-id="04bcc-111">Migrace stávajícího místního virtuálního počítače VMWare</span><span class="sxs-lookup"><span data-stu-id="04bcc-111">Migrate an existing on-premises VMWare virtual machine</span></span>](/azure/migrate/tutorial-migrate-vmware)
  - [<span data-ttu-id="04bcc-112">Migrace stávajícího místního virtuálního počítače Hyper-V</span><span class="sxs-lookup"><span data-stu-id="04bcc-112">Migrate an existing on-premises Hyper-V virtual machine</span></span>](/azure/migrate/tutorial-migrate-hyper-v)
- [<span data-ttu-id="04bcc-113">Publikování aplikace pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="04bcc-113">Publish your app using Visual Studio</span></span>](https://go.microsoft.com/fwlink/?linkid=863240)
- [<span data-ttu-id="04bcc-114">Vytvoření zabezpečené virtuální sítě pro vaše virtuální počítače</span><span class="sxs-lookup"><span data-stu-id="04bcc-114">Create a secure virtual network for your VMs</span></span>](/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [<span data-ttu-id="04bcc-115">Vytvoření kanálu CI/CD pro vaši aplikaci</span><span class="sxs-lookup"><span data-stu-id="04bcc-115">Create a CI/CD pipeline for your application</span></span>](/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [<span data-ttu-id="04bcc-116">Přechod na škálu virtuálních počítačů s vysokou dostupností a škálovatelností</span><span class="sxs-lookup"><span data-stu-id="04bcc-116">Move to a VM scale set for high availability and scalability</span></span>](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a><span data-ttu-id="04bcc-117">Co je potřeba vzít v úvahu</span><span class="sxs-lookup"><span data-stu-id="04bcc-117">Considerations</span></span>

### <a name="benefits"></a><span data-ttu-id="04bcc-118">Výhody</span><span class="sxs-lookup"><span data-stu-id="04bcc-118">Benefits</span></span>

<span data-ttu-id="04bcc-119">Virtuální počítače nabízejí nejjednodušší cestu k migraci aplikace z místního prostředí do cloudu.</span><span class="sxs-lookup"><span data-stu-id="04bcc-119">Virtual machines offer the easiest path to migrate an application from on-premises to the cloud.</span></span> <span data-ttu-id="04bcc-120">Umožňují replikovat stejné prostředí, které vaše aplikace používá místně, a zároveň odstranit nutnost udržovat si vlastní datová centra.</span><span class="sxs-lookup"><span data-stu-id="04bcc-120">They enable you to replicate the same environment your application uses on-premises, while removing the need to maintain your own data centers.</span></span> <span data-ttu-id="04bcc-121">Virtual Machine Scale Sets poskytovat vysokou dostupnost a škálovatelnost aplikací běžících v Virtual Machines.</span><span class="sxs-lookup"><span data-stu-id="04bcc-121">Virtual Machine Scale Sets provide high availability and scalability for applications running in Virtual Machines.</span></span>

### <a name="virtual-machine-size"></a><span data-ttu-id="04bcc-122">Velikost virtuálního počítače</span><span class="sxs-lookup"><span data-stu-id="04bcc-122">Virtual Machine Size</span></span>

<span data-ttu-id="04bcc-123">Vyberte velikost virtuálního počítače a typ, který je nejlépe optimalizovaný pro vaše zatížení.</span><span class="sxs-lookup"><span data-stu-id="04bcc-123">Choose the virtual machine size and type that is best optimized for your workload.</span></span> <span data-ttu-id="04bcc-124">Další informace najdete v tématu [velikosti pro virtuální počítače s Windows v Azure](/azure/virtual-machines/windows/sizes).</span><span class="sxs-lookup"><span data-stu-id="04bcc-124">For more information, see [Sizes for Windows virtual machines in Azure](/azure/virtual-machines/windows/sizes).</span></span>

### <a name="maintenance"></a><span data-ttu-id="04bcc-125">Údržba</span><span class="sxs-lookup"><span data-stu-id="04bcc-125">Maintenance</span></span>

<span data-ttu-id="04bcc-126">Stejně jako v místním počítači zodpovídáte za údržbu a aktualizaci<sup>&#42;</sup>virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="04bcc-126">Just like an on-premises machine, you are responsible for maintaining and updating the virtual machine<sup>&#42;</sup>.</span></span> <span data-ttu-id="04bcc-127">Pokud vaše aplikace může běžet v prostředí PaaS (Platform as a Service), jako je například [Azure App Service](/azure/app-service/) nebo v [kontejneru](/azure/app-service/containers/), které tuto potřebu odstraní.</span><span class="sxs-lookup"><span data-stu-id="04bcc-127">If your application can run in a Platform as a Service (PaaS) environment such as [Azure App Service](/azure/app-service/) or in a [container](/azure/app-service/containers/), that will remove this need.</span></span>

<span data-ttu-id="04bcc-128">*<sup>&#42;</sup> [automatické upgrady operačního systému pro Virtual Machine Scale Sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) jsou aktuálně k dispozici jako služba ve verzi Preview.*</span><span class="sxs-lookup"><span data-stu-id="04bcc-128">*<sup>&#42;</sup>[Automatic OS upgrades for virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) is currently available as a Preview service.*</span></span>

### <a name="virtual-networks"></a><span data-ttu-id="04bcc-129">Virtuální sítě</span><span class="sxs-lookup"><span data-stu-id="04bcc-129">Virtual Networks</span></span>

<span data-ttu-id="04bcc-130">Virtuální sítě Azure umožňují:</span><span class="sxs-lookup"><span data-stu-id="04bcc-130">Azure Virtual Networks enable you to:</span></span>

- <span data-ttu-id="04bcc-131">Sestavení hybridní infrastruktury, kterou ovládáte</span><span class="sxs-lookup"><span data-stu-id="04bcc-131">Build a hybrid infrastructure that you control</span></span>
- <span data-ttu-id="04bcc-132">Přineste si vlastní IP adresy a servery DNS</span><span class="sxs-lookup"><span data-stu-id="04bcc-132">Bring your own IP addresses and DNS servers</span></span>
- <span data-ttu-id="04bcc-133">Vytvoření izolovaného a vysoce zabezpečeného prostředí pro vaše aplikace</span><span class="sxs-lookup"><span data-stu-id="04bcc-133">Create an isolated and highly secure environment for your applications</span></span>
- <span data-ttu-id="04bcc-134">Připojte svůj virtuální počítač k místní síti pomocí jedné z několika [možností připojení](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) .</span><span class="sxs-lookup"><span data-stu-id="04bcc-134">Connect your VM to your on-premises network using one of several [connectivity options](/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)</span></span>
- <span data-ttu-id="04bcc-135">Integrujte svůj virtuální počítač do místní sítě pomocí [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span><span class="sxs-lookup"><span data-stu-id="04bcc-135">Integrate your virtual machine into your on-premises network using [ExpressRoute](https://azure.microsoft.com/services/expressroute/)</span></span>

<span data-ttu-id="04bcc-136">Informace o tom, jak začít, najdete v [dokumentaci k Virtual Network](/azure/virtual-network/)</span><span class="sxs-lookup"><span data-stu-id="04bcc-136">To get started, see the [Virtual Network documentation](/azure/virtual-network/)</span></span>

### <a name="active-directory"></a><span data-ttu-id="04bcc-137">Active Directory</span><span class="sxs-lookup"><span data-stu-id="04bcc-137">Active Directory</span></span>
<span data-ttu-id="04bcc-138">Mnoho aplikací používá ke správě ověřování a správy identit službu Active Directory.</span><span class="sxs-lookup"><span data-stu-id="04bcc-138">Many applications use Active Directory for authentication and identity management.</span></span>

- <span data-ttu-id="04bcc-139">Azure AD Connect umožňuje integrovat místní adresáře s Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="04bcc-139">Azure AD Connect enables you to integrate your on-premises directories with Azure Active Directory.</span></span> <span data-ttu-id="04bcc-140">Informace o tom, jak začít, najdete v tématu [Integrace místních adresářů s Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="04bcc-140">To get started, see [Integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>
- <span data-ttu-id="04bcc-141">[ExpressRoute](https://azure.microsoft.com/services/expressroute/) také umožňuje vaší aplikaci přistupovat k místní službě Active Directory.</span><span class="sxs-lookup"><span data-stu-id="04bcc-141">Alternatively, [ExpressRoute](https://azure.microsoft.com/services/expressroute/) enables your application to access your on-premises Active Directory.</span></span>

### <a name="sql-databases"></a><span data-ttu-id="04bcc-142">Databáze SQL</span><span class="sxs-lookup"><span data-stu-id="04bcc-142">SQL Databases</span></span>

<span data-ttu-id="04bcc-143">Pokud vaše aplikace používá místní databázi, aplikace ve výchozím nastavení nebude schopná mluvit na ni.</span><span class="sxs-lookup"><span data-stu-id="04bcc-143">If your application is using an on-premises database, your app will not be able to talk to it by default.</span></span> <span data-ttu-id="04bcc-144">Máte tyto možnosti:</span><span class="sxs-lookup"><span data-stu-id="04bcc-144">You can either:</span></span>

- <span data-ttu-id="04bcc-145">Nakonfigurujte hybridní síť, která umožňuje vaší aplikaci přístup k vaší databázi běžící místně.</span><span class="sxs-lookup"><span data-stu-id="04bcc-145">Configure a hybrid network that enables your application to access your database running on-premises.</span></span>
- <span data-ttu-id="04bcc-146">Migrujte svou databázi do Azure.</span><span class="sxs-lookup"><span data-stu-id="04bcc-146">Migrate your database to the Azure.</span></span> <span data-ttu-id="04bcc-147">Další informace najdete v tématu [migrace databáze SQL Server do Azure](sql.md).</span><span class="sxs-lookup"><span data-stu-id="04bcc-147">For more information, see [Migrate your SQL Server database to Azure](sql.md).</span></span>

### <a name="high-availability-and-scalability"></a><span data-ttu-id="04bcc-148">Vysoká dostupnost a škálovatelnost</span><span class="sxs-lookup"><span data-stu-id="04bcc-148">High Availability and Scalability</span></span>

#### <a name="virtual-machine-scale-sets"></a><span data-ttu-id="04bcc-149">Virtual Machine Scale Sets</span><span class="sxs-lookup"><span data-stu-id="04bcc-149">Virtual Machine Scale Sets</span></span>
<span data-ttu-id="04bcc-150">Chcete mít jistotu, že je vaše aplikace vysoce dostupná a může škálovat, migrovat image virtuálního počítače do sady škálování virtuálních počítačů Azure, aby se zlepšila dostupnost a škálovatelnost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="04bcc-150">You want to make sure that your application is highly available and can scale, migrate your VM image to an Azure Virtual Machine Scale Set to improve the availability and scalability of your application.</span></span> <span data-ttu-id="04bcc-151">VM Scale Sets poskytují možnost použít existující virtuální počítač, který jste už nakonfigurovali, nebo vytvořit kanál sestavení pro sestavení image s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="04bcc-151">VM Scale Sets provide the ability to use an existing VM you've already configured or set up a build pipeline to build an image with your application.</span></span>

<span data-ttu-id="04bcc-152">Informace o tom, jak začít, najdete v tématu [nasazení aplikace ve službě Virtual Machine Scale Sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span><span class="sxs-lookup"><span data-stu-id="04bcc-152">To get started, see [Deploy your application on virtual machine scale sets](/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).</span></span>

#### <a name="centralized-logging"></a><span data-ttu-id="04bcc-153">Centralizované protokolování</span><span class="sxs-lookup"><span data-stu-id="04bcc-153">Centralized Logging</span></span>
<span data-ttu-id="04bcc-154">Při spuštění aplikace napříč několika instancemi zvažte ukládání protokolů do centralizovaného umístění, jako je například [Azure Storage](/azure/storage/).</span><span class="sxs-lookup"><span data-stu-id="04bcc-154">When running your application across multiple instances, consider storing your logs in a centralized location such as [Azure Storage](/azure/storage/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="04bcc-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="04bcc-155">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04bcc-156">Migrace databáze SQL Serveru do Azure</span><span class="sxs-lookup"><span data-stu-id="04bcc-156">Migrate a SQL Server database to Azure</span></span>](sql.md)
