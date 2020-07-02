---
title: Nasazení .NET Framework a aplikací
description: Začněte s nasazením .NET s vaší aplikací. Rozhraní .NET poskytuje aplikace bez dopadu, soukromé komponenty ve výchozím nastavení, řízená sdílení kódu a další.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: cce888c962c9ab83c13cce4040eb9ba50270972d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803496"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="b1d57-104">Nasazení .NET Framework a aplikací</span><span class="sxs-lookup"><span data-stu-id="b1d57-104">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="b1d57-105">Tento článek vám pomůže začít s nasazením .NET Framework s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="b1d57-105">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="b1d57-106">Většina informací je určená vývojářům, výrobcům OEM a podnikovým správcům.</span><span class="sxs-lookup"><span data-stu-id="b1d57-106">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="b1d57-107">Uživatelé, kteří chtějí instalovat .NET Framework na svých počítačích, by si měli přečíst [instalaci .NET Framework](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="b1d57-107">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="b1d57-108">Prostředky nasazení klíčů</span><span class="sxs-lookup"><span data-stu-id="b1d57-108">Key Deployment Resources</span></span>

<span data-ttu-id="b1d57-109">Pro konkrétní informace o nasazení a údržbě .NET Framework použijte následující odkazy na další témata MSDN.</span><span class="sxs-lookup"><span data-stu-id="b1d57-109">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="b1d57-110">**Nastavení a nasazení**</span><span class="sxs-lookup"><span data-stu-id="b1d57-110">**Setup and deployment**</span></span>

- <span data-ttu-id="b1d57-111">Obecné informace o instalačním programu a nasazení:</span><span class="sxs-lookup"><span data-stu-id="b1d57-111">General installer and deployment information:</span></span>

  - <span data-ttu-id="b1d57-112">Možnosti instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="b1d57-112">Installer options:</span></span>

    - [<span data-ttu-id="b1d57-113">Webová instalační služba</span><span class="sxs-lookup"><span data-stu-id="b1d57-113">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="b1d57-114">Offline instalační program</span><span class="sxs-lookup"><span data-stu-id="b1d57-114">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="b1d57-115">Režimy instalace:</span><span class="sxs-lookup"><span data-stu-id="b1d57-115">Installation modes:</span></span>

    - [<span data-ttu-id="b1d57-116">Bezobslužná instalace</span><span class="sxs-lookup"><span data-stu-id="b1d57-116">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="b1d57-117">Zobrazení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1d57-117">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="b1d57-118">Snížení restartu systému během instalací .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="b1d57-118">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="b1d57-119">Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1d57-119">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="b1d57-120">Nasazení .NET Framework pomocí klientské aplikace (pro vývojáře):</span><span class="sxs-lookup"><span data-stu-id="b1d57-120">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="b1d57-121">[Používání programu InstallShield](deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení</span><span class="sxs-lookup"><span data-stu-id="b1d57-121">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="b1d57-122">Použití aplikace Visual Studio ClickOnce</span><span class="sxs-lookup"><span data-stu-id="b1d57-122">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="b1d57-123">Vytvoření instalačního balíčku WiX</span><span class="sxs-lookup"><span data-stu-id="b1d57-123">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="b1d57-124">Použití vlastního instalačního programu</span><span class="sxs-lookup"><span data-stu-id="b1d57-124">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="b1d57-125">[Další informace](deployment-guide-for-developers.md) pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b1d57-125">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="b1d57-126">Nasazení .NET Framework (pro výrobce OEM a správce):</span><span class="sxs-lookup"><span data-stu-id="b1d57-126">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="b1d57-127">Sada Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="b1d57-127">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="b1d57-128">Příručka pro správce</span><span class="sxs-lookup"><span data-stu-id="b1d57-128">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="b1d57-129">**Údržba**</span><span class="sxs-lookup"><span data-stu-id="b1d57-129">**Servicing**</span></span>

- <span data-ttu-id="b1d57-130">Obecné informace najdete na [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="b1d57-130">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="b1d57-131">Zjišťují se verze</span><span class="sxs-lookup"><span data-stu-id="b1d57-131">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="b1d57-132">Zjišťování aktualizací Service Pack a aktualizací</span><span class="sxs-lookup"><span data-stu-id="b1d57-132">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="b1d57-133">Funkce, které zjednodušují nasazení</span><span class="sxs-lookup"><span data-stu-id="b1d57-133">Features That Simplify Deployment</span></span>

<span data-ttu-id="b1d57-134">.NET Framework poskytuje řadu základních funkcí, které usnadňují nasazení aplikací:</span><span class="sxs-lookup"><span data-stu-id="b1d57-134">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="b1d57-135">Aplikace bez dopadu.</span><span class="sxs-lookup"><span data-stu-id="b1d57-135">No-impact applications.</span></span>

     <span data-ttu-id="b1d57-136">Tato funkce poskytuje izolaci aplikace a eliminuje konflikty knihoven DLL.</span><span class="sxs-lookup"><span data-stu-id="b1d57-136">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="b1d57-137">Ve výchozím nastavení komponenty neovlivňují jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1d57-137">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="b1d57-138">Ve výchozím nastavení soukromé součásti.</span><span class="sxs-lookup"><span data-stu-id="b1d57-138">Private components by default.</span></span>

     <span data-ttu-id="b1d57-139">Ve výchozím nastavení jsou komponenty nasazeny do adresáře aplikace a jsou viditelné pouze pro aplikaci, která ji obsahuje.</span><span class="sxs-lookup"><span data-stu-id="b1d57-139">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="b1d57-140">Řízená sdílení kódu.</span><span class="sxs-lookup"><span data-stu-id="b1d57-140">Controlled code sharing.</span></span>

     <span data-ttu-id="b1d57-141">Sdílení kódu vyžaduje explicitní zpřístupnění kódu pro sdílení namísto výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="b1d57-141">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="b1d57-142">Souběžná Správa verzí.</span><span class="sxs-lookup"><span data-stu-id="b1d57-142">Side-by-side versioning.</span></span>

     <span data-ttu-id="b1d57-143">Několik verzí komponenty nebo aplikace může existovat současně, můžete zvolit, které verze se mají použít, a modul CLR (Common Language Runtime) vynutil zásady správy verzí.</span><span class="sxs-lookup"><span data-stu-id="b1d57-143">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="b1d57-144">Nasazení a replikace XCOPY.</span><span class="sxs-lookup"><span data-stu-id="b1d57-144">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="b1d57-145">Samostatné a samostatně uzavřené komponenty a aplikace lze nasadit bez položek registru nebo závislostí.</span><span class="sxs-lookup"><span data-stu-id="b1d57-145">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="b1d57-146">Průběžné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="b1d57-146">On-the-fly updates.</span></span>

     <span data-ttu-id="b1d57-147">Správci můžou použít hostitele, jako je ASP.NET, k aktualizaci knihoven DLL programu, i na vzdálených počítačích.</span><span class="sxs-lookup"><span data-stu-id="b1d57-147">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="b1d57-148">Integrace s Instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b1d57-148">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="b1d57-149">Inzerce, publikování, opravy a instalace na vyžádání jsou dostupné při nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1d57-149">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="b1d57-150">Podnikové nasazení.</span><span class="sxs-lookup"><span data-stu-id="b1d57-150">Enterprise deployment.</span></span>

     <span data-ttu-id="b1d57-151">Tato funkce poskytuje jednoduchou distribuci softwaru, včetně používání služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b1d57-151">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="b1d57-152">Stahování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b1d57-152">Downloading and caching.</span></span>

     <span data-ttu-id="b1d57-153">Přírůstkové stahování udržuje menší soubory ke stažení a součásti lze izolovat pouze pro použití v aplikaci pro nasazení s nízkým dopadem.</span><span class="sxs-lookup"><span data-stu-id="b1d57-153">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="b1d57-154">Částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="b1d57-154">Partially trusted code.</span></span>

     <span data-ttu-id="b1d57-155">Identita je založena na kódu namísto uživatele a nezobrazují se dialogová okna certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b1d57-155">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="b1d57-156">Balení a distribuce .NET Frameworkch aplikací</span><span class="sxs-lookup"><span data-stu-id="b1d57-156">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="b1d57-157">Některé informace o balení a nasazení pro .NET Framework jsou popsány v dalších částech dokumentace.</span><span class="sxs-lookup"><span data-stu-id="b1d57-157">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="b1d57-158">Tyto části poskytují informace o jednotkách, které jsou označovány jako [sestavení](../../standard/assembly/index.md), které nevyžadují žádné položky registru, [sestavení se silným názvem](../../standard/assembly/strong-named.md), které zajišťují jedinečnost názvu a brání falšování názvů a [správu verzí sestavení](../../standard/assembly/versioning.md), které řeší mnohé problémy spojené s konflikty knihoven DLL.</span><span class="sxs-lookup"><span data-stu-id="b1d57-158">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="b1d57-159">Následující části obsahují informace o balení a distribuci .NET Frameworkch aplikací.</span><span class="sxs-lookup"><span data-stu-id="b1d57-159">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="b1d57-160">Zabalení</span><span class="sxs-lookup"><span data-stu-id="b1d57-160">Packaging</span></span>

<span data-ttu-id="b1d57-161">.NET Framework poskytuje následující možnosti pro vytváření balíčků aplikací:</span><span class="sxs-lookup"><span data-stu-id="b1d57-161">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="b1d57-162">Jako jedno sestavení nebo jako kolekce sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1d57-162">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="b1d57-163">Pomocí této možnosti jednoduše použijete soubory. dll nebo. exe, jak byly sestaveny.</span><span class="sxs-lookup"><span data-stu-id="b1d57-163">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="b1d57-164">Jako soubory CAB.</span><span class="sxs-lookup"><span data-stu-id="b1d57-164">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="b1d57-165">Pomocí této možnosti zkomprimujete soubory do souborů. cab, abyste mohli distribuovat nebo stahovat méně času náročného.</span><span class="sxs-lookup"><span data-stu-id="b1d57-165">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="b1d57-166">Jako balíček Instalační služba systému Windows nebo v jiných formátech instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="b1d57-166">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="b1d57-167">Pomocí této možnosti vytvoříte soubory. msi pro použití s Instalační služba systému Windows nebo zabalíte aplikaci pro použití s nějakým jiným instalačním programem.</span><span class="sxs-lookup"><span data-stu-id="b1d57-167">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="b1d57-168">Distribuce</span><span class="sxs-lookup"><span data-stu-id="b1d57-168">Distribution</span></span>

<span data-ttu-id="b1d57-169">.NET Framework poskytuje následující možnosti pro distribuci aplikací:</span><span class="sxs-lookup"><span data-stu-id="b1d57-169">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="b1d57-170">Použijte XCOPY nebo FTP.</span><span class="sxs-lookup"><span data-stu-id="b1d57-170">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="b1d57-171">Vzhledem k tomu, že aplikace modulu CLR (Common Language Runtime) samy popisují a nevyžadují žádné položky registru, můžete pomocí příkazu XCOPY nebo FTP jednoduše zkopírovat aplikaci do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="b1d57-171">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="b1d57-172">Aplikaci lze následně spustit z tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="b1d57-172">The application can then be run from that directory.</span></span>

- <span data-ttu-id="b1d57-173">Použijte stahování kódu.</span><span class="sxs-lookup"><span data-stu-id="b1d57-173">Use code download.</span></span>

     <span data-ttu-id="b1d57-174">Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikového intranetu, můžete jednoduše stáhnout kód do počítače a spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b1d57-174">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="b1d57-175">Použijte instalační program, například Instalační služba systému Windows 2,0.</span><span class="sxs-lookup"><span data-stu-id="b1d57-175">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="b1d57-176">Instalační služba systému Windows 2,0 může instalovat, opravovat nebo odebírat .NET Framework sestavení v globální mezipaměti sestavení (GAC) a v privátních adresářích.</span><span class="sxs-lookup"><span data-stu-id="b1d57-176">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="b1d57-177">Umístění instalace</span><span class="sxs-lookup"><span data-stu-id="b1d57-177">Installation Location</span></span>

<span data-ttu-id="b1d57-178">Chcete-li určit, kam se mají nasadit sestavení vaší aplikace, aby je bylo možné najít modulem runtime, přečtěte si téma [jak modul runtime vyhledává sestavení](how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b1d57-178">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="b1d57-179">Požadavky na zabezpečení mohou také ovlivnit způsob nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1d57-179">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="b1d57-180">Oprávnění zabezpečení se udělují spravovanému kódu podle toho, kde se nachází kód.</span><span class="sxs-lookup"><span data-stu-id="b1d57-180">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="b1d57-181">Nasazení aplikace nebo komponenty do umístění, kde obdrží malý vztah důvěryhodnosti, jako je například Internet, omezuje, co může aplikace nebo komponenta dělat.</span><span class="sxs-lookup"><span data-stu-id="b1d57-181">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="b1d57-182">Další informace o možnostech nasazení a zabezpečení najdete v tématu [Základy zabezpečení přístupu kódu](../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b1d57-182">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="b1d57-183">Související témata</span><span class="sxs-lookup"><span data-stu-id="b1d57-183">Related Topics</span></span>

|<span data-ttu-id="b1d57-184">Nadpis</span><span class="sxs-lookup"><span data-stu-id="b1d57-184">Title</span></span>|<span data-ttu-id="b1d57-185">Popis</span><span class="sxs-lookup"><span data-stu-id="b1d57-185">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="b1d57-186">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b1d57-186">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="b1d57-187">Popisuje, jak modul CLR (Common Language Runtime) určuje, které sestavení se má použít ke splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="b1d57-187">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="b1d57-188">Doporučené postupy pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="b1d57-188">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="b1d57-189">Popisuje způsoby, jak zabránit problémům s typem identity, který může vést k <xref:System.InvalidCastException> <xref:System.MissingMethodException> chybám, a.</span><span class="sxs-lookup"><span data-stu-id="b1d57-189">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="b1d57-190">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b1d57-190">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="b1d57-191">Popisuje správce restartování, který znemožňuje restartování, kdykoli je to možné, a vysvětluje, jak můžou aplikace, které instalují .NET Framework, využít.</span><span class="sxs-lookup"><span data-stu-id="b1d57-191">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="b1d57-192">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="b1d57-192">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="b1d57-193">Vysvětluje, jak může správce systému nasadit .NET Framework a jeho systémové závislosti v síti pomocí služby Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="b1d57-193">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="b1d57-194">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b1d57-194">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="b1d57-195">Vysvětluje, jak můžou vývojáři instalovat .NET Framework na počítačích uživatelů s jejich aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="b1d57-195">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="b1d57-196">Nasazení aplikací, služeb a komponent</span><span class="sxs-lookup"><span data-stu-id="b1d57-196">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="b1d57-197">Popisuje možnosti nasazení v aplikaci Visual Studio, včetně pokynů pro publikování aplikace pomocí technologie ClickOnce a Instalační služba systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b1d57-197">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="b1d57-198">Publikování aplikací ClickOnce</span><span class="sxs-lookup"><span data-stu-id="b1d57-198">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="b1d57-199">Popisuje, jak zabalit aplikaci model Windows Forms a nasadit ji pomocí technologie ClickOnce na klientské počítače v síti.</span><span class="sxs-lookup"><span data-stu-id="b1d57-199">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="b1d57-200">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="b1d57-200">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="b1d57-201">Popisuje model hvězdicové a paprsky, které .NET Framework používá k zabalení a nasazení prostředků. Popisuje zásady vytváření názvů prostředků, záložní proces a alternativy balení.</span><span class="sxs-lookup"><span data-stu-id="b1d57-201">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="b1d57-202">Nasazení aplikace spolupráce</span><span class="sxs-lookup"><span data-stu-id="b1d57-202">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="b1d57-203">Vysvětluje, jak dodávat a instalovat aplikace spolupráce, které obvykle zahrnují .NET Framework sestavení klienta, jedno nebo více definičních sestavení představujících odlišné knihovny typů modelu COM a jednu nebo více registrovaných komponent modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b1d57-203">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="b1d57-204">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b1d57-204">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="b1d57-205">V této části najdete popis postupu při tichém spuštění a sledování procesu instalace .NET Framework při zobrazení vlastního zobrazení průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="b1d57-205">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b1d57-206">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1d57-206">See also</span></span>

- [<span data-ttu-id="b1d57-207">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="b1d57-207">Development Guide</span></span>](../development-guide.md)
