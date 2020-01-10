---
title: Nasazení .NET Framework a aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716467"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="5d796-102">Nasazení .NET Framework a aplikací</span><span class="sxs-lookup"><span data-stu-id="5d796-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="5d796-103">Tento článek vám pomůže začít s nasazením .NET Framework s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="5d796-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="5d796-104">Většina informací je určená vývojářům, výrobcům OEM a podnikovým správcům.</span><span class="sxs-lookup"><span data-stu-id="5d796-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="5d796-105">Uživatelé, kteří chtějí instalovat .NET Framework na svých počítačích, by si měli přečíst [instalaci .NET Framework](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d796-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="5d796-106">Prostředky nasazení klíčů</span><span class="sxs-lookup"><span data-stu-id="5d796-106">Key Deployment Resources</span></span>

<span data-ttu-id="5d796-107">Pro konkrétní informace o nasazení a údržbě .NET Framework použijte následující odkazy na další témata MSDN.</span><span class="sxs-lookup"><span data-stu-id="5d796-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="5d796-108">**Nastavení a nasazení**</span><span class="sxs-lookup"><span data-stu-id="5d796-108">**Setup and deployment**</span></span>

- <span data-ttu-id="5d796-109">Obecné informace o instalačním programu a nasazení:</span><span class="sxs-lookup"><span data-stu-id="5d796-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="5d796-110">Možnosti instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="5d796-110">Installer options:</span></span>

    - [<span data-ttu-id="5d796-111">Webová instalační služba</span><span class="sxs-lookup"><span data-stu-id="5d796-111">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="5d796-112">Offline instalační program</span><span class="sxs-lookup"><span data-stu-id="5d796-112">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="5d796-113">Režimy instalace:</span><span class="sxs-lookup"><span data-stu-id="5d796-113">Installation modes:</span></span>

    - [<span data-ttu-id="5d796-114">Bezobslužná instalace</span><span class="sxs-lookup"><span data-stu-id="5d796-114">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="5d796-115">Zobrazení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d796-115">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="5d796-116">Snížení restartu systému během instalací .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="5d796-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="5d796-117">Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d796-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="5d796-118">Nasazení .NET Framework pomocí klientské aplikace (pro vývojáře):</span><span class="sxs-lookup"><span data-stu-id="5d796-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="5d796-119">[Používání programu InstallShield](deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení</span><span class="sxs-lookup"><span data-stu-id="5d796-119">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="5d796-120">Použití aplikace Visual Studio ClickOnce</span><span class="sxs-lookup"><span data-stu-id="5d796-120">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="5d796-121">Vytvoření instalačního balíčku WiX</span><span class="sxs-lookup"><span data-stu-id="5d796-121">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="5d796-122">Použití vlastního instalačního programu</span><span class="sxs-lookup"><span data-stu-id="5d796-122">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="5d796-123">[Další informace](deployment-guide-for-developers.md) pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="5d796-123">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="5d796-124">Nasazení .NET Framework (pro výrobce OEM a správce):</span><span class="sxs-lookup"><span data-stu-id="5d796-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="5d796-125">Sada Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="5d796-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="5d796-126">Příručka pro správce</span><span class="sxs-lookup"><span data-stu-id="5d796-126">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="5d796-127">**Údržba**</span><span class="sxs-lookup"><span data-stu-id="5d796-127">**Servicing**</span></span>

- <span data-ttu-id="5d796-128">Obecné informace najdete na [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="5d796-128">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="5d796-129">Zjišťují se verze</span><span class="sxs-lookup"><span data-stu-id="5d796-129">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="5d796-130">Zjišťování aktualizací Service Pack a aktualizací</span><span class="sxs-lookup"><span data-stu-id="5d796-130">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="5d796-131">Funkce, které zjednodušují nasazení</span><span class="sxs-lookup"><span data-stu-id="5d796-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="5d796-132">.NET Framework poskytuje řadu základních funkcí, které usnadňují nasazení aplikací:</span><span class="sxs-lookup"><span data-stu-id="5d796-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="5d796-133">Aplikace bez dopadu.</span><span class="sxs-lookup"><span data-stu-id="5d796-133">No-impact applications.</span></span>

     <span data-ttu-id="5d796-134">Tato funkce poskytuje izolaci aplikace a eliminuje konflikty knihoven DLL.</span><span class="sxs-lookup"><span data-stu-id="5d796-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="5d796-135">Ve výchozím nastavení komponenty neovlivňují jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d796-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="5d796-136">Ve výchozím nastavení soukromé součásti.</span><span class="sxs-lookup"><span data-stu-id="5d796-136">Private components by default.</span></span>

     <span data-ttu-id="5d796-137">Ve výchozím nastavení jsou komponenty nasazeny do adresáře aplikace a jsou viditelné pouze pro aplikaci, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="5d796-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="5d796-138">Řízená sdílení kódu.</span><span class="sxs-lookup"><span data-stu-id="5d796-138">Controlled code sharing.</span></span>

     <span data-ttu-id="5d796-139">Sdílení kódu vyžaduje explicitní zpřístupnění kódu pro sdílení namísto výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="5d796-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="5d796-140">Souběžná Správa verzí.</span><span class="sxs-lookup"><span data-stu-id="5d796-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="5d796-141">Několik verzí komponenty nebo aplikace může existovat současně, můžete zvolit, které verze se mají použít, a modul CLR (Common Language Runtime) vynutil zásady správy verzí.</span><span class="sxs-lookup"><span data-stu-id="5d796-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="5d796-142">Nasazení a replikace XCOPY.</span><span class="sxs-lookup"><span data-stu-id="5d796-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="5d796-143">Samostatné a samostatně uzavřené komponenty a aplikace lze nasadit bez položek registru nebo závislostí.</span><span class="sxs-lookup"><span data-stu-id="5d796-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="5d796-144">Průběžné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5d796-144">On-the-fly updates.</span></span>

     <span data-ttu-id="5d796-145">Správci můžou použít hostitele, jako je ASP.NET, k aktualizaci knihoven DLL programu, i na vzdálených počítačích.</span><span class="sxs-lookup"><span data-stu-id="5d796-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="5d796-146">Integrace s Instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5d796-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="5d796-147">Inzerce, publikování, opravy a instalace na vyžádání jsou dostupné při nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d796-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="5d796-148">Podnikové nasazení.</span><span class="sxs-lookup"><span data-stu-id="5d796-148">Enterprise deployment.</span></span>

     <span data-ttu-id="5d796-149">Tato funkce poskytuje jednoduchou distribuci softwaru, včetně používání služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5d796-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="5d796-150">Stahování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5d796-150">Downloading and caching.</span></span>

     <span data-ttu-id="5d796-151">Přírůstkové stahování udržuje menší soubory ke stažení a součásti lze izolovat pouze pro použití v aplikaci pro nasazení s nízkým dopadem.</span><span class="sxs-lookup"><span data-stu-id="5d796-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="5d796-152">Částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="5d796-152">Partially trusted code.</span></span>

     <span data-ttu-id="5d796-153">Identita je založena na kódu namísto uživatele a nezobrazují se dialogová okna certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5d796-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="5d796-154">Balení a distribuce .NET Frameworkch aplikací</span><span class="sxs-lookup"><span data-stu-id="5d796-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="5d796-155">Některé informace o balení a nasazení pro .NET Framework jsou popsány v dalších částech dokumentace.</span><span class="sxs-lookup"><span data-stu-id="5d796-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="5d796-156">Tyto části poskytují informace o jednotkách, které jsou označovány jako [sestavení](../../standard/assembly/index.md), které nevyžadují žádné položky registru, [sestavení se silným názvem](../../standard/assembly/strong-named.md), které zajišťují jedinečnost názvu a brání falšování názvů a [správu verzí sestavení](../../standard/assembly/versioning.md), které řeší mnohé problémy spojené s konflikty knihoven DLL.</span><span class="sxs-lookup"><span data-stu-id="5d796-156">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="5d796-157">Následující části obsahují informace o balení a distribuci .NET Frameworkch aplikací.</span><span class="sxs-lookup"><span data-stu-id="5d796-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="5d796-158">Balení</span><span class="sxs-lookup"><span data-stu-id="5d796-158">Packaging</span></span>

<span data-ttu-id="5d796-159">.NET Framework poskytuje následující možnosti pro vytváření balíčků aplikací:</span><span class="sxs-lookup"><span data-stu-id="5d796-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="5d796-160">Jako jedno sestavení nebo jako kolekce sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d796-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="5d796-161">Pomocí této možnosti jednoduše použijete soubory. dll nebo. exe, jak byly sestaveny.</span><span class="sxs-lookup"><span data-stu-id="5d796-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="5d796-162">Jako soubory CAB.</span><span class="sxs-lookup"><span data-stu-id="5d796-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="5d796-163">Pomocí této možnosti zkomprimujete soubory do souborů. cab, abyste mohli distribuovat nebo stahovat méně času náročného.</span><span class="sxs-lookup"><span data-stu-id="5d796-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="5d796-164">Jako balíček Instalační služba systému Windows nebo v jiných formátech instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="5d796-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="5d796-165">Pomocí této možnosti vytvoříte soubory. msi pro použití s Instalační služba systému Windows nebo zabalíte aplikaci pro použití s nějakým jiným instalačním programem.</span><span class="sxs-lookup"><span data-stu-id="5d796-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="5d796-166">Distribuce</span><span class="sxs-lookup"><span data-stu-id="5d796-166">Distribution</span></span>

<span data-ttu-id="5d796-167">.NET Framework poskytuje následující možnosti pro distribuci aplikací:</span><span class="sxs-lookup"><span data-stu-id="5d796-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="5d796-168">Použijte XCOPY nebo FTP.</span><span class="sxs-lookup"><span data-stu-id="5d796-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="5d796-169">Vzhledem k tomu, že aplikace modulu CLR (Common Language Runtime) samy popisují a nevyžadují žádné položky registru, můžete pomocí příkazu XCOPY nebo FTP jednoduše zkopírovat aplikaci do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="5d796-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="5d796-170">Aplikaci lze následně spustit z tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="5d796-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="5d796-171">Použijte stahování kódu.</span><span class="sxs-lookup"><span data-stu-id="5d796-171">Use code download.</span></span>

     <span data-ttu-id="5d796-172">Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikového intranetu, můžete jednoduše stáhnout kód do počítače a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d796-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="5d796-173">Použijte instalační program, například Instalační služba systému Windows 2,0.</span><span class="sxs-lookup"><span data-stu-id="5d796-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="5d796-174">Instalační služba systému Windows 2,0 může instalovat, opravovat nebo odebírat .NET Framework sestavení v globální mezipaměti sestavení (GAC) a v privátních adresářích.</span><span class="sxs-lookup"><span data-stu-id="5d796-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="5d796-175">Umístění instalace</span><span class="sxs-lookup"><span data-stu-id="5d796-175">Installation Location</span></span>

<span data-ttu-id="5d796-176">Chcete-li určit, kam se mají nasadit sestavení vaší aplikace, aby je bylo možné najít modulem runtime, přečtěte si téma [jak modul runtime vyhledává sestavení](how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5d796-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="5d796-177">Požadavky na zabezpečení mohou také ovlivnit způsob nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d796-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="5d796-178">Oprávnění zabezpečení se udělují spravovanému kódu podle toho, kde se nachází kód.</span><span class="sxs-lookup"><span data-stu-id="5d796-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="5d796-179">Nasazení aplikace nebo komponenty do umístění, kde obdrží malý vztah důvěryhodnosti, jako je například Internet, omezuje, co může aplikace nebo komponenta dělat.</span><span class="sxs-lookup"><span data-stu-id="5d796-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="5d796-180">Další informace o možnostech nasazení a zabezpečení najdete v tématu [Základy zabezpečení přístupu kódu](../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5d796-180">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="5d796-181">Související témata</span><span class="sxs-lookup"><span data-stu-id="5d796-181">Related Topics</span></span>

|<span data-ttu-id="5d796-182">Název</span><span class="sxs-lookup"><span data-stu-id="5d796-182">Title</span></span>|<span data-ttu-id="5d796-183">Popis</span><span class="sxs-lookup"><span data-stu-id="5d796-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="5d796-184">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="5d796-184">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="5d796-185">Popisuje, jak modul CLR (Common Language Runtime) určuje, které sestavení se má použít ke splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="5d796-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="5d796-186">Doporučené postupy pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="5d796-186">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="5d796-187">Popisuje způsoby, jak zabránit problémům s typem identity, který může vést k <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a dalším chybám.</span><span class="sxs-lookup"><span data-stu-id="5d796-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="5d796-188">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="5d796-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="5d796-189">Popisuje správce restartování, který znemožňuje restartování, kdykoli je to možné, a vysvětluje, jak můžou aplikace, které instalují .NET Framework, využít.</span><span class="sxs-lookup"><span data-stu-id="5d796-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="5d796-190">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="5d796-190">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="5d796-191">Vysvětluje, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti pomocí služby Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5d796-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="5d796-192">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="5d796-192">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="5d796-193">Vysvětluje, jak můžou vývojáři instalovat .NET Framework na počítačích uživatelů s jejich aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="5d796-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="5d796-194">Nasazení aplikací, služeb a komponent</span><span class="sxs-lookup"><span data-stu-id="5d796-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="5d796-195">Popisuje možnosti nasazení v aplikaci Visual Studio, včetně pokynů pro publikování aplikace pomocí technologie ClickOnce a Instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5d796-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="5d796-196">Publikování aplikací ClickOnce</span><span class="sxs-lookup"><span data-stu-id="5d796-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="5d796-197">Popisuje, jak zabalit aplikaci model Windows Forms a nasadit ji pomocí technologie ClickOnce na klientské počítače v síti.</span><span class="sxs-lookup"><span data-stu-id="5d796-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="5d796-198">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="5d796-198">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="5d796-199">Popisuje model hvězdicové a paprsky, které .NET Framework používá k zabalení a nasazení prostředků. Popisuje zásady vytváření názvů prostředků, záložní proces a alternativy balení.</span><span class="sxs-lookup"><span data-stu-id="5d796-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="5d796-200">Nasazení aplikace spolupráce</span><span class="sxs-lookup"><span data-stu-id="5d796-200">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="5d796-201">Vysvětluje, jak dodávat a instalovat aplikace spolupráce, které obvykle zahrnují .NET Framework sestavení klienta, jedno nebo více definičních sestavení představujících odlišné knihovny typů modelu COM a jednu nebo více registrovaných komponent modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d796-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="5d796-202">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="5d796-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="5d796-203">V této části najdete popis postupu při tichém spuštění a sledování procesu instalace .NET Framework při zobrazení vlastního zobrazení průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="5d796-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5d796-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d796-204">See also</span></span>

- [<span data-ttu-id="5d796-205">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="5d796-205">Development Guide</span></span>](../development-guide.md)
