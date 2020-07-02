---
title: Identifikátory URI Pack
description: Přečtěte si o mnoha způsobech použití identifikátorů URI (Uniform Resource Identifier) k identifikaci a načítání souborů v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 1d19dec0d846659f8de6ed518a7f98d224354a82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621688"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="fced4-103">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="fced4-103">Pack URIs in WPF</span></span>

<span data-ttu-id="fced4-104">V Windows Presentation Foundation (WPF) se k identifikaci a načítání souborů v mnoha různých způsobech používají identifikátory URI (Uniform Resource Identifier), včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="fced4-104">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="fced4-105">Určení, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] které se má zobrazit při prvním spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="fced4-105">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="fced4-106">Načítají se obrázky.</span><span class="sxs-lookup"><span data-stu-id="fced4-106">Loading images.</span></span>

- <span data-ttu-id="fced4-107">Navigace na stránky.</span><span class="sxs-lookup"><span data-stu-id="fced4-107">Navigating to pages.</span></span>

- <span data-ttu-id="fced4-108">Načítání nespustitelných datových souborů.</span><span class="sxs-lookup"><span data-stu-id="fced4-108">Loading non-executable data files.</span></span>

<span data-ttu-id="fced4-109">Identifikátory URI se navíc dají použít k identifikaci a načítání souborů z různých umístění, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="fced4-109">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="fced4-110">Aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-110">The current assembly.</span></span>

- <span data-ttu-id="fced4-111">Odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-111">A referenced assembly.</span></span>

- <span data-ttu-id="fced4-112">Umístění relativní k sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-112">A location relative to an assembly.</span></span>

- <span data-ttu-id="fced4-113">Původní lokalita aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-113">The application's site of origin.</span></span>

<span data-ttu-id="fced4-114">Pro zajištění konzistentního mechanismu pro identifikaci a načítání těchto typů souborů z těchto umístění WPF využívá rozšíření *schématu identifikátoru URI*.</span><span class="sxs-lookup"><span data-stu-id="fced4-114">To provide a consistent mechanism for identifying and loading these types of files from these locations, WPF leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="fced4-115">Toto téma obsahuje přehled schématu, popisuje, jak vytvořit identifikátory URI balíčku pro celou řadu scénářů, popisuje absolutní a relativní identifikátory URI a rozlišení identifikátoru URI před zobrazením způsobu použití identifikátorů URI balíčku z kódu a kódu.</span><span class="sxs-lookup"><span data-stu-id="fced4-115">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="fced4-116">Schéma identifikátoru URI balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-116">The Pack URI Scheme</span></span>

<span data-ttu-id="fced4-117">Schéma URI balíčku se používá ve specifikaci OPC ( [Open balení Conventions](https://www.ecma-international.org/publications/standards/Ecma-376.htm) ), která popisuje model pro organizování a identifikaci obsahu.</span><span class="sxs-lookup"><span data-stu-id="fced4-117">The pack URI scheme is used by the [Open Packaging Conventions](https://www.ecma-international.org/publications/standards/Ecma-376.htm) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="fced4-118">Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíček* je logický kontejner pro jednu nebo více logických *částí*.</span><span class="sxs-lookup"><span data-stu-id="fced4-118">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="fced4-119">Tento koncept znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="fced4-119">The following figure illustrates this concept.</span></span>

![Diagram balíčků a částí](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="fced4-121">Pro identifikaci částí používá specifikace OPC rozšiřitelnost RFC 2396 (Uniform resource identifiers (URI): Generic Syntax) k definování schématu identifikátoru URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-121">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="fced4-122">Schéma, které je určeno identifikátorem URI, je definováno jeho předponou; protokol HTTP, FTP a soubor jsou známé příklady.</span><span class="sxs-lookup"><span data-stu-id="fced4-122">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="fced4-123">Schéma identifikátoru URI balíčku používá jako své schéma "sadu" a obsahuje dvě komponenty: autorita a cesta.</span><span class="sxs-lookup"><span data-stu-id="fced4-123">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="fced4-124">Následuje formát pro identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-124">The following is the format for a pack URI.</span></span>

<span data-ttu-id="fced4-125">Cesta k*autoritě* / *path* Pack://</span><span class="sxs-lookup"><span data-stu-id="fced4-125">pack://*authority*/*path*</span></span>

<span data-ttu-id="fced4-126">*Autorita* určuje typ balíčku, který součást obsahuje, zatímco *cesta* určuje umístění součásti v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-126">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="fced4-127">Tento koncept je znázorněný na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="fced4-127">This concept is illustrated by the following figure:</span></span>

![Vztah mezi balíčkem, autoritou a cestou](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="fced4-129">Balíčky a části jsou analogické pro aplikace a soubory, kde aplikace (balíček) může obsahovat jeden nebo více souborů (částí), včetně:</span><span class="sxs-lookup"><span data-stu-id="fced4-129">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="fced4-130">Soubory prostředků, které jsou zkompilovány do místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-130">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="fced4-131">Soubory prostředků, které jsou zkompilovány do odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-131">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="fced4-132">Soubory prostředků, které jsou zkompilovány do odkazujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-132">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="fced4-133">Soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="fced4-133">Content files.</span></span>

- <span data-ttu-id="fced4-134">Lokalita se zdrojovými soubory.</span><span class="sxs-lookup"><span data-stu-id="fced4-134">Site of origin files.</span></span>

<span data-ttu-id="fced4-135">Pro přístup k těmto typům souborů podporuje WPF dva autority: application:///a siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="fced4-135">To access these types of files, WPF supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="fced4-136">Autorita application:///identifikuje datové soubory aplikace, které jsou známy v době kompilace, včetně souborů prostředků a obsahu.</span><span class="sxs-lookup"><span data-stu-id="fced4-136">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="fced4-137">Autorita siteoforigin:///identifikuje web se zdrojovými soubory.</span><span class="sxs-lookup"><span data-stu-id="fced4-137">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="fced4-138">Rozsah jednotlivých autorit je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="fced4-138">The scope of each authority is shown in the following figure.</span></span>

![Diagram identifikátoru URI balíčku](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="fced4-140">Součást autority identifikátoru URI balíčku je vložený identifikátor URI, který odkazuje na balíček a musí odpovídat specifikaci RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="fced4-140">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="fced4-141">Kromě toho musí být znak "/" nahrazen znakem "," a vyhrazené znaky, například "%" a "?" musí být uvozeny řídicím znakem.</span><span class="sxs-lookup"><span data-stu-id="fced4-141">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="fced4-142">Podrobnosti najdete v OPC.</span><span class="sxs-lookup"><span data-stu-id="fced4-142">See the OPC for details.</span></span>

<span data-ttu-id="fced4-143">V následujících částech se dozvíte, jak vytvořit identifikátory URI balíčků pomocí těchto dvou úřadů ve spojení s příslušnými cestami k identifikaci prostředků, obsahu a umístění původních souborů.</span><span class="sxs-lookup"><span data-stu-id="fced4-143">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="fced4-144">Identifikátory URI sad prostředků souboru</span><span class="sxs-lookup"><span data-stu-id="fced4-144">Resource File Pack URIs</span></span>

<span data-ttu-id="fced4-145">Soubory prostředků jsou nakonfigurovány jako `Resource` položky MSBuild a jsou zkompilovány do sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-145">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="fced4-146">WPF podporuje konstrukci identifikátorů URI balíčku, které lze použít k identifikaci souborů prostředků, které jsou zkompilovány do místního sestavení nebo zkompilovány do sestavení, které je odkazováno z místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-146">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="fced4-147">Soubor prostředků místního sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-147">Local Assembly Resource File</span></span>

<span data-ttu-id="fced4-148">Identifikátor URI balíčku pro soubor prostředků kompilovaný do místního sestavení používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="fced4-148">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="fced4-149">**Autorita**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="fced4-149">**Authority**: application:///.</span></span>

- <span data-ttu-id="fced4-150">**Cesta**: název souboru prostředků, včetně jeho cesty, relativní vzhledem k místnímu kořenu složky sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="fced4-150">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="fced4-151">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v kořenovém adresáři složky projektu místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="fced4-152">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v podsložce složky projektu místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-152">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="fced4-153">Odkazovaný soubor prostředků sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-153">Referenced Assembly Resource File</span></span>

<span data-ttu-id="fced4-154">Identifikátor URI balíčku pro soubor prostředků kompilovaný do odkazovaného sestavení používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="fced4-154">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="fced4-155">**Autorita**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="fced4-155">**Authority**: application:///.</span></span>

- <span data-ttu-id="fced4-156">**Cesta**: název souboru prostředků, který je zkompilován do odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-156">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="fced4-157">Cesta musí odpovídat následujícímu formátu:</span><span class="sxs-lookup"><span data-stu-id="fced4-157">The path must conform to the following format:</span></span>

  <span data-ttu-id="fced4-158">*AssemblyShortName*{*; Verze*] {*; PublicKey*]; součást/*cesta*</span><span class="sxs-lookup"><span data-stu-id="fced4-158">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="fced4-159">**AssemblyShortName**: krátký název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-159">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="fced4-160">**; Verze** [volitelné]: verze odkazovaného sestavení, které obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="fced4-160">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="fced4-161">To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.</span><span class="sxs-lookup"><span data-stu-id="fced4-161">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="fced4-162">**; PublicKey** [volitelné]: veřejný klíč, který se použil k podepsání odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-162">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="fced4-163">To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.</span><span class="sxs-lookup"><span data-stu-id="fced4-163">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="fced4-164">**; Component**: Určuje, zda je na odkazované sestavení odkazováno z místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-164">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="fced4-165">**/Path**: název souboru prostředků, včetně jeho cesty, vzhledem k kořenu složky projektu odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-165">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="fced4-166">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v kořenovém adresáři složky projektu odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="fced4-167">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v podsložce složky projektu odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="fced4-168">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v kořenové složce odkazované složky projektu pro specifické verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-168">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="fced4-169">Všimněte si, že syntaxe identifikátoru URI balíčku pro odkazované soubory prostředků sestavení se dá použít jenom s autoritou application:///.</span><span class="sxs-lookup"><span data-stu-id="fced4-169">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="fced4-170">Například následující příkaz není podporován v technologii WPF.</span><span class="sxs-lookup"><span data-stu-id="fced4-170">For example, the following is not supported in WPF.</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="fced4-171">Identifikátory URI sady souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="fced4-171">Content File Pack URIs</span></span>

<span data-ttu-id="fced4-172">Identifikátor URI balíčku pro soubor obsahu používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="fced4-172">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="fced4-173">**Autorita**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="fced4-173">**Authority**: application:///.</span></span>

- <span data-ttu-id="fced4-174">**Cesta**: název souboru obsahu, včetně jeho cesty relativního k umístění systému souborů v hlavním spustitelném sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-174">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="fced4-175">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor obsahu, který je umístěn ve stejné složce jako spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="fced4-176">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor obsahu umístěný v podsložce, která je relativní vzhledem k spustitelnému sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-176">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="fced4-177">Soubory obsahu HTML nelze přejít na.</span><span class="sxs-lookup"><span data-stu-id="fced4-177">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="fced4-178">Schéma identifikátoru URI podporuje pouze navigaci na soubory HTML, které jsou umístěny v lokalitě původu.</span><span class="sxs-lookup"><span data-stu-id="fced4-178">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="fced4-179">Server sad identifikátorů URI pro původní sadu</span><span class="sxs-lookup"><span data-stu-id="fced4-179">Site of Origin Pack URIs</span></span>

<span data-ttu-id="fced4-180">Identifikátor URI balíčku pro lokalitu zdrojového souboru používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="fced4-180">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="fced4-181">**Autorita**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="fced4-181">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="fced4-182">**Cesta**: název lokality zdrojového souboru, včetně cesty relativního k umístění, ze kterého se spustilo spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-182">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="fced4-183">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokalitu zdrojového souboru, uložený v umístění, ze kterého se spouští spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="fced4-184">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lokalitu zdrojového souboru, uložený v podsložce, která je relativní k umístění, ze kterého se spouští sestavení spustitelného objektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-184">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="fced4-185">Stránkovací soubory</span><span class="sxs-lookup"><span data-stu-id="fced4-185">Page Files</span></span>

<span data-ttu-id="fced4-186">Soubory XAML, které jsou konfigurovány jako položky MSBuild, `Page` jsou zkompilovány do sestavení stejným způsobem jako soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="fced4-186">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="fced4-187">V důsledku toho `Page` mohou být položky MSBuild identifikovány pomocí identifikátorů URI balíčků pro soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="fced4-187">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="fced4-188">Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů, které jsou běžně nakonfigurované jako položky MSBuild, `Page` mají jako svůj kořenový prvek jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="fced4-188">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="fced4-189">Absolutní identifikátory URI sady vs. relativní Pack</span><span class="sxs-lookup"><span data-stu-id="fced4-189">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="fced4-190">Plně kvalifikovaný identifikátor URI balíčku zahrnuje schéma, autoritu a cestu a je považován za absolutní identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-190">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="fced4-191">V rámci zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky obvykle umožňují nastavit odpovídající atributy s identifikátorem URI relativního balíčku, který obsahuje pouze cestu.</span><span class="sxs-lookup"><span data-stu-id="fced4-191">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="fced4-192">Zvažte například následující absolutní identifikátor URI balíčku pro soubor prostředků v místním sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-192">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="fced4-193">Identifikátor URI relativního balíčku, který se vztahuje k tomuto souboru prostředků, by byl následující.</span><span class="sxs-lookup"><span data-stu-id="fced4-193">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="fced4-194">Vzhledem k tomu, že lokalita původních souborů není přidružena k sestavením, mohou být pouze odkazována pouze pomocí absolutních identifikátorů URI Pack.</span><span class="sxs-lookup"><span data-stu-id="fced4-194">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="fced4-195">Ve výchozím nastavení se identifikátor URI relativního balíčku považuje za relativní k umístění značky nebo kódu, který obsahuje odkaz.</span><span class="sxs-lookup"><span data-stu-id="fced4-195">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="fced4-196">Pokud se použije počáteční zpětné lomítko, pak se odkaz na identifikátor URI relativního balíčku považuje za relativní ke kořenu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-196">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="fced4-197">Zvažte například následující strukturu projektu.</span><span class="sxs-lookup"><span data-stu-id="fced4-197">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="fced4-198">Pokud Page1. XAML obsahuje identifikátor URI, který odkazuje na *kořenový*\SubFolder\Page2.XAML, může odkaz použít následující identifikátor URI relativního balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-198">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="fced4-199">Pokud Page1. XAML obsahuje identifikátor URI, který odkazuje na *kořenový*\Page2.XAML, může odkaz použít následující identifikátor URI relativního balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-199">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="fced4-200">Rozlišení URI balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-200">Pack URI Resolution</span></span>

<span data-ttu-id="fced4-201">Formát identifikátorů URI Pack umožňuje, aby identifikátory URI balíčku pro různé typy souborů vypadaly stejně.</span><span class="sxs-lookup"><span data-stu-id="fced4-201">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="fced4-202">Zvažte například následující absolutní identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-202">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="fced4-203">Tento identifikátor URI absolutního balíčku může odkazovat buď na soubor prostředků v místním sestavení, nebo v souboru obsahu.</span><span class="sxs-lookup"><span data-stu-id="fced4-203">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="fced4-204">Totéž platí pro následující relativní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="fced4-204">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="fced4-205">Aby bylo možné určit typ souboru, na který odkazuje identifikátor URI balíčku, rozpozná WPF identifikátory URI pro soubory prostředků v místních sestavení a souborech obsahu pomocí následujících heuristik:</span><span class="sxs-lookup"><span data-stu-id="fced4-205">In order to determine the type of file that a pack URI refers to, WPF resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="fced4-206">Sondujte metadata sestavení pro <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut, který odpovídá identifikátoru URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-206">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="fced4-207">Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> je atribut nalezen, cesta k identifikátoru URI balíčku odkazuje na soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="fced4-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="fced4-208">Pokud <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atribut nebyl nalezen, proveďte test souborů prostředků sady, které jsou zkompilovány do místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fced4-208">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="fced4-209">Pokud je nalezen soubor prostředků odpovídající cestě k identifikátoru URI balíčku, cesta k identifikátoru URI balíčku odkazuje na soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="fced4-209">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="fced4-210">Pokud se prostředek nenajde, interně vytvořené pole <xref:System.Uri> je neplatné.</span><span class="sxs-lookup"><span data-stu-id="fced4-210">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="fced4-211">Rozlišení identifikátoru URI se nevztahuje na identifikátory URI, které odkazují na následující:</span><span class="sxs-lookup"><span data-stu-id="fced4-211">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="fced4-212">Soubory obsahu v odkazovaných sestaveních: tyto typy souborů rozhraní WPF nepodporují.</span><span class="sxs-lookup"><span data-stu-id="fced4-212">Content files in referenced assemblies: these file types are not supported by WPF.</span></span>

- <span data-ttu-id="fced4-213">Vložené soubory v odkazovaných sestaveních: identifikátory URI, které je identifikují, jsou jedinečné, protože zahrnují název odkazovaného sestavení a `;component` příponu.</span><span class="sxs-lookup"><span data-stu-id="fced4-213">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="fced4-214">Lokalita se zdrojovými soubory: identifikátory URI, které je identifikují, jsou jedinečné, protože se jedná o jediné soubory, které je možné identifikovat pomocí identifikátorů URI balíčků, které obsahují siteoforigin:///autoritu.</span><span class="sxs-lookup"><span data-stu-id="fced4-214">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="fced4-215">Jedno zjednodušení, které umožňuje rozlišení URI balíčku, je, že kód může být trochu nezávislý na umístění souborů prostředků a obsahu.</span><span class="sxs-lookup"><span data-stu-id="fced4-215">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="fced4-216">Například pokud máte soubor prostředků v lokálním sestavení, které je překonfigurováno na soubor obsahu, identifikátor URI balíčku pro prostředek zůstane stejný, jako kód, který používá identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-216">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="fced4-217">Programování s identifikátory URI balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-217">Programming with Pack URIs</span></span>

<span data-ttu-id="fced4-218">Mnoho tříd WPF implementuje vlastnosti, které lze nastavit pomocí identifikátorů URI Pack, včetně:</span><span class="sxs-lookup"><span data-stu-id="fced4-218">Many WPF classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="fced4-219">Tyto vlastnosti lze nastavit z kódu i kódu.</span><span class="sxs-lookup"><span data-stu-id="fced4-219">These properties can be set from both markup and code.</span></span> <span data-ttu-id="fced4-220">Tato část ukazuje základní konstrukce pro obojí a pak ukazuje příklady běžných scénářů.</span><span class="sxs-lookup"><span data-stu-id="fced4-220">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="fced4-221">Použití identifikátorů URI Pack v kódu</span><span class="sxs-lookup"><span data-stu-id="fced4-221">Using Pack URIs in Markup</span></span>

<span data-ttu-id="fced4-222">Identifikátor URI balíku je zadán v označení nastavením elementu atributu s identifikátorem URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-222">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="fced4-223">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fced4-223">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="fced4-224">Tabulka 1 znázorňuje různé identifikátory URI absolutních balíčků, které lze zadat v označení.</span><span class="sxs-lookup"><span data-stu-id="fced4-224">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="fced4-225">Tabulka 1: identifikátory URI absolutních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="fced4-225">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="fced4-226">Soubor</span><span class="sxs-lookup"><span data-stu-id="fced4-226">File</span></span>|<span data-ttu-id="fced4-227">Identifikátor URI absolutního balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-227">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="fced4-228">Místní sestavení souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="fced4-228">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-229">Soubor prostředků v sestavení místních podsložek</span><span class="sxs-lookup"><span data-stu-id="fced4-229">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-230">Soubor prostředků – odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-230">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-231">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-231">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-232">Soubor prostředků ve verzi odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-232">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-233">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="fced4-233">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="fced4-234">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="fced4-234">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="fced4-235">Lokalita zdrojového souboru</span><span class="sxs-lookup"><span data-stu-id="fced4-235">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="fced4-236">Lokalita zdrojového souboru v podsložce</span><span class="sxs-lookup"><span data-stu-id="fced4-236">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="fced4-237">Tabulka 2 znázorňuje různé identifikátory URI pro relativní balíčky, které lze zadat v označení.</span><span class="sxs-lookup"><span data-stu-id="fced4-237">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="fced4-238">Tabulka 2: identifikátory URI relativních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="fced4-238">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="fced4-239">Soubor</span><span class="sxs-lookup"><span data-stu-id="fced4-239">File</span></span>|<span data-ttu-id="fced4-240">Identifikátor URI relativního balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-240">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="fced4-241">Soubor prostředků v místním sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-241">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-242">Soubor prostředků v podsložce místního sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-242">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-243">Soubor prostředků v odkazovaném sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-243">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-244">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-244">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="fced4-245">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="fced4-245">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="fced4-246">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="fced4-246">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="fced4-247">Použití identifikátorů URI Pack v kódu</span><span class="sxs-lookup"><span data-stu-id="fced4-247">Using Pack URIs in Code</span></span>

<span data-ttu-id="fced4-248">Identifikátor URI balíčku zadáte v kódu vytvořením instance <xref:System.Uri> třídy a předáním identifikátoru URI balíčku jako parametru konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="fced4-248">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="fced4-249">To je patrné z následujícího příkladu.</span><span class="sxs-lookup"><span data-stu-id="fced4-249">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="fced4-250">Ve výchozím nastavení <xref:System.Uri> Třída považuje identifikátory URI balíčku za absolutní.</span><span class="sxs-lookup"><span data-stu-id="fced4-250">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="fced4-251">V důsledku toho je vyvolána výjimka, když <xref:System.Uri> je vytvořena instance třídy s identifikátorem URI relativního balíčku.</span><span class="sxs-lookup"><span data-stu-id="fced4-251">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="fced4-252">Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení <xref:System.Uri> konstruktoru třídy přijímá parametr typu, který umožňuje <xref:System.UriKind> určit, zda je identifikátor URI balíčku buď absolutní, nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="fced4-252">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="fced4-253">Měli byste zadat jenom <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative> , pokud jste si jisti, že poskytnutý identifikátor URI Pack je jeden nebo druhý.</span><span class="sxs-lookup"><span data-stu-id="fced4-253">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="fced4-254">Pokud neznáte typ identifikátoru URI balíčku, který se používá, například když uživatel zadá v době běhu identifikátor URI balíčku, použijte <xref:System.UriKind.RelativeOrAbsolute> místo toho.</span><span class="sxs-lookup"><span data-stu-id="fced4-254">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="fced4-255">Tabulka 3 znázorňuje různé identifikátory URI relativních balíčků, které můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fced4-255">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fced4-256">Tabulka 3: identifikátory URI absolutních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="fced4-256">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="fced4-257">Soubor</span><span class="sxs-lookup"><span data-stu-id="fced4-257">File</span></span>|<span data-ttu-id="fced4-258">Identifikátor URI absolutního balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-258">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="fced4-259">Místní sestavení souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="fced4-259">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-260">Soubor prostředků v sestavení místních podsložek</span><span class="sxs-lookup"><span data-stu-id="fced4-260">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-261">Soubor prostředků – odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-261">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-262">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-262">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-263">Soubor prostředků ve verzi odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-263">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-264">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="fced4-264">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-265">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="fced4-265">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-266">Lokalita zdrojového souboru</span><span class="sxs-lookup"><span data-stu-id="fced4-266">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="fced4-267">Lokalita zdrojového souboru v podsložce</span><span class="sxs-lookup"><span data-stu-id="fced4-267">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="fced4-268">Tabulka 4 znázorňuje různé identifikátory URI pro relativní balíčky, které můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fced4-268">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fced4-269">Tabulka 4: identifikátory URI relativních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="fced4-269">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="fced4-270">Soubor</span><span class="sxs-lookup"><span data-stu-id="fced4-270">File</span></span>|<span data-ttu-id="fced4-271">Identifikátor URI relativního balíčku</span><span class="sxs-lookup"><span data-stu-id="fced4-271">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="fced4-272">Místní sestavení souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="fced4-272">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="fced4-273">Soubor prostředků v sestavení místních podsložek</span><span class="sxs-lookup"><span data-stu-id="fced4-273">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="fced4-274">Soubor prostředků – odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="fced4-274">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="fced4-275">Soubor prostředků v sestavení odkazovaném podsložkou</span><span class="sxs-lookup"><span data-stu-id="fced4-275">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="fced4-276">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="fced4-276">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="fced4-277">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="fced4-277">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="fced4-278">Scénáře identifikátoru URI pro Common Pack</span><span class="sxs-lookup"><span data-stu-id="fced4-278">Common Pack URI Scenarios</span></span>

<span data-ttu-id="fced4-279">V předchozích částech byly popsány postupy sestavení identifikátorů URI pro identifikaci prostředků, obsahu a umístění původních souborů.</span><span class="sxs-lookup"><span data-stu-id="fced4-279">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="fced4-280">V rámci WPF jsou tyto konstrukce používány různými způsoby a následující oddíly obsahují několik běžných použití.</span><span class="sxs-lookup"><span data-stu-id="fced4-280">In WPF, these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="fced4-281">Určení uživatelského rozhraní, které se zobrazí při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="fced4-281">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="fced4-282"><xref:System.Windows.Application.StartupUri%2A>Určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který se má zobrazit při spuštění aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="fced4-282"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a WPF application is launched.</span></span> <span data-ttu-id="fced4-283">Pro samostatné aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] může být okno, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fced4-283">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="fced4-284">Samostatné aplikace a aplikace prohlížeče XAML (XBAP) mohou také určit stránku jako počáteční uživatelské rozhraní, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fced4-284">Standalone applications and XAML browser applications (XBAPs) can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="fced4-285">Pokud je aplikace samostatnou aplikací a je určena Stránka s nástrojem <xref:System.Windows.Application.StartupUri%2A> , WPF otevře <xref:System.Windows.Navigation.NavigationWindow> pro hostování stránky.</span><span class="sxs-lookup"><span data-stu-id="fced4-285">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, WPF opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="fced4-286">Pro XBAP se stránka zobrazuje v prohlížeči hostitele.</span><span class="sxs-lookup"><span data-stu-id="fced4-286">For XBAPs, the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="fced4-287">Navigace na stránku</span><span class="sxs-lookup"><span data-stu-id="fced4-287">Navigating to a Page</span></span>

<span data-ttu-id="fced4-288">Následující příklad ukazuje, jak přejít na stránku.</span><span class="sxs-lookup"><span data-stu-id="fced4-288">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="fced4-289">Další informace o různých způsobech navigace v WPF naleznete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fced4-289">For more information on the various ways to navigate in WPF, see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="fced4-290">Určení ikony okna</span><span class="sxs-lookup"><span data-stu-id="fced4-290">Specifying a Window Icon</span></span>

<span data-ttu-id="fced4-291">Následující příklad ukazuje, jak použít identifikátor URI k určení ikony okna.</span><span class="sxs-lookup"><span data-stu-id="fced4-291">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="fced4-292">Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="fced4-292">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="fced4-293">Načítání obrázků, zvukových souborů a videosouborů</span><span class="sxs-lookup"><span data-stu-id="fced4-293">Loading Image, Audio, and Video Files</span></span>

<span data-ttu-id="fced4-294">WPF umožňuje aplikacím využívat širokou škálu typů médií, které je možné identifikovat a načíst pomocí identifikátorů URI Pack, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="fced4-294">WPF allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="fced4-295">Další informace o práci s mediálním obsahem najdete v tématu [grafika a multimédia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="fced4-295">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="fced4-296">Načítání slovníku prostředků z lokality původu</span><span class="sxs-lookup"><span data-stu-id="fced4-296">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="fced4-297">Slovníky prostředků ( <xref:System.Windows.ResourceDictionary> ) lze použít k podpoře motivů aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-297">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="fced4-298">Jedním ze způsobů, jak vytvářet a spravovat motivy, je vytvořit několik motivů jako slovníky prostředků nacházející se v lokalitě aplikace, kde je původ.</span><span class="sxs-lookup"><span data-stu-id="fced4-298">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="fced4-299">To umožňuje přidat a aktualizovat motivy bez nutnosti opětovné kompilace a opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="fced4-299">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="fced4-300">Tyto slovníky prostředků je možné identifikovat a načíst pomocí identifikátorů URI Pack, který je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fced4-300">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="fced4-301">Přehled motivů v WPF naleznete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fced4-301">For an overview of themes in WPF, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fced4-302">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fced4-302">See also</span></span>

- [<span data-ttu-id="fced4-303">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="fced4-303">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
