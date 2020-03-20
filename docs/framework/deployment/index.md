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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716467"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="efedf-102">Nasazení .NET Framework a aplikací</span><span class="sxs-lookup"><span data-stu-id="efedf-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="efedf-103">Tento článek vám pomůže začít nasazovat rozhraní .NET Framework s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="efedf-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="efedf-104">Většina informací je určena vývojářům, oemům oem a správcům rozlehlé sítě.</span><span class="sxs-lookup"><span data-stu-id="efedf-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="efedf-105">Uživatelé, kteří chtějí nainstalovat rozhraní .NET Framework do svých počítačů, by si měli [přečíst článek Instalace rozhraní .NET Framework](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="efedf-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="efedf-106">Klíčové prostředky pro nasazení</span><span class="sxs-lookup"><span data-stu-id="efedf-106">Key Deployment Resources</span></span>

<span data-ttu-id="efedf-107">Konkrétní informace o nasazení a údržbě rozhraní .NET Framework použijte následující odkazy na jiná témata služby MSDN.</span><span class="sxs-lookup"><span data-stu-id="efedf-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="efedf-108">**Nastavení a nasazení**</span><span class="sxs-lookup"><span data-stu-id="efedf-108">**Setup and deployment**</span></span>

- <span data-ttu-id="efedf-109">Obecné informace o instalačním programu a nasazení:</span><span class="sxs-lookup"><span data-stu-id="efedf-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="efedf-110">Možnosti instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="efedf-110">Installer options:</span></span>

    - [<span data-ttu-id="efedf-111">Webový instalační program</span><span class="sxs-lookup"><span data-stu-id="efedf-111">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="efedf-112">Offline instalační program</span><span class="sxs-lookup"><span data-stu-id="efedf-112">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="efedf-113">Instalační režimy:</span><span class="sxs-lookup"><span data-stu-id="efedf-113">Installation modes:</span></span>

    - [<span data-ttu-id="efedf-114">Bezobslužná instalace</span><span class="sxs-lookup"><span data-stu-id="efedf-114">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="efedf-115">Zobrazení nového ui</span><span class="sxs-lookup"><span data-stu-id="efedf-115">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="efedf-116">Snížení restartování systému během instalace rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="efedf-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="efedf-117">Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="efedf-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="efedf-118">Nasazení rozhraní .NET Framework s klientskou aplikací (pro vývojáře):</span><span class="sxs-lookup"><span data-stu-id="efedf-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="efedf-119">[Použití programu InstallShield](deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení</span><span class="sxs-lookup"><span data-stu-id="efedf-119">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="efedf-120">Použití aplikace Visual Studio ClickOnce</span><span class="sxs-lookup"><span data-stu-id="efedf-120">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="efedf-121">Vytvoření instalačního balíčku WiX</span><span class="sxs-lookup"><span data-stu-id="efedf-121">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="efedf-122">Použití vlastního instalačního programu</span><span class="sxs-lookup"><span data-stu-id="efedf-122">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="efedf-123">[Další informace](deployment-guide-for-developers.md) pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="efedf-123">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="efedf-124">Nasazení rozhraní .NET Framework (pro oemy a správce):</span><span class="sxs-lookup"><span data-stu-id="efedf-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="efedf-125">Sada Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="efedf-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="efedf-126">Průvodce správcem</span><span class="sxs-lookup"><span data-stu-id="efedf-126">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="efedf-127">**Údržba**</span><span class="sxs-lookup"><span data-stu-id="efedf-127">**Servicing**</span></span>

- <span data-ttu-id="efedf-128">Obecné informace naleznete na [blogu rozhraní .NET Framework](https://devblogs.microsoft.com/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="efedf-128">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="efedf-129">Zjišťování verzí</span><span class="sxs-lookup"><span data-stu-id="efedf-129">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="efedf-130">Zjišťování aktualizací Service Pack a aktualizací</span><span class="sxs-lookup"><span data-stu-id="efedf-130">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="efedf-131">Funkce, které zjednodušují nasazení</span><span class="sxs-lookup"><span data-stu-id="efedf-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="efedf-132">Rozhraní .NET Framework poskytuje řadu základních funkcí, které usnadňují nasazení aplikací:</span><span class="sxs-lookup"><span data-stu-id="efedf-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="efedf-133">Aplikace bez dopadu.</span><span class="sxs-lookup"><span data-stu-id="efedf-133">No-impact applications.</span></span>

     <span data-ttu-id="efedf-134">Tato funkce poskytuje izolaci aplikací a eliminuje konflikty dll.</span><span class="sxs-lookup"><span data-stu-id="efedf-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="efedf-135">Ve výchozím nastavení součásti nemají vliv na jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="efedf-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="efedf-136">Soukromé součásti ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="efedf-136">Private components by default.</span></span>

     <span data-ttu-id="efedf-137">Ve výchozím nastavení jsou součásti nasazeny do adresáře aplikace a jsou viditelné pouze pro obsahující aplikaci.</span><span class="sxs-lookup"><span data-stu-id="efedf-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="efedf-138">Řízené sdílení kódu.</span><span class="sxs-lookup"><span data-stu-id="efedf-138">Controlled code sharing.</span></span>

     <span data-ttu-id="efedf-139">Sdílení kódu vyžaduje, abyste explicitně zpřístupnit kód pro sdílení namísto výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="efedf-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="efedf-140">Souběžná správa verzí.</span><span class="sxs-lookup"><span data-stu-id="efedf-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="efedf-141">Více verzí komponenty nebo aplikace může existovat vedle sebe, můžete si vybrat, které verze se mají použít, a běžný jazyk runtime vynucuje zásady správy verzí.</span><span class="sxs-lookup"><span data-stu-id="efedf-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="efedf-142">Nasazení a replikace XCOPY.</span><span class="sxs-lookup"><span data-stu-id="efedf-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="efedf-143">Samostatné a samostatné součásti a aplikace lze nasadit bez položek registru nebo závislostí.</span><span class="sxs-lookup"><span data-stu-id="efedf-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="efedf-144">Průběžně aktuální informace.</span><span class="sxs-lookup"><span data-stu-id="efedf-144">On-the-fly updates.</span></span>

     <span data-ttu-id="efedf-145">Správci mohou k aktualizaci knihoven DLL programů, například ASP.NET, dokonce i ve vzdálených počítačích.</span><span class="sxs-lookup"><span data-stu-id="efedf-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="efedf-146">Integrace s Instalační službou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="efedf-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="efedf-147">Reklama, publikování, opravy a instalace na vyžádání jsou k dispozici při nasazování aplikace.</span><span class="sxs-lookup"><span data-stu-id="efedf-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="efedf-148">Podnikové nasazení.</span><span class="sxs-lookup"><span data-stu-id="efedf-148">Enterprise deployment.</span></span>

     <span data-ttu-id="efedf-149">Tato funkce poskytuje snadnou distribuci softwaru, včetně použití služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="efedf-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="efedf-150">Stahování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="efedf-150">Downloading and caching.</span></span>

     <span data-ttu-id="efedf-151">Přírůstkové stahování udržuje stahování menší a součásti mohou být izolovány pouze pro použití aplikací pro nasazení s nízkým dopadem.</span><span class="sxs-lookup"><span data-stu-id="efedf-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="efedf-152">Částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="efedf-152">Partially trusted code.</span></span>

     <span data-ttu-id="efedf-153">Identita je založena na kódu namísto uživatele a nezobrazí se žádná dialogová okna certifikátu.</span><span class="sxs-lookup"><span data-stu-id="efedf-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="efedf-154">Balení a distribuce aplikací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="efedf-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="efedf-155">Některé informace o balení a nasazení pro rozhraní .NET Framework jsou popsány v jiných částech dokumentace.</span><span class="sxs-lookup"><span data-stu-id="efedf-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="efedf-156">Tyto oddíly obsahují informace o jednotkách s vlastním popisem [nazývaných sestavení](../../standard/assembly/index.md), které nevyžadují žádné položky registru, [sestavení se silným názvem](../../standard/assembly/strong-named.md), které zajišťují jedinečnost názvů a zabraňují falšování názvů, a [správu verzí sestavení](../../standard/assembly/versioning.md), které řeší mnoho problémů spojených s konflikty dll.</span><span class="sxs-lookup"><span data-stu-id="efedf-156">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="efedf-157">Následující části obsahují informace o balení a distribuci aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="efedf-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="efedf-158">Balení</span><span class="sxs-lookup"><span data-stu-id="efedf-158">Packaging</span></span>

<span data-ttu-id="efedf-159">Rozhraní .NET Framework poskytuje následující možnosti pro balení aplikací:</span><span class="sxs-lookup"><span data-stu-id="efedf-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="efedf-160">Jako jedno sestavení nebo jako kolekce sestavení.</span><span class="sxs-lookup"><span data-stu-id="efedf-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="efedf-161">Pomocí této možnosti jednoduše použijete soubory DLL nebo EXE tak, jak byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="efedf-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="efedf-162">Jako skříň (CAB) soubory.</span><span class="sxs-lookup"><span data-stu-id="efedf-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="efedf-163">Pomocí této možnosti můžete komprimovat soubory do souborů CAB, aby distribuce nebo stáhnout méně časově náročné.</span><span class="sxs-lookup"><span data-stu-id="efedf-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="efedf-164">Jako balíček Instalační služby systému Windows nebo v jiných formátech instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="efedf-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="efedf-165">Pomocí této možnosti vytvoříte soubory MSI pro použití s Instalační službou systému Windows nebo zabalíte aplikaci pro použití s jiným instalačním programem.</span><span class="sxs-lookup"><span data-stu-id="efedf-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="efedf-166">Distribuce</span><span class="sxs-lookup"><span data-stu-id="efedf-166">Distribution</span></span>

<span data-ttu-id="efedf-167">Rozhraní .NET Framework poskytuje následující možnosti pro distribuci aplikací:</span><span class="sxs-lookup"><span data-stu-id="efedf-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="efedf-168">Použijte XCOPY nebo FTP.</span><span class="sxs-lookup"><span data-stu-id="efedf-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="efedf-169">Vzhledem k tomu, že aplikace s běžným jazykovým runtime jsou samoobslužné a nevyžadují žádné položky registru, můžete pomocí xcopy nebo FTP jednoduše zkopírovat aplikaci do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="efedf-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="efedf-170">Aplikace pak lze spustit z tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="efedf-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="efedf-171">Použijte kód ke stažení.</span><span class="sxs-lookup"><span data-stu-id="efedf-171">Use code download.</span></span>

     <span data-ttu-id="efedf-172">Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikové sítě intranet, můžete jednoduše stáhnout kód do počítače a spustit aplikaci tam.</span><span class="sxs-lookup"><span data-stu-id="efedf-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="efedf-173">Použijte instalační program, například Instalační službu systému Windows 2.0.</span><span class="sxs-lookup"><span data-stu-id="efedf-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="efedf-174">Instalační služba systému Windows 2.0 může instalovat, opravovat nebo odebírat sestavení rozhraní .NET Framework v globální mezipaměti sestavení a v soukromých adresářích.</span><span class="sxs-lookup"><span data-stu-id="efedf-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="efedf-175">Umístění instalace</span><span class="sxs-lookup"><span data-stu-id="efedf-175">Installation Location</span></span>

<span data-ttu-id="efedf-176">Chcete-li zjistit, kde nasadit sestavení aplikace tak, aby je bylo možné najít v době runtime, naleznete [v tématu Jak runtime vyhledá sestavení](how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="efedf-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="efedf-177">Důležité informace o zabezpečení může také ovlivnit způsob nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="efedf-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="efedf-178">Oprávnění zabezpečení jsou udělena spravovanému kódu podle toho, kde je kód umístěn.</span><span class="sxs-lookup"><span data-stu-id="efedf-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="efedf-179">Nasazení aplikace nebo součásti do umístění, kde získá malou důvěryhodnost, například Internet, omezuje, co aplikace nebo součást může dělat.</span><span class="sxs-lookup"><span data-stu-id="efedf-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="efedf-180">Další informace o nasazení a aspektech zabezpečení naleznete v [tématu Základy zabezpečení přístupu kódu](../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="efedf-180">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="efedf-181">Související témata</span><span class="sxs-lookup"><span data-stu-id="efedf-181">Related Topics</span></span>

|<span data-ttu-id="efedf-182">Nadpis</span><span class="sxs-lookup"><span data-stu-id="efedf-182">Title</span></span>|<span data-ttu-id="efedf-183">Popis</span><span class="sxs-lookup"><span data-stu-id="efedf-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="efedf-184">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="efedf-184">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="efedf-185">Popisuje, jak běžný jazyk runtime určuje, které sestavení použít ke splnění požadavku na vazbu.</span><span class="sxs-lookup"><span data-stu-id="efedf-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="efedf-186">Doporučené postupy pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="efedf-186">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="efedf-187">Popisuje způsoby, jak se vyhnout problémům <xref:System.InvalidCastException>s <xref:System.MissingMethodException>identitou typu, které mohou vést k , a dalším chybám.</span><span class="sxs-lookup"><span data-stu-id="efedf-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="efedf-188">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="efedf-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="efedf-189">Popisuje Správce restartování, který brání restartování, kdykoli je to možné, a vysvětluje, jak aplikace, které instalují rozhraní .NET Framework, mohou využít.</span><span class="sxs-lookup"><span data-stu-id="efedf-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="efedf-190">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="efedf-190">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="efedf-191">Vysvětluje, jak může správce systému nasadit rozhraní .NET Framework a jeho systémové závislosti v síti pomocí nástroje Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="efedf-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="efedf-192">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="efedf-192">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="efedf-193">Vysvětluje, jak mohou vývojáři nainstalovat rozhraní .NET Framework do počítačů svých uživatelů pomocí svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="efedf-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="efedf-194">Nasazení aplikací, služeb a komponent</span><span class="sxs-lookup"><span data-stu-id="efedf-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="efedf-195">Popisuje možnosti nasazení v sadě Visual Studio, včetně pokynů pro publikování aplikace pomocí technologií ClickOnce a Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="efedf-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="efedf-196">Publikování aplikací ClickOnce</span><span class="sxs-lookup"><span data-stu-id="efedf-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="efedf-197">Popisuje, jak zabalit aplikaci Windows Forms a nasadit ji pomocí clickonce do klientských počítačů v síti.</span><span class="sxs-lookup"><span data-stu-id="efedf-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="efedf-198">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="efedf-198">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="efedf-199">Popisuje model rozbočovače a paprsku, který rozhraní .NET Framework používá k balení a nasazení prostředků. zahrnuje konvence pojmenování prostředků, záložní proces a alternativy balení.</span><span class="sxs-lookup"><span data-stu-id="efedf-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="efedf-200">Nasazení aplikace spolupráce</span><span class="sxs-lookup"><span data-stu-id="efedf-200">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="efedf-201">Vysvětluje, jak dodávat a instalovat interop aplikace, které obvykle zahrnují sestavení klienta rozhraní .NET Framework, jedno nebo více meziop sestavení představujících odlišné knihovny typů MODELU A jednu nebo více registrovaných součástí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="efedf-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="efedf-202">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="efedf-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="efedf-203">Popisuje, jak tiše spustit a sledovat proces nastavení rozhraní .NET Framework při zobrazení vlastního zobrazení průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="efedf-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="efedf-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="efedf-204">See also</span></span>

- [<span data-ttu-id="efedf-205">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="efedf-205">Development Guide</span></span>](../development-guide.md)
