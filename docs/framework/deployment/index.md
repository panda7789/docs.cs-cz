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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a650fa0340ce63a573074746eef60994e2254c86
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453226"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="09661-102">Nasazení .NET Framework a aplikací</span><span class="sxs-lookup"><span data-stu-id="09661-102">Deploying the .NET Framework and Applications</span></span>
<span data-ttu-id="09661-103">Tento článek pomůže začít nasazení rozhraní .NET Framework s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="09661-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="09661-104">Většina informací je určená pro vývojáře, výrobci OEM a enterprise administrators.</span><span class="sxs-lookup"><span data-stu-id="09661-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="09661-105">Uživatelé, kteří chtějí nainstalovat rozhraní .NET Framework na svých počítačích byste si přečíst [instalace rozhraní .NET Framework](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="09661-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>  
  
## <a name="key-deployment-resources"></a><span data-ttu-id="09661-106">Klíče nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="09661-106">Key Deployment Resources</span></span>  
 <span data-ttu-id="09661-107">Použijte následující odkazy na další témata MSDN pro konkrétní informace o nasazení a údržba rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09661-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>  
  
 <span data-ttu-id="09661-108">**Instalace a nasazení**</span><span class="sxs-lookup"><span data-stu-id="09661-108">**Setup and deployment**</span></span>  
  
-   <span data-ttu-id="09661-109">Obecné informace Instalační program a nasazení:</span><span class="sxs-lookup"><span data-stu-id="09661-109">General installer and deployment information:</span></span>  
  
    -   <span data-ttu-id="09661-110">Instalační program možnosti:</span><span class="sxs-lookup"><span data-stu-id="09661-110">Installer options:</span></span>  
  
        -   [<span data-ttu-id="09661-111">Webová instalační služba</span><span class="sxs-lookup"><span data-stu-id="09661-111">Web installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [<span data-ttu-id="09661-112">Offline instalační program</span><span class="sxs-lookup"><span data-stu-id="09661-112">Offline installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   <span data-ttu-id="09661-113">Režimy instalace:</span><span class="sxs-lookup"><span data-stu-id="09661-113">Installation modes:</span></span>  
  
        -   [<span data-ttu-id="09661-114">Bezobslužná instalace</span><span class="sxs-lookup"><span data-stu-id="09661-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [<span data-ttu-id="09661-115">Zobrazení uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="09661-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [<span data-ttu-id="09661-116">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="09661-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [<span data-ttu-id="09661-117">Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="09661-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   <span data-ttu-id="09661-118">Nasazení rozhraní .NET Framework pomocí klientské aplikace (pro vývojáře):</span><span class="sxs-lookup"><span data-stu-id="09661-118">Deploying the .NET Framework with a client application (for developers):</span></span>  
  
    -   <span data-ttu-id="09661-119">[Pomocí programu InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) v projektu instalace a nasazení</span><span class="sxs-lookup"><span data-stu-id="09661-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>  
  
    -   [<span data-ttu-id="09661-120">Pomocí aplikace Visual Studio ClickOnce</span><span class="sxs-lookup"><span data-stu-id="09661-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [<span data-ttu-id="09661-121">Vytvoření balíčku instalace WiX</span><span class="sxs-lookup"><span data-stu-id="09661-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [<span data-ttu-id="09661-122">Pomocí vlastního instalačního programu</span><span class="sxs-lookup"><span data-stu-id="09661-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   <span data-ttu-id="09661-123">[Další informace o](../../../docs/framework/deployment/deployment-guide-for-developers.md) pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="09661-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>  
  
-   <span data-ttu-id="09661-124">Nasazení rozhraní .NET Framework (pro výrobce OEM a správce):</span><span class="sxs-lookup"><span data-stu-id="09661-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>  
  
    -   [<span data-ttu-id="09661-125">Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="09661-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [<span data-ttu-id="09661-126">Příručka pro správce</span><span class="sxs-lookup"><span data-stu-id="09661-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 <span data-ttu-id="09661-127">**Údržba**</span><span class="sxs-lookup"><span data-stu-id="09661-127">**Servicing**</span></span>  
  
-   <span data-ttu-id="09661-128">Obecné informace najdete v tématu [blogu .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span><span class="sxs-lookup"><span data-stu-id="09661-128">For general information, see the [.NET Framework blog](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>  
  
-   [<span data-ttu-id="09661-129">Zjištění verze</span><span class="sxs-lookup"><span data-stu-id="09661-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [<span data-ttu-id="09661-130">Zjišťování aktualizací service Pack a aktualizace</span><span class="sxs-lookup"><span data-stu-id="09661-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a><span data-ttu-id="09661-131">Funkce, které zjednodušují nasazení</span><span class="sxs-lookup"><span data-stu-id="09661-131">Features That Simplify Deployment</span></span>  
 <span data-ttu-id="09661-132">Rozhraní .NET Framework poskytuje řadu základních funkcí, které zjednodušují nasazení aplikací:</span><span class="sxs-lookup"><span data-stu-id="09661-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>  
  
-   <span data-ttu-id="09661-133">Aplikace bez dopadu.</span><span class="sxs-lookup"><span data-stu-id="09661-133">No-impact applications.</span></span>  
  
     <span data-ttu-id="09661-134">Tato funkce zajišťuje izolaci aplikace a eliminuje DLL – konflikty.</span><span class="sxs-lookup"><span data-stu-id="09661-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="09661-135">Ve výchozím nastavení komponenty nemají vliv na jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="09661-135">By default, components do not affect other applications.</span></span>  
  
-   <span data-ttu-id="09661-136">Součásti ve výchozím nastavení je privátní.</span><span class="sxs-lookup"><span data-stu-id="09661-136">Private components by default.</span></span>  
  
     <span data-ttu-id="09661-137">Ve výchozím nastavení komponenty jsou nasazené do adresáře aplikace a jsou viditelné pouze pro obsahující aplikaci.</span><span class="sxs-lookup"><span data-stu-id="09661-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>  
  
-   <span data-ttu-id="09661-138">Řízené sdílení kódu.</span><span class="sxs-lookup"><span data-stu-id="09661-138">Controlled code sharing.</span></span>  
  
     <span data-ttu-id="09661-139">Sdílení kódu, musíte explicitně zpřístupnit kód pro sdílení obsahu namísto výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="09661-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>  
  
-   <span data-ttu-id="09661-140">Správa verzí vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="09661-140">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="09661-141">Více verzí aplikace nebo součásti mohou existovat vedle sebe, můžete zvolit, které verze používat, a modul common language runtime vynucuje zásad správy verzí.</span><span class="sxs-lookup"><span data-stu-id="09661-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>  
  
-   <span data-ttu-id="09661-142">Replikace a nasazení XCOPY.</span><span class="sxs-lookup"><span data-stu-id="09661-142">XCOPY deployment and replication.</span></span>  
  
     <span data-ttu-id="09661-143">Samostatná a místním popisu komponent a aplikací můžete nasadit bez položky registru nebo závislosti.</span><span class="sxs-lookup"><span data-stu-id="09661-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>  
  
-   <span data-ttu-id="09661-144">Na průběžné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="09661-144">On-the-fly updates.</span></span>  
  
     <span data-ttu-id="09661-145">Správci můžou použít hostitele, jako je ASP.NET, k aktualizaci aplikace knihovny DLL, i na vzdálených počítačích.</span><span class="sxs-lookup"><span data-stu-id="09661-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>  
  
-   <span data-ttu-id="09661-146">Integrace pomocí Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="09661-146">Integration with the Windows Installer.</span></span>  
  
     <span data-ttu-id="09661-147">Oznámení o inzerovaném programu, publikování, opravy a instalaci na vyžádání jsou všechny dostupné při nasazování aplikace.</span><span class="sxs-lookup"><span data-stu-id="09661-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>  
  
-   <span data-ttu-id="09661-148">Nasazení v podniku.</span><span class="sxs-lookup"><span data-stu-id="09661-148">Enterprise deployment.</span></span>  
  
     <span data-ttu-id="09661-149">Tato funkce poskytuje distribuce snadno softwaru, včetně použití služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="09661-149">This feature provides easy software distribution, including using Active Directory.</span></span>  
  
-   <span data-ttu-id="09661-150">Stahování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="09661-150">Downloading and caching.</span></span>  
  
     <span data-ttu-id="09661-151">Přírůstková stahování zachovat menší soubory ke stažení a komponenty můžou být izolované pro použití pouze pomocí aplikace pro nasazení nízkým dopadem na koncové uživatele.</span><span class="sxs-lookup"><span data-stu-id="09661-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>  
  
-   <span data-ttu-id="09661-152">Částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="09661-152">Partially trusted code.</span></span>  
  
     <span data-ttu-id="09661-153">Identita je založena na kódu, nikoli na uživatele a dialogová žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="09661-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>  
  
## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="09661-154">Balení a distribuce aplikací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="09661-154">Packaging and Distributing .NET Framework Applications</span></span>  
 <span data-ttu-id="09661-155">Některé balení a informace o nasazení pro rozhraní .NET Framework je popsané v dalších částech v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="09661-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="09661-156">Tyto části obsahují informace o popisující samy sebe jednotky nazvané [sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), které vyžadují žádné položky registru [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md), který zajistí jedinečnost názvu a zabránit název falšování identity, a [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md), které řeší celou řadu problémy související s DLL – konflikty.</span><span class="sxs-lookup"><span data-stu-id="09661-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="09661-157">Následující části obsahují informace o balení a distribuce aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09661-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>  
  
### <a name="packaging"></a><span data-ttu-id="09661-158">Balení</span><span class="sxs-lookup"><span data-stu-id="09661-158">Packaging</span></span>  
 <span data-ttu-id="09661-159">Rozhraní .NET Framework poskytuje následující možnosti pro vytváření balíčků aplikací:</span><span class="sxs-lookup"><span data-stu-id="09661-159">The .NET Framework provides the following options for packaging applications:</span></span>  
  
-   <span data-ttu-id="09661-160">Jako jednoho sestavení nebo jako kolekci sestavení.</span><span class="sxs-lookup"><span data-stu-id="09661-160">As a single assembly or as a collection of assemblies.</span></span>  
  
     <span data-ttu-id="09661-161">Když je tato možnost jednoduše používáte soubory .dll nebo .exe jako byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="09661-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>  
  
-   <span data-ttu-id="09661-162">Jako soubory CAB (CAB).</span><span class="sxs-lookup"><span data-stu-id="09661-162">As cabinet (CAB) files.</span></span>  
  
     <span data-ttu-id="09661-163">Pomocí této možnosti komprimovat soubor do souborů .cab distribuce nebo stáhnout méně časově náročné.</span><span class="sxs-lookup"><span data-stu-id="09661-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>  
  
-   <span data-ttu-id="09661-164">Jako balíček Instalační služby systému Windows nebo v jiných formátů Instalační služby.</span><span class="sxs-lookup"><span data-stu-id="09661-164">As a Windows Installer package or in other installer formats.</span></span>  
  
     <span data-ttu-id="09661-165">Pomocí této možnosti vytvoříte soubory .msi pro použití Instalační služby systému Windows nebo balíček aplikace pro použití s další instalační služby.</span><span class="sxs-lookup"><span data-stu-id="09661-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>  
  
### <a name="distribution"></a><span data-ttu-id="09661-166">Distribuce</span><span class="sxs-lookup"><span data-stu-id="09661-166">Distribution</span></span>  
 <span data-ttu-id="09661-167">Rozhraní .NET Framework poskytuje následující možnosti distribuce aplikací:</span><span class="sxs-lookup"><span data-stu-id="09661-167">The .NET Framework provides the following options for distributing applications:</span></span>  
  
-   <span data-ttu-id="09661-168">Pomocí příkazu XCOPY nebo FTP.</span><span class="sxs-lookup"><span data-stu-id="09661-168">Use XCOPY or FTP.</span></span>  
  
     <span data-ttu-id="09661-169">Protože common language runtime aplikace jsou samovysvětlující a vyžadují žádné položky registru, jednoduše zkopírujte aplikaci do příslušného adresáře můžete použít příkazu XCOPY nebo FTP.</span><span class="sxs-lookup"><span data-stu-id="09661-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="09661-170">Aplikace se dá spustit pak z tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="09661-170">The application can then be run from that directory.</span></span>  
  
-   <span data-ttu-id="09661-171">Použijte kód ke stažení.</span><span class="sxs-lookup"><span data-stu-id="09661-171">Use code download.</span></span>  
  
     <span data-ttu-id="09661-172">Pokud distribuujete aplikaci přes Internet nebo prostřednictvím podnikové síti, do počítače stáhnout kód a spusťte aplikaci existuje.</span><span class="sxs-lookup"><span data-stu-id="09661-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>  
  
-   <span data-ttu-id="09661-173">Pomocí instalačního programu jako 2.0 Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="09661-173">Use an installer program such as Windows Installer 2.0.</span></span>  
  
     <span data-ttu-id="09661-174">2.0 Instalační služby systému Windows můžete nainstalovat, opravit nebo odebrat sestavení rozhraní .NET Framework v globální mezipaměti sestavení a privátní adresáře.</span><span class="sxs-lookup"><span data-stu-id="09661-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>  
  
### <a name="installation-location"></a><span data-ttu-id="09661-175">Umístění instalace</span><span class="sxs-lookup"><span data-stu-id="09661-175">Installation Location</span></span>  
 <span data-ttu-id="09661-176">Pokud chcete zjistit, jak nasadíte sestavení vaší aplikace, takže najdete modulem runtime, naleznete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="09661-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="09661-177">Důležité informace o zabezpečení může také ovlivnit způsob nasazení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="09661-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="09661-178">Spravovaný kód podle toho, kde je kód umístěn udělují oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09661-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="09661-179">Nasazení aplikace nebo komponenty do umístění, ve kterém přijímá trochu vztahu důvěryhodnosti, jako je například Internet, omezení aplikace nebo komponenta přínosech.</span><span class="sxs-lookup"><span data-stu-id="09661-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="09661-180">Další informace o nasazení a důležité informace o zabezpečení najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="09661-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="09661-181">Související témata</span><span class="sxs-lookup"><span data-stu-id="09661-181">Related Topics</span></span>  
  
|<span data-ttu-id="09661-182">Název</span><span class="sxs-lookup"><span data-stu-id="09661-182">Title</span></span>|<span data-ttu-id="09661-183">Popis</span><span class="sxs-lookup"><span data-stu-id="09661-183">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="09661-184">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="09661-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="09661-185">Popisuje, jak modul common language runtime určuje sestavení, které použít ke splnění požadavků vazby.</span><span class="sxs-lookup"><span data-stu-id="09661-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|  
|[<span data-ttu-id="09661-186">Doporučené postupy pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="09661-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="09661-187">Tento článek popisuje způsoby, jak se vyhnout problémům identity typu, který může mít za následek <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a další chyby.</span><span class="sxs-lookup"><span data-stu-id="09661-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|  
|[<span data-ttu-id="09661-188">Omezení restartů systému při instalaci rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="09661-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="09661-189">Popisuje správce restartování se zabránilo restartuje kdykoli je to možné a vysvětluje, jak aplikace, které instalace rozhraní .NET Framework můžete využívat jejich výhod.</span><span class="sxs-lookup"><span data-stu-id="09661-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|  
|[<span data-ttu-id="09661-190">Příručka nasazení pro administrátory</span><span class="sxs-lookup"><span data-stu-id="09661-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="09661-191">Vysvětluje, jak může správce systému můžete nasadit rozhraní .NET Framework a jeho systémové závislosti napříč sítí pomocí System Center Configuration Manageru (SCCM).</span><span class="sxs-lookup"><span data-stu-id="09661-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|  
|[<span data-ttu-id="09661-192">Průvodce nasazením pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="09661-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="09661-193">Vysvětluje, jak vývojáři můžete nainstalovat rozhraní .NET Framework na jejich uživatele, počítače s jejich aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="09661-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|  
|[<span data-ttu-id="09661-194">Nasazení aplikací, služeb a komponent</span><span class="sxs-lookup"><span data-stu-id="09661-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="09661-195">Tento článek popisuje možnosti nasazení v sadě Visual Studio, včetně pokynů pro publikování aplikace pomocí technologie ClickOnce a instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="09661-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>| 
|[<span data-ttu-id="09661-196">Publikování aplikací ClickOnce</span><span class="sxs-lookup"><span data-stu-id="09661-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="09661-197">Popisuje, jak zabalit aplikace modelu Windows Forms a nasazení pomocí technologie ClickOnce pro klientské počítače v síti.</span><span class="sxs-lookup"><span data-stu-id="09661-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|  
|[<span data-ttu-id="09661-198">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="09661-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="09661-199">Popisuje model střed a paprsek, balení a nasazení prostředků; využívající rozhraní .NET Framework popisuje konvence, proces získávání náhradních a balení alternativy pojmenování prostředků.</span><span class="sxs-lookup"><span data-stu-id="09661-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|  
|[<span data-ttu-id="09661-200">Nasazení aplikace spolupráce</span><span class="sxs-lookup"><span data-stu-id="09661-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="09661-201">Vysvětluje způsob dodání a nainstalujte spolupráce – aplikace, které sestavení klienta rozhraní .NET Framework, obvykle zahrnují jeden nebo více sestavení vzájemné spolupráce reprezentující různé knihovny typů modelu COM, a jeden nebo víc registrovaných komponent COM.</span><span class="sxs-lookup"><span data-stu-id="09661-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|  
|[<span data-ttu-id="09661-202">Postupy: Získání procesu z instalačního programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="09661-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="09661-203">Popisuje, jak spustit bez upozornění a sledovat proces instalace rozhraní .NET Framework při vlastním zobrazením průběhu instalace.</span><span class="sxs-lookup"><span data-stu-id="09661-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09661-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="09661-204">See Also</span></span>  
- [<span data-ttu-id="09661-205">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="09661-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
