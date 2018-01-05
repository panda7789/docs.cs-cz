---
title: "Sbalení URI v technologii WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3143bcc05d88cde43e844ec21b95963e672bbc52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="75bf8-102">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="75bf8-102">Pack URIs in WPF</span></span>
<span data-ttu-id="75bf8-103">V [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] slouží k identifikaci a načíst soubory mnoha způsoby, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="75bf8-103">In [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>  
  
-   <span data-ttu-id="75bf8-104">Určení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zobrazíte při aplikaci prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="75bf8-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>  
  
-   <span data-ttu-id="75bf8-105">Načítání obrázků.</span><span class="sxs-lookup"><span data-stu-id="75bf8-105">Loading images.</span></span>  
  
-   <span data-ttu-id="75bf8-106">Navigace na stránky.</span><span class="sxs-lookup"><span data-stu-id="75bf8-106">Navigating to pages.</span></span>  
  
-   <span data-ttu-id="75bf8-107">Načítání-spustitelný soubor datových souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-107">Loading non-executable data files.</span></span>  
  
 <span data-ttu-id="75bf8-108">Kromě toho [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] slouží k identifikaci a nahrajte soubory z různých umístění, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="75bf8-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>  
  
-   <span data-ttu-id="75bf8-109">Aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-109">The current assembly.</span></span>  
  
-   <span data-ttu-id="75bf8-110">Odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-110">A referenced assembly.</span></span>  
  
-   <span data-ttu-id="75bf8-111">Umístění relativně k sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-111">A location relative to an assembly.</span></span>  
  
-   <span data-ttu-id="75bf8-112">Aplikace Web původu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-112">The application's site of origin.</span></span>  
  
 <span data-ttu-id="75bf8-113">K zajištění konzistentní mechanismus pro identifikaci a načítání těchto typů souborů z těchto umístění [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá rozšiřitelnosti služby *schéma identifikátoru URI pack*.</span><span class="sxs-lookup"><span data-stu-id="75bf8-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="75bf8-114">Toto téma obsahuje přehled schéma, popisuje postup vytvoření pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé scénáře, popisuje absolutní a relativní [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení před znázorňující způsob použití sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obou značek a kód.</span><span class="sxs-lookup"><span data-stu-id="75bf8-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a><span data-ttu-id="75bf8-115">Schéma identifikátoru URI Pack</span><span class="sxs-lookup"><span data-stu-id="75bf8-115">The Pack URI Scheme</span></span>  
 <span data-ttu-id="75bf8-116">Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma používá [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) specifikace (OPC), která popisuje model pro uspořádání a určení obsahu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="75bf8-117">Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíček* je logický kontejner pro jednu nebo více logických *částí*.</span><span class="sxs-lookup"><span data-stu-id="75bf8-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="75bf8-118">Tento koncept znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="75bf8-118">The following figure illustrates this concept.</span></span>  
  
 <span data-ttu-id="75bf8-119">![Diagram balíčku a částí](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span><span class="sxs-lookup"><span data-stu-id="75bf8-119">![Package and Parts diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span></span>  
  
 <span data-ttu-id="75bf8-120">K identifikaci částí, specifikace OPC využívá rozšiřitelnosti RFC 2396 (identifikátory URI (Uniform Resource): Obecná syntaxe) můžete definovat sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma.</span><span class="sxs-lookup"><span data-stu-id="75bf8-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>  
  
 <span data-ttu-id="75bf8-121">Schéma, která je zadána [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je definována předponu jeho; souborů protokolu http, ftp a jsou známé příklady.</span><span class="sxs-lookup"><span data-stu-id="75bf8-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="75bf8-122">Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schéma používá "pack" jako jeho schéma a obsahuje dvě součásti: autority a cestu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="75bf8-123">Tady je formát pro sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 <span data-ttu-id="75bf8-124">Sada: / /*autority*/*cesta*</span><span class="sxs-lookup"><span data-stu-id="75bf8-124">pack://*authority*/*path*</span></span>
  
 <span data-ttu-id="75bf8-125">*Autority* Určuje typ balíčku, který je součástí obsažený v, zatímco *cesta* Určuje umístění součástí v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="75bf8-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>  
  
 <span data-ttu-id="75bf8-126">Tento koncept je zobrazená ve na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="75bf8-126">This concept is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="75bf8-127">![Vztah mezi balíčku, autority a cestu](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span><span class="sxs-lookup"><span data-stu-id="75bf8-127">![Relationship among package, authority, and path](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span></span>  
  
 <span data-ttu-id="75bf8-128">Jsou obdobou aplikací a souborů, kde aplikace (balíček) může obsahovat jeden nebo více souborů (části), včetně balíčků a částí:</span><span class="sxs-lookup"><span data-stu-id="75bf8-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>  
  
-   <span data-ttu-id="75bf8-129">Soubory prostředků, které jsou zkompilovány do místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-129">Resource files that are compiled into the local assembly.</span></span>  
  
-   <span data-ttu-id="75bf8-130">Soubory prostředků, které jsou zkompilovány do odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-130">Resource files that are compiled into a referenced assembly.</span></span>  
  
-   <span data-ttu-id="75bf8-131">Soubory prostředků, které jsou zkompilovány do odkazující sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-131">Resource files that are compiled into a referencing assembly.</span></span>  
  
-   <span data-ttu-id="75bf8-132">Soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-132">Content files.</span></span>  
  
-   <span data-ttu-id="75bf8-133">Lokalita počátek souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-133">Site of origin files.</span></span>  
  
 <span data-ttu-id="75bf8-134">Pro přístup k tyto typy souborů, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje dva autorit: aplikace: / / / a siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="75bf8-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="75bf8-135">Aplikace: / / / autority identifikuje datové soubory aplikace, které jsou známé při kompilaci, včetně prostředků a obsah souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="75bf8-136">Siteoforigin: / / / autority identifikuje lokalitu počátek souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="75bf8-137">Rozsah každý oprávnění je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="75bf8-137">The scope of each authority is shown in the following figure.</span></span>  
  
 <span data-ttu-id="75bf8-138">![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span><span class="sxs-lookup"><span data-stu-id="75bf8-138">![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75bf8-139">Komponenta autority sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] který body do balíčku a musí odpovídat RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="75bf8-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="75bf8-140">Kromě toho musí být nahrazen znakem "," znak "/" a vyhrazené znaky, jako je například "%" a "?", je nutné uvést.</span><span class="sxs-lookup"><span data-stu-id="75bf8-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="75bf8-141">V tématu OPC podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="75bf8-141">See the OPC for details.</span></span>  
  
 <span data-ttu-id="75bf8-142">Následující části popisují, jak vytvořit pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pomocí těchto dvou autority ve spojení s příslušné cesty k identifikaci prostředků, obsah a lokality počátek souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a><span data-ttu-id="75bf8-143">Identifikátory URI Pack souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="75bf8-143">Resource File Pack URIs</span></span>  
 <span data-ttu-id="75bf8-144">Soubory prostředků, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` položky a kompilované do sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="75bf8-145">podporuje vytváření sady [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] který lze použít k identifikaci soubory prostředků, které jsou buď zkompilovat do místní sestavení nebo zkompilovány do sestavení, které se odkazuje z místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-145"> supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a><span data-ttu-id="75bf8-146">Místní sestavení zdrojového souboru</span><span class="sxs-lookup"><span data-stu-id="75bf8-146">Local Assembly Resource File</span></span>  
 <span data-ttu-id="75bf8-147">Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prostředku soubor, který se zkompiluje do místní sestavení používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="75bf8-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="75bf8-148">**Autorita**: aplikace: / / /.</span><span class="sxs-lookup"><span data-stu-id="75bf8-148">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="75bf8-149">**Cesta**: název souboru prostředků, včetně jeho cesty relativní vůči kořenovému adresáři místní sestavení projektu složky.</span><span class="sxs-lookup"><span data-stu-id="75bf8-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>  
  
 <span data-ttu-id="75bf8-150">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru prostředků, který se nachází v kořenové složce místní sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="75bf8-151">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdrojového souboru, který je umístěný v podsložce složky místní sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="75bf8-152">Soubor prostředků odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-152">Referenced Assembly Resource File</span></span>  
 <span data-ttu-id="75bf8-153">Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prostředku soubor, který se zkompiluje do odkazované sestavení používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="75bf8-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="75bf8-154">**Autorita**: aplikace: / / /.</span><span class="sxs-lookup"><span data-stu-id="75bf8-154">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="75bf8-155">**Cesta**: název souboru prostředků, který se zkompiluje do odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="75bf8-156">Cesta musí splňovat následující formát:</span><span class="sxs-lookup"><span data-stu-id="75bf8-156">The path must conform to the following format:</span></span>  
  
     <span data-ttu-id="75bf8-157">*AssemblyShortName*{*; Verze*] {*; PublicKey*]; součásti nebo*cesta*</span><span class="sxs-lookup"><span data-stu-id="75bf8-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>  
  
    -   <span data-ttu-id="75bf8-158">**AssemblyShortName**: krátký název pro odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>  
  
    -   <span data-ttu-id="75bf8-159">**; Verze** [Nepovinné]: verze odkazované sestavení, která obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="75bf8-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="75bf8-160">To se používá, pokud dva nebo více odkazovaná sestavení se stejným názvem krátké jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="75bf8-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="75bf8-161">**; PublicKey** [Nepovinné]: veřejný klíč, který se použil k podepsání odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="75bf8-162">To se používá, pokud dva nebo více odkazovaná sestavení se stejným názvem krátké jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="75bf8-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="75bf8-163">**; součást**: Určuje, že odkazovaného sestavení odkazuje z místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>  
  
    -   <span data-ttu-id="75bf8-164">**Či cestu**: název souboru prostředků, včetně jeho cesty relativní vůči kořenovému adresáři složky odkazované sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>  
  
 <span data-ttu-id="75bf8-165">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru prostředků, který se nachází v kořenové složce projektu odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 <span data-ttu-id="75bf8-166">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zdrojového souboru, který je umístěný v podsložce složky odkazované sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 <span data-ttu-id="75bf8-167">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru prostředků, který se nachází v kořenové složce odkazované, specifické pro verzi sestavení projektu složky.</span><span class="sxs-lookup"><span data-stu-id="75bf8-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 <span data-ttu-id="75bf8-168">Všimněte si, že sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntaxe pro soubory prostředků odkazované sestavení může být použita pouze s aplikací: / / / autoritu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="75bf8-169">Například následující není podporována v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a><span data-ttu-id="75bf8-170">Identifikátory URI Pack souboru obsahu</span><span class="sxs-lookup"><span data-stu-id="75bf8-170">Content File Pack URIs</span></span>  
 <span data-ttu-id="75bf8-171">Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro soubor obsahu používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="75bf8-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="75bf8-172">**Autorita**: aplikace: / / /.</span><span class="sxs-lookup"><span data-stu-id="75bf8-172">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="75bf8-173">**Cesta**: název souboru obsahu, včetně jeho cesty relativní k umístění systému souboru hlavní spustitelný soubor sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="75bf8-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>  
  
 <span data-ttu-id="75bf8-174">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu soubor umístěný ve stejné složce jako spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 <span data-ttu-id="75bf8-175">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu soubor umístěný ve složce do podsložky, která je relativní vzhledem ke spustitelné sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="75bf8-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]<span data-ttu-id="75bf8-176">soubory obsahu nelze přesměrováni do.</span><span class="sxs-lookup"><span data-stu-id="75bf8-176"> content files cannot be navigated to.</span></span> <span data-ttu-id="75bf8-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schéma podporuje pouze navigaci na [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] soubory, které jsou umístěny v lokalitě původu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="75bf8-178">Lokality počátek Pack identifikátory URI</span><span class="sxs-lookup"><span data-stu-id="75bf8-178">Site of Origin Pack URIs</span></span>  
 <span data-ttu-id="75bf8-179">Sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro lokalitu původu souboru používá následující autority a cesta:</span><span class="sxs-lookup"><span data-stu-id="75bf8-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="75bf8-180">**Autorita**: siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="75bf8-180">**Authority**: siteoforigin:///.</span></span>  
  
-   <span data-ttu-id="75bf8-181">**Cesta**: název webu zdrojový soubor, včetně jeho cesty relativní k umístění, ze kterého se spuštění spustitelného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>  
  
 <span data-ttu-id="75bf8-182">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality zdrojový soubor, uložené v umístění, ze kterého se spouští spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 <span data-ttu-id="75bf8-183">Následující příklad ukazuje sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokality zdrojový soubor, uložené v podsložku, která je relativní k umístění, ze kterého se spouští spustitelný soubor sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="75bf8-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a><span data-ttu-id="75bf8-184">Stránkovací soubory</span><span class="sxs-lookup"><span data-stu-id="75bf8-184">Page Files</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="75bf8-185">soubory, které jsou nakonfigurované jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky kompilované do sestavení stejným způsobem jako soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="75bf8-185"> files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="75bf8-186">V důsledku toho [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky lze identifikovat pomocí pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="75bf8-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>  
  
 <span data-ttu-id="75bf8-187">Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které jsou běžně nakonfigurována jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` položky mají jednu z těchto jako kořenový element:</span><span class="sxs-lookup"><span data-stu-id="75bf8-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="75bf8-188">Absolutní vs. Identifikátory URI relativní Pack</span><span class="sxs-lookup"><span data-stu-id="75bf8-188">Absolute vs. Relative Pack URIs</span></span>  
 <span data-ttu-id="75bf8-189">Plně kvalifikovaný pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] obsahuje schéma, oprávnění a cestu, a bude považován za absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="75bf8-190">Jako zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy obvykle umožňují nastavit příslušné atributy s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], což zahrnuje pouze cestu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>  
  
 <span data-ttu-id="75bf8-191">Zvažte například následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] soubor prostředků v místním sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="75bf8-192">Sada pro relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] který odkazuje tento prostředek soubor bude následující.</span><span class="sxs-lookup"><span data-stu-id="75bf8-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="75bf8-193">Protože lokality počátek soubory nejsou přidružené sestavení, se může odkazovat pouze s absolutní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="75bf8-194">Ve výchozím nastavení sadu relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] považuje za relativní k umístění kód nebo kód, který obsahuje odkaz na.</span><span class="sxs-lookup"><span data-stu-id="75bf8-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="75bf8-195">Pokud se používá počáteční zpětné lomítko, ale relativního pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkaz se považovat za relativní vůči kořenovému adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="75bf8-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="75bf8-196">Zvažte například následující strukturu projektu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-196">For example, consider the following project structure.</span></span>  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 <span data-ttu-id="75bf8-197">Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazující *kořenové*\SubFolder\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `Page2.xaml`  
  
 <span data-ttu-id="75bf8-198">Pokud obsahuje Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazující *kořenové*\Page2.xaml, odkaz můžete použít následující relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a><span data-ttu-id="75bf8-199">Pack URI řešení</span><span class="sxs-lookup"><span data-stu-id="75bf8-199">Pack URI Resolution</span></span>  
 <span data-ttu-id="75bf8-200">Formát pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] díky je možné, pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro různé typy souborů, které vypadají stejně.</span><span class="sxs-lookup"><span data-stu-id="75bf8-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it is possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="75bf8-201">Zvažte například následující absolutní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="75bf8-202">Tato sada absolutní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] může odkazovat na soubor prostředků v místním sestavení nebo soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="75bf8-203">Totéž platí pro následující relativní [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="75bf8-204">Aby bylo možné zjistit typ souboru, který sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] přeloží [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pro soubory prostředků v místní sestavení a soubory obsahu pomocí heuristiky následující:</span><span class="sxs-lookup"><span data-stu-id="75bf8-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>  
  
1.  <span data-ttu-id="75bf8-205">Probe metadata sestavení <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut, který odpovídá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
2.  <span data-ttu-id="75bf8-206">Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nenajde, cesta sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>  
  
3.  <span data-ttu-id="75bf8-207">Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nebyl nalezen, probe soubory sadu prostředků, které jsou zkompilovány do místní sestavení.</span><span class="sxs-lookup"><span data-stu-id="75bf8-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>  
  
4.  <span data-ttu-id="75bf8-208">Pokud soubor prostředků, který odpovídá cesta sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] nenajde, cesta sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odkazuje na soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="75bf8-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>  
  
5.  <span data-ttu-id="75bf8-209">Pokud prostředek není nalezen, interně vytvořené <xref:System.Uri> je neplatný.</span><span class="sxs-lookup"><span data-stu-id="75bf8-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="75bf8-210">řešení se nevztahuje na [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , naleznete na následující:</span><span class="sxs-lookup"><span data-stu-id="75bf8-210"> resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>  
  
-   <span data-ttu-id="75bf8-211">Obsah souborů v odkazovaných sestaveních: nepodporuje tyto typy souborů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
-   <span data-ttu-id="75bf8-212">Vložené soubory v odkazovaných sestaveních: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , je identifikovat jsou jedinečné, protože obsahují název odkazovaného sestavení a `;component` příponu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>  
  
-   <span data-ttu-id="75bf8-213">Lokality původ souborů: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , je identifikovat jsou jedinečné, protože jsou pouze soubory, které lze identifikovat podle pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] obsahující siteoforigin: / / / autority.</span><span class="sxs-lookup"><span data-stu-id="75bf8-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>  
  
 <span data-ttu-id="75bf8-214">Jeden zápis, který pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] řešení umožňuje je pro kód být poněkud nezávislé na umístění prostředků a obsah souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="75bf8-215">Například, pokud máte soubor prostředků v místním sestavení, která je překonfigurovat tak, aby se soubor s obsahem, sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro prostředek zůstane stejný, stejně jako kód, který používá sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a><span data-ttu-id="75bf8-216">Programování s aktualizací Service Pack identifikátory URI</span><span class="sxs-lookup"><span data-stu-id="75bf8-216">Programming with Pack URIs</span></span>  
 <span data-ttu-id="75bf8-217">Mnoho [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] třídy implementovat vlastnosti, které lze nastavit s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], včetně:</span><span class="sxs-lookup"><span data-stu-id="75bf8-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="75bf8-218">Tyto vlastnosti můžete nastavit od značek a kódu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="75bf8-219">Tato část ukazuje základní konstrukce pro oba a poté zobrazí příklady běžné scénáře.</span><span class="sxs-lookup"><span data-stu-id="75bf8-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="75bf8-220">Použití Pack identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="75bf8-220">Using Pack URIs in Markup</span></span>  
 <span data-ttu-id="75bf8-221">Sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je určený ve značce nastavením elementu atributu balíček [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="75bf8-222">Příklad:</span><span class="sxs-lookup"><span data-stu-id="75bf8-222">For example:</span></span>  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 <span data-ttu-id="75bf8-223">Tabulka 1 ukazuje různé absolutní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="75bf8-224">Tabulka 1: Absolutní Pack identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="75bf8-224">Table 1: Absolute Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="75bf8-225">Soubor</span><span class="sxs-lookup"><span data-stu-id="75bf8-225">File</span></span>|<span data-ttu-id="75bf8-226">Absolutní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bf8-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="75bf8-227">Soubor prostředků - místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-228">Souboru prostředků v podsložce - místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-229">Soubor prostředků - odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-230">Souboru prostředků v podsložce odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-231">Soubor prostředků v verzí odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-232">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="75bf8-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|  
|<span data-ttu-id="75bf8-233">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="75bf8-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|<span data-ttu-id="75bf8-234">Lokality zdrojový soubor</span><span class="sxs-lookup"><span data-stu-id="75bf8-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|<span data-ttu-id="75bf8-235">Lokality zdrojového souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="75bf8-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 <span data-ttu-id="75bf8-236">Tabulka 2 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="75bf8-237">Tabulka 2: Pack relativní identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="75bf8-237">Table 2: Relative Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="75bf8-238">Soubor</span><span class="sxs-lookup"><span data-stu-id="75bf8-238">File</span></span>|<span data-ttu-id="75bf8-239">Relativní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bf8-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="75bf8-240">Soubor prostředků v místním sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-241">Souboru prostředků v podsložku místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-242">Soubor prostředků v odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-243">Souboru prostředků v podsložce odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="75bf8-244">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="75bf8-244">Content file</span></span>|`"/ContentFile.xaml"`|  
|<span data-ttu-id="75bf8-245">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="75bf8-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a><span data-ttu-id="75bf8-246">Použití Pack identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="75bf8-246">Using Pack URIs in Code</span></span>  
 <span data-ttu-id="75bf8-247">Zadejte sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] v kódu po vytvoření instance <xref:System.Uri> třídy a předání sada [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="75bf8-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="75bf8-248">To je patrné z následujícího příkladu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-248">This is demonstrated in the following example.</span></span>  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 <span data-ttu-id="75bf8-249">Ve výchozím nastavení <xref:System.Uri> třída zvažuje pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] na absolutní.</span><span class="sxs-lookup"><span data-stu-id="75bf8-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="75bf8-250">V důsledku toho je vyvolána výjimka, pokud instance <xref:System.Uri> třída je vytvořena s relativní pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75bf8-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 <span data-ttu-id="75bf8-251">Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení z <xref:System.Uri> konstruktoru třídy přijme parametr typu <xref:System.UriKind> umožňují určit, zda sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="75bf8-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 <span data-ttu-id="75bf8-252">Byste měli zadat jenom <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative> když jste si jisti, že zadaný pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] je jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="75bf8-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="75bf8-253">Pokud neznáte typ sady [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] používané, například když uživatel zadá sadu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] za běhu použít <xref:System.UriKind.RelativeOrAbsolute> místo.</span><span class="sxs-lookup"><span data-stu-id="75bf8-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 <span data-ttu-id="75bf8-254">Tabulka 3 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75bf8-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="75bf8-255">Tabulka 3: Absolutní Pack identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="75bf8-255">Table 3: Absolute Pack URIs in Code</span></span>  
  
|<span data-ttu-id="75bf8-256">Soubor</span><span class="sxs-lookup"><span data-stu-id="75bf8-256">File</span></span>|<span data-ttu-id="75bf8-257">Absolutní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bf8-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="75bf8-258">Soubor prostředků - místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-259">Souboru prostředků v podsložce - místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-260">Soubor prostředků - odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-261">Souboru prostředků v podsložce odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-262">Soubor prostředků v verzí odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-263">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="75bf8-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-264">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="75bf8-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-265">Lokality zdrojový soubor</span><span class="sxs-lookup"><span data-stu-id="75bf8-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="75bf8-266">Lokality zdrojového souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="75bf8-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 <span data-ttu-id="75bf8-267">Tabulka 4 ukazuje různé relativní pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75bf8-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="75bf8-268">Tabulka 4: Pack relativní identifikátory URI v kódu</span><span class="sxs-lookup"><span data-stu-id="75bf8-268">Table 4: Relative Pack URIs in Code</span></span>  
  
|<span data-ttu-id="75bf8-269">Soubor</span><span class="sxs-lookup"><span data-stu-id="75bf8-269">File</span></span>|<span data-ttu-id="75bf8-270">Relativní pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bf8-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="75bf8-271">Soubor prostředků - místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="75bf8-272">Souboru prostředků v podsložce - místní sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="75bf8-273">Soubor prostředků - odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="75bf8-274">Souboru prostředků v podsložce - odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="75bf8-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="75bf8-275">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="75bf8-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="75bf8-276">Obsah souboru do podsložky</span><span class="sxs-lookup"><span data-stu-id="75bf8-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="75bf8-277">Běžné scénáře URI Pack</span><span class="sxs-lookup"><span data-stu-id="75bf8-277">Common Pack URI Scenarios</span></span>  
 <span data-ttu-id="75bf8-278">V předchozích částech projednat konstruování pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] k identifikaci prostředků, obsah a lokality počátek souborů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="75bf8-279">V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], tyto konstrukce se používají v mnoha různými způsoby, a následující části se věnují několik běžných použití.</span><span class="sxs-lookup"><span data-stu-id="75bf8-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="75bf8-280">Zadání uživatelského rozhraní k zobrazení při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="75bf8-280">Specifying the UI to Show When an Application Starts</span></span>  
 <span data-ttu-id="75bf8-281"><xref:System.Windows.Application.StartupUri%2A>Určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zobrazíte, když [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="75bf8-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="75bf8-282">Pro samostatné aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být v časovém období, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 <span data-ttu-id="75bf8-283">Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] můžete na stránce také určit jako počáteční uživatelského rozhraní, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 <span data-ttu-id="75bf8-284">Pokud aplikace je samostatná aplikace, a na stránce je definován s <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otevře <xref:System.Windows.Navigation.NavigationWindow> k hostování stránky.</span><span class="sxs-lookup"><span data-stu-id="75bf8-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="75bf8-285">Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], stránka se zobrazí v prohlížeči hostitele.</span><span class="sxs-lookup"><span data-stu-id="75bf8-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a><span data-ttu-id="75bf8-286">Přejdete na stránku</span><span class="sxs-lookup"><span data-stu-id="75bf8-286">Navigating to a Page</span></span>  
 <span data-ttu-id="75bf8-287">Následující příklad ukazuje, jak přejděte na stránku.</span><span class="sxs-lookup"><span data-stu-id="75bf8-287">The following example shows how to navigate to a page.</span></span>  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 <span data-ttu-id="75bf8-288">Další informace o různých způsobech přejděte v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], najdete v části [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="75bf8-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a><span data-ttu-id="75bf8-289">Určení ikony okna</span><span class="sxs-lookup"><span data-stu-id="75bf8-289">Specifying a Window Icon</span></span>  
 <span data-ttu-id="75bf8-290">Následující příklad ukazuje, jak k používání identifikátoru URI k určení ikony časového období.</span><span class="sxs-lookup"><span data-stu-id="75bf8-290">The following example shows how to use a URI to specify a window's icon.</span></span>  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 <span data-ttu-id="75bf8-291">Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="75bf8-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="75bf8-292">Načítání bitové kopie, zvuk a Video soubory</span><span class="sxs-lookup"><span data-stu-id="75bf8-292">Loading Image, Audio, and Video Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="75bf8-293">umožňuje aplikacím používat celou řadu typů médií, které můžete identifikovat a načíst s aktualizací Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="75bf8-293"> allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 <span data-ttu-id="75bf8-294">Další informace o práci s obsahem média, najdete v části [grafika a multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="75bf8-294">For more information on working with media content, see [Graphics and Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span></span>  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="75bf8-295">Načítání slovník prostředků, a z webu původu</span><span class="sxs-lookup"><span data-stu-id="75bf8-295">Loading a Resource Dictionary from the Site of Origin</span></span>  
 <span data-ttu-id="75bf8-296">Slovnících prostředků (<xref:System.Windows.ResourceDictionary>) lze použít pro podporu aplikace motivů.</span><span class="sxs-lookup"><span data-stu-id="75bf8-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="75bf8-297">Jeden způsob, jak vytvořit a spravovat motivy je vytvoření víc motivů jako slovnících prostředků, které jsou umístěny v lokalitě aplikace původu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="75bf8-298">To umožňuje motivy přidat a aktualizovat bez nutnosti rekompilace a znovu nasazovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="75bf8-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="75bf8-299">Tyto slovnících prostředků je možné identifikovat a načíst pomocí pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], která je uvedena v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="75bf8-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 <span data-ttu-id="75bf8-300">Přehled motivy obsažené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], najdete v části [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="75bf8-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bf8-301">Viz také</span><span class="sxs-lookup"><span data-stu-id="75bf8-301">See Also</span></span>  
 [<span data-ttu-id="75bf8-302">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="75bf8-302">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
