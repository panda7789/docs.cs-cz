---
title: Identifikátory URI Pack
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 0fec72bdedbcc2c84d8bc65e72391366e42d82be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739162"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="ca6fe-102">Sbalení URI v technologii WPF</span><span class="sxs-lookup"><span data-stu-id="ca6fe-102">Pack URIs in WPF</span></span>

<span data-ttu-id="ca6fe-103">V Windows Presentation Foundation (WPF) se k identifikaci a načítání souborů v mnoha různých způsobech používají identifikátory URI (Uniform Resource Identifier), včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-103">In Windows Presentation Foundation (WPF), uniform resource identifiers (URIs) are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="ca6fe-104">Určení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], který se má zobrazit při prvním spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ca6fe-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="ca6fe-105">Načítají se obrázky.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-105">Loading images.</span></span>

- <span data-ttu-id="ca6fe-106">Navigace na stránky.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-106">Navigating to pages.</span></span>

- <span data-ttu-id="ca6fe-107">Načítání nespustitelných datových souborů.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-107">Loading non-executable data files.</span></span>

<span data-ttu-id="ca6fe-108">Identifikátory URI se navíc dají použít k identifikaci a načítání souborů z různých umístění, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-108">Furthermore, URIs can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="ca6fe-109">Aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-109">The current assembly.</span></span>

- <span data-ttu-id="ca6fe-110">Odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-110">A referenced assembly.</span></span>

- <span data-ttu-id="ca6fe-111">Umístění relativní k sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="ca6fe-112">Původní lokalita aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-112">The application's site of origin.</span></span>

<span data-ttu-id="ca6fe-113">Pro zajištění konzistentního mechanismu pro identifikaci a načítání těchto typů souborů z těchto umístění WPF využívá rozšíření *schématu identifikátoru URI*.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, WPF leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="ca6fe-114">Toto téma obsahuje přehled schématu, popisuje, jak vytvořit identifikátory URI balíčku pro celou řadu scénářů, popisuje absolutní a relativní identifikátory URI a rozlišení identifikátoru URI před zobrazením způsobu použití identifikátorů URI balíčku z kódu a kódu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-114">This topic provides an overview of the scheme, covers how to construct pack URIs for a variety of scenarios, discusses absolute and relative URIs and URI resolution, before showing how to use pack URIs from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="ca6fe-115">Schéma identifikátoru URI balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-115">The Pack URI Scheme</span></span>

<span data-ttu-id="ca6fe-116">Schéma URI balíčku se používá ve specifikaci OPC ( [Open balení Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) ), která popisuje model pro organizování a identifikaci obsahu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-116">The pack URI scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="ca6fe-117">Klíčové prvky tohoto modelu jsou balíčky a části, kde *balíček* je logický kontejner pro jednu nebo více logických *částí*.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="ca6fe-118">Tento koncept znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-118">The following figure illustrates this concept.</span></span>

![Diagram balíčků a částí](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="ca6fe-120">Pro identifikaci částí používá specifikace OPC rozšiřitelnost RFC 2396 (Uniform resource identifiers (URI): Generic Syntax) k definování schématu identifikátoru URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack URI scheme.</span></span>

<span data-ttu-id="ca6fe-121">Schéma, které je určeno identifikátorem URI, je definováno jeho předponou; protokol HTTP, FTP a soubor jsou známé příklady.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-121">The scheme that is specified by a URI is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="ca6fe-122">Schéma identifikátoru URI balíčku používá jako své schéma "sadu" a obsahuje dvě komponenty: autorita a cesta.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-122">The pack URI scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="ca6fe-123">Následuje formát pro identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-123">The following is the format for a pack URI.</span></span>

<span data-ttu-id="ca6fe-124">*cesta*/*autority* Pack://</span><span class="sxs-lookup"><span data-stu-id="ca6fe-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="ca6fe-125">*Autorita* určuje typ balíčku, který součást obsahuje, zatímco *cesta* určuje umístění součásti v rámci balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="ca6fe-126">Tento koncept je znázorněný na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-126">This concept is illustrated by the following figure:</span></span>

![Vztah mezi balíčkem, autoritou a cestou](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="ca6fe-128">Balíčky a části jsou analogické pro aplikace a soubory, kde aplikace (balíček) může obsahovat jeden nebo více souborů (částí), včetně:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="ca6fe-129">Soubory prostředků, které jsou zkompilovány do místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="ca6fe-130">Soubory prostředků, které jsou zkompilovány do odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="ca6fe-131">Soubory prostředků, které jsou zkompilovány do odkazujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="ca6fe-132">Soubory obsahu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-132">Content files.</span></span>

- <span data-ttu-id="ca6fe-133">Lokalita se zdrojovými soubory.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-133">Site of origin files.</span></span>

<span data-ttu-id="ca6fe-134">Pro přístup k těmto typům souborů podporuje WPF dva autority: application:///a siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-134">To access these types of files, WPF supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="ca6fe-135">Autorita application:///identifikuje datové soubory aplikace, které jsou známy v době kompilace, včetně souborů prostředků a obsahu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="ca6fe-136">Autorita siteoforigin:///identifikuje web se zdrojovými soubory.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="ca6fe-137">Rozsah jednotlivých autorit je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-137">The scope of each authority is shown in the following figure.</span></span>

![Diagram identifikátoru URI balíčku](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="ca6fe-139">Součást autority identifikátoru URI balíčku je vložený identifikátor URI, který odkazuje na balíček a musí odpovídat specifikaci RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-139">The authority component of a pack URI is an embedded URI that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="ca6fe-140">Kromě toho musí být znak "/" nahrazen znakem "," a vyhrazené znaky, například "%" a "?" musí být uvozeny řídicím znakem.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="ca6fe-141">Podrobnosti najdete v OPC.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-141">See the OPC for details.</span></span>

<span data-ttu-id="ca6fe-142">V následujících částech se dozvíte, jak vytvořit identifikátory URI balíčků pomocí těchto dvou úřadů ve spojení s příslušnými cestami k identifikaci prostředků, obsahu a umístění původních souborů.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-142">The following sections explain how to construct pack URIs using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="ca6fe-143">Identifikátory URI sad prostředků souboru</span><span class="sxs-lookup"><span data-stu-id="ca6fe-143">Resource File Pack URIs</span></span>

<span data-ttu-id="ca6fe-144">Soubory prostředků jsou nakonfigurovány jako MSBuild `Resource` položky a jsou zkompilovány do sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="ca6fe-145">WPF podporuje konstrukci identifikátorů URI balíčku, které lze použít k identifikaci souborů prostředků, které jsou zkompilovány do místního sestavení nebo zkompilovány do sestavení, které je odkazováno z místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="ca6fe-146">Soubor prostředků místního sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-146">Local Assembly Resource File</span></span>

<span data-ttu-id="ca6fe-147">Identifikátor URI balíčku pro soubor prostředků kompilovaný do místního sestavení používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-147">The pack URI for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="ca6fe-148">**Autorita**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="ca6fe-149">**Cesta**: název souboru prostředků, včetně jeho cesty, relativní vzhledem k místnímu kořenu složky sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="ca6fe-150">Následující příklad ukazuje identifikátor URI balíčku pro soubor prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který je umístěn v kořenovém adresáři složky projektu místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-150">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="ca6fe-151">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v podsložce složky projektu místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-151">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="ca6fe-152">Odkazovaný soubor prostředků sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="ca6fe-153">Identifikátor URI balíčku pro soubor prostředků kompilovaný do odkazovaného sestavení používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-153">The pack URI for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="ca6fe-154">**Autorita**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="ca6fe-155">**Cesta**: název souboru prostředků, který je zkompilován do odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="ca6fe-156">Cesta musí odpovídat následujícímu formátu:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="ca6fe-157">*AssemblyShortName*{ *; Verze*] { *; PublicKey*]; součást/*cesta*</span><span class="sxs-lookup"><span data-stu-id="ca6fe-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="ca6fe-158">**AssemblyShortName**: krátký název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="ca6fe-159">**; Verze** [volitelné]: verze odkazovaného sestavení, které obsahuje soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="ca6fe-160">To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="ca6fe-161">**; PublicKey** [volitelné]: veřejný klíč, který se použil k podepsání odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="ca6fe-162">To se používá, když jsou načtena dvě nebo více odkazovaných sestavení se stejným krátkým názvem.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="ca6fe-163">**; Component**: Určuje, zda je na odkazované sestavení odkazováno z místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="ca6fe-164">**/Path**: název souboru prostředků, včetně jeho cesty, vzhledem k kořenu složky projektu odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="ca6fe-165">Následující příklad ukazuje identifikátor URI balíčku pro soubor prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který je umístěn v kořenovém adresáři složky projektu odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-165">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="ca6fe-166">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor prostředků, který je umístěn v podsložce složky projektu odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-166">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="ca6fe-167">Následující příklad ukazuje identifikátor URI balíčku pro soubor prostředků [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], který je umístěn v kořenové složce odkazované složky projektu pro specifické verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-167">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="ca6fe-168">Všimněte si, že syntaxe identifikátoru URI balíčku pro odkazované soubory prostředků sestavení se dá použít jenom s autoritou application:///.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-168">Note that the pack URI syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="ca6fe-169">Například následující příkaz není podporován v technologii WPF.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-169">For example, the following is not supported in WPF.</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="ca6fe-170">Identifikátory URI sady souborů obsahu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-170">Content File Pack URIs</span></span>

<span data-ttu-id="ca6fe-171">Identifikátor URI balíčku pro soubor obsahu používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-171">The pack URI for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="ca6fe-172">**Autorita**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="ca6fe-173">**Cesta**: název souboru obsahu, včetně jeho cesty relativního k umístění systému souborů v hlavním spustitelném sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="ca6fe-174">Následující příklad ukazuje identifikátor URI balíčku pro soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu umístěný ve stejné složce jako spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-174">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="ca6fe-175">Následující příklad ukazuje identifikátor URI balíčku pro soubor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahu umístěný v podsložce, která je relativní vzhledem k spustitelnému sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-175">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="ca6fe-176">Soubory obsahu HTML nelze přejít na.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="ca6fe-177">Schéma identifikátoru URI podporuje pouze navigaci na soubory HTML, které jsou umístěny v lokalitě původu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-177">The URI scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="ca6fe-178">Server sad identifikátorů URI pro původní sadu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="ca6fe-179">Identifikátor URI balíčku pro lokalitu zdrojového souboru používá následující autoritu a cestu:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-179">The pack URI for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="ca6fe-180">**Autorita**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="ca6fe-181">**Cesta**: název lokality zdrojového souboru, včetně cesty relativního k umístění, ze kterého se spustilo spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="ca6fe-182">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] web zdrojového souboru uložený v umístění, ze kterého se spouští spustitelné sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-182">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="ca6fe-183">Následující příklad ukazuje identifikátor URI balíčku pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] web zdrojového souboru, uložený v podsložce, která je relativní k umístění, ze kterého se spouští sestavení spustitelného souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-183">The following example shows the pack URI for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="ca6fe-184">Stránkovací soubory</span><span class="sxs-lookup"><span data-stu-id="ca6fe-184">Page Files</span></span>

<span data-ttu-id="ca6fe-185">Soubory XAML, které jsou konfigurovány jako MSBuild `Page` položky, jsou zkompilovány do sestavení stejným způsobem jako soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="ca6fe-186">V důsledku toho mohou být MSBuild `Page` položky identifikovány pomocí identifikátorů URI Pack pro soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="ca6fe-187">Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů, které jsou běžně nakonfigurované jako MSBuild`Page` položky, mají jako svůj kořenový prvek jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="ca6fe-188">Absolutní identifikátory URI sady vs. relativní Pack</span><span class="sxs-lookup"><span data-stu-id="ca6fe-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="ca6fe-189">Plně kvalifikovaný identifikátor URI balíčku zahrnuje schéma, autoritu a cestu a je považován za absolutní identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-189">A fully qualified pack URI includes the scheme, the authority, and the path, and it is considered an absolute pack URI.</span></span> <span data-ttu-id="ca6fe-190">V rámci zjednodušení pro vývojáře [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky obvykle umožňují nastavit příslušné atributy s identifikátorem URI relativního balíčku, který obsahuje pouze cestu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack URI, which includes only the path.</span></span>

<span data-ttu-id="ca6fe-191">Zvažte například následující absolutní identifikátor URI balíčku pro soubor prostředků v místním sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-191">For example, consider the following absolute pack URI for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="ca6fe-192">Identifikátor URI relativního balíčku, který se vztahuje k tomuto souboru prostředků, by byl následující.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-192">The relative pack URI that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="ca6fe-193">Vzhledem k tomu, že lokalita původních souborů není přidružena k sestavením, mohou být pouze odkazována pouze pomocí absolutních identifikátorů URI Pack.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack URIs.</span></span>

<span data-ttu-id="ca6fe-194">Ve výchozím nastavení se identifikátor URI relativního balíčku považuje za relativní k umístění značky nebo kódu, který obsahuje odkaz.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-194">By default, a relative pack URI is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="ca6fe-195">Pokud se použije počáteční zpětné lomítko, pak se odkaz na identifikátor URI relativního balíčku považuje za relativní ke kořenu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-195">If a leading backslash is used, however, the relative pack URI reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="ca6fe-196">Zvažte například následující strukturu projektu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="ca6fe-197">Pokud Page1. XAML obsahuje identifikátor URI, který odkazuje na *kořenový*\SubFolder\Page2.XAML, může odkaz použít následující identifikátor URI relativního balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-197">If Page1.xaml contains a URI that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`Page2.xaml`

<span data-ttu-id="ca6fe-198">Pokud Page1. XAML obsahuje identifikátor URI, který odkazuje na *kořenový*\Page2.XAML, může odkaz použít následující identifikátor URI relativního balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-198">If Page1.xaml contains a URI that references *Root*\Page2.xaml, the reference can use the following relative pack URI.</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="ca6fe-199">Rozlišení URI balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-199">Pack URI Resolution</span></span>

<span data-ttu-id="ca6fe-200">Formát identifikátorů URI Pack umožňuje, aby identifikátory URI balíčku pro různé typy souborů vypadaly stejně.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-200">The format of pack URIs makes it possible for pack URIs for different types of files to look the same.</span></span> <span data-ttu-id="ca6fe-201">Zvažte například následující absolutní identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-201">For example, consider the following absolute pack URI.</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="ca6fe-202">Tento identifikátor URI absolutního balíčku může odkazovat buď na soubor prostředků v místním sestavení, nebo v souboru obsahu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-202">This absolute pack URI could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="ca6fe-203">Totéž platí pro následující relativní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-203">The same is true for the following relative URI.</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="ca6fe-204">Aby bylo možné určit typ souboru, na který odkazuje identifikátor URI balíčku, rozpozná WPF identifikátory URI pro soubory prostředků v místních sestavení a souborech obsahu pomocí následujících heuristik:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-204">In order to determine the type of file that a pack URI refers to, WPF resolves URIs for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="ca6fe-205">Sondujte metadata sestavení pro atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, který se shoduje s identifikátorem URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack URI.</span></span>

2. <span data-ttu-id="ca6fe-206">Pokud je nalezen atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, cesta k identifikátoru URI balíčku odkazuje na soubor obsahu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack URI refers to a content file.</span></span>

3. <span data-ttu-id="ca6fe-207">Pokud atribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> nebyl nalezen, proveďte test souborů prostředků sady, které jsou zkompilovány do místního sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="ca6fe-208">Pokud je nalezen soubor prostředků odpovídající cestě k identifikátoru URI balíčku, cesta k identifikátoru URI balíčku odkazuje na soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-208">If a resource file that matches the path of the pack URI is found, the path of the pack URI refers to a resource file.</span></span>

5. <span data-ttu-id="ca6fe-209">Pokud se prostředek nenajde, interně vytvořené <xref:System.Uri> je neplatné.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

<span data-ttu-id="ca6fe-210">Rozlišení identifikátoru URI se nevztahuje na identifikátory URI, které odkazují na následující:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-210">URI resolution does not apply for URIs that refer to the following:</span></span>

- <span data-ttu-id="ca6fe-211">Soubory obsahu v odkazovaných sestaveních: tyto typy souborů rozhraní WPF nepodporují.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-211">Content files in referenced assemblies: these file types are not supported by WPF.</span></span>

- <span data-ttu-id="ca6fe-212">Vložené soubory v odkazovaných sestaveních: identifikátory URI, které je identifikují, jsou jedinečné, protože zahrnují název odkazovaného sestavení a příponu `;component`.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-212">Embedded files in referenced assemblies: URIs that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="ca6fe-213">Lokalita se zdrojovými soubory: identifikátory URI, které je identifikují, jsou jedinečné, protože se jedná o jediné soubory, které je možné identifikovat pomocí identifikátorů URI balíčků, které obsahují siteoforigin:///autoritu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-213">Site of origin files: URIs that identify them are unique because they are the only files that can be identified by pack URIs that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="ca6fe-214">Jedno zjednodušení, které umožňuje rozlišení URI balíčku, je, že kód může být trochu nezávislý na umístění souborů prostředků a obsahu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-214">One simplification that pack URI resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="ca6fe-215">Například pokud máte soubor prostředků v lokálním sestavení, které je překonfigurováno na soubor obsahu, identifikátor URI balíčku pro prostředek zůstane stejný, jako kód, který používá identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack URI for the resource remains the same, as does the code that uses the pack URI.</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="ca6fe-216">Programování s identifikátory URI balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-216">Programming with Pack URIs</span></span>

<span data-ttu-id="ca6fe-217">Mnoho tříd WPF implementuje vlastnosti, které lze nastavit pomocí identifikátorů URI Pack, včetně:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-217">Many WPF classes implement properties that can be set with pack URIs, including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="ca6fe-218">Tyto vlastnosti lze nastavit z kódu i kódu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="ca6fe-219">Tato část ukazuje základní konstrukce pro obojí a pak ukazuje příklady běžných scénářů.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="ca6fe-220">Použití identifikátorů URI Pack v kódu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="ca6fe-221">Identifikátor URI balíku je zadán v označení nastavením elementu atributu s identifikátorem URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-221">A pack URI is specified in markup by setting the element of an attribute with the pack URI.</span></span> <span data-ttu-id="ca6fe-222">Například:</span><span class="sxs-lookup"><span data-stu-id="ca6fe-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="ca6fe-223">Tabulka 1 znázorňuje různé identifikátory URI absolutních balíčků, které lze zadat v označení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-223">Table 1 illustrates the various absolute pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="ca6fe-224">Tabulka 1: identifikátory URI absolutních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="ca6fe-225">File</span><span class="sxs-lookup"><span data-stu-id="ca6fe-225">File</span></span>|<span data-ttu-id="ca6fe-226">Identifikátor URI absolutního balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-226">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ca6fe-227">Místní sestavení souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="ca6fe-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-228">Soubor prostředků v sestavení místních podsložek</span><span class="sxs-lookup"><span data-stu-id="ca6fe-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-229">Soubor prostředků – odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-230">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-231">Soubor prostředků ve verzi odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-232">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="ca6fe-233">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="ca6fe-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="ca6fe-234">Lokalita zdrojového souboru</span><span class="sxs-lookup"><span data-stu-id="ca6fe-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="ca6fe-235">Lokalita zdrojového souboru v podsložce</span><span class="sxs-lookup"><span data-stu-id="ca6fe-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="ca6fe-236">Tabulka 2 znázorňuje různé identifikátory URI pro relativní balíčky, které lze zadat v označení.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-236">Table 2 illustrates the various relative pack URIs that you can specify in markup.</span></span>

<span data-ttu-id="ca6fe-237">Tabulka 2: identifikátory URI relativních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="ca6fe-238">File</span><span class="sxs-lookup"><span data-stu-id="ca6fe-238">File</span></span>|<span data-ttu-id="ca6fe-239">Identifikátor URI relativního balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-239">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ca6fe-240">Soubor prostředků v místním sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-241">Soubor prostředků v podsložce místního sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-242">Soubor prostředků v odkazovaném sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-243">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="ca6fe-244">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="ca6fe-245">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="ca6fe-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="ca6fe-246">Použití identifikátorů URI Pack v kódu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="ca6fe-247">Identifikátor URI balíčku zadáte v kódu vytvořením instance třídy <xref:System.Uri> a předáním identifikátoru URI balíčku jako parametru konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-247">You specify a pack URI in code by instantiating the <xref:System.Uri> class and passing the pack URI as a parameter to the constructor.</span></span> <span data-ttu-id="ca6fe-248">To je patrné z následujícího příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="ca6fe-249">Ve výchozím nastavení třída <xref:System.Uri> považuje identifikátory URI balíčku za absolutní.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-249">By default, the <xref:System.Uri> class considers pack URIs to be absolute.</span></span> <span data-ttu-id="ca6fe-250">V důsledku toho je vyvolána výjimka, když je vytvořena instance třídy <xref:System.Uri> s identifikátorem URI relativního balíčku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack URI.</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="ca6fe-251">Naštěstí <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> přetížení konstruktoru <xref:System.Uri> třídy přijímá parametr typu <xref:System.UriKind>, který umožňuje určit, zda je identifikátor URI balíčku buď absolutní, nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack URI is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="ca6fe-252">Pokud jste si jisti, že poskytnutý identifikátor URI Pack je jeden nebo druhý, je třeba zadat pouze <xref:System.UriKind.Absolute> nebo <xref:System.UriKind.Relative>.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack URI is one or the other.</span></span> <span data-ttu-id="ca6fe-253">Pokud neznáte typ identifikátoru URI balíčku, který se používá, například když uživatel zadá identifikátor URI balíčku za běhu, použijte místo toho <xref:System.UriKind.RelativeOrAbsolute>.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-253">If you don't know the type of pack URI that is used, such as when a user enters a pack URI at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="ca6fe-254">Tabulka 3 znázorňuje různé identifikátory URI relativních balíčků, které můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-254">Table 3 illustrates the various relative pack URIs that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ca6fe-255">Tabulka 3: identifikátory URI absolutních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="ca6fe-256">File</span><span class="sxs-lookup"><span data-stu-id="ca6fe-256">File</span></span>|<span data-ttu-id="ca6fe-257">Identifikátor URI absolutního balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-257">Absolute pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ca6fe-258">Místní sestavení souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="ca6fe-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-259">Soubor prostředků v sestavení místních podsložek</span><span class="sxs-lookup"><span data-stu-id="ca6fe-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-260">Soubor prostředků – odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-261">Soubor prostředků v podsložce odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-262">Soubor prostředků ve verzi odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-263">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-264">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="ca6fe-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-265">Lokalita zdrojového souboru</span><span class="sxs-lookup"><span data-stu-id="ca6fe-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="ca6fe-266">Lokalita zdrojového souboru v podsložce</span><span class="sxs-lookup"><span data-stu-id="ca6fe-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="ca6fe-267">Tabulka 4 znázorňuje různé identifikátory URI relativních balíčků, které můžete zadat v kódu pomocí <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-267">Table 4 illustrates the various relative pack URIs that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ca6fe-268">Tabulka 4: identifikátory URI relativních balíčků v kódu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="ca6fe-269">File</span><span class="sxs-lookup"><span data-stu-id="ca6fe-269">File</span></span>|<span data-ttu-id="ca6fe-270">Identifikátor URI relativního balíčku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-270">Relative pack URI</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="ca6fe-271">Místní sestavení souboru prostředků</span><span class="sxs-lookup"><span data-stu-id="ca6fe-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ca6fe-272">Soubor prostředků v sestavení místních podsložek</span><span class="sxs-lookup"><span data-stu-id="ca6fe-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ca6fe-273">Soubor prostředků – odkazované sestavení</span><span class="sxs-lookup"><span data-stu-id="ca6fe-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ca6fe-274">Soubor prostředků v sestavení odkazovaném podsložkou</span><span class="sxs-lookup"><span data-stu-id="ca6fe-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ca6fe-275">Soubor obsahu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="ca6fe-276">Soubor obsahu v podsložce</span><span class="sxs-lookup"><span data-stu-id="ca6fe-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="ca6fe-277">Scénáře identifikátoru URI pro Common Pack</span><span class="sxs-lookup"><span data-stu-id="ca6fe-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="ca6fe-278">V předchozích částech byly popsány postupy sestavení identifikátorů URI pro identifikaci prostředků, obsahu a umístění původních souborů.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-278">The preceding sections have discussed how to construct pack URIs to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="ca6fe-279">V rámci WPF jsou tyto konstrukce používány různými způsoby a následující oddíly obsahují několik běžných použití.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-279">In WPF, these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="ca6fe-280">Určení uživatelského rozhraní, které se zobrazí při spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="ca6fe-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="ca6fe-281"><xref:System.Windows.Application.StartupUri%2A> určuje první [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], který se má zobrazit při spuštění aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a WPF application is launched.</span></span> <span data-ttu-id="ca6fe-282">Pro samostatné aplikace může být [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] okno, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="ca6fe-283">Samostatné aplikace a aplikace prohlížeče XAML (XBAP) mohou také určit stránku jako počáteční uživatelské rozhraní, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-283">Standalone applications and XAML browser applications (XBAPs) can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="ca6fe-284">Pokud je aplikace samostatnou aplikací a je určena Stránka s <xref:System.Windows.Application.StartupUri%2A>, WPF otevře <xref:System.Windows.Navigation.NavigationWindow> pro hostování stránky.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, WPF opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="ca6fe-285">Pro XBAP se stránka zobrazuje v prohlížeči hostitele.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-285">For XBAPs, the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="ca6fe-286">Navigace na stránku</span><span class="sxs-lookup"><span data-stu-id="ca6fe-286">Navigating to a Page</span></span>

<span data-ttu-id="ca6fe-287">Následující příklad ukazuje, jak přejít na stránku.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="ca6fe-288">Další informace o různých způsobech navigace v WPF naleznete v tématu [Přehled navigace](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ca6fe-288">For more information on the various ways to navigate in WPF, see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="ca6fe-289">Určení ikony okna</span><span class="sxs-lookup"><span data-stu-id="ca6fe-289">Specifying a Window Icon</span></span>

<span data-ttu-id="ca6fe-290">Následující příklad ukazuje, jak použít identifikátor URI k určení ikony okna.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="ca6fe-291">Další informace naleznete v tématu <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="ca6fe-292">Načítání obrázků, zvukových souborů a videosouborů</span><span class="sxs-lookup"><span data-stu-id="ca6fe-292">Loading Image, Audio, and Video Files</span></span>

<span data-ttu-id="ca6fe-293">WPF umožňuje aplikacím využívat širokou škálu typů médií, které je možné identifikovat a načíst pomocí identifikátorů URI Pack, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-293">WPF allows applications to use a wide variety of media types, all of which can be identified and loaded with pack URIs, as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="ca6fe-294">Další informace o práci s mediálním obsahem najdete v tématu [grafika a multimédia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="ca6fe-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="ca6fe-295">Načítání slovníku prostředků z lokality původu</span><span class="sxs-lookup"><span data-stu-id="ca6fe-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="ca6fe-296">Slovníky prostředků (<xref:System.Windows.ResourceDictionary>) lze použít k podpoře motivů aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="ca6fe-297">Jedním ze způsobů, jak vytvářet a spravovat motivy, je vytvořit několik motivů jako slovníky prostředků nacházející se v lokalitě aplikace, kde je původ.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="ca6fe-298">To umožňuje přidat a aktualizovat motivy bez nutnosti opětovné kompilace a opětovného nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="ca6fe-299">Tyto slovníky prostředků je možné identifikovat a načíst pomocí identifikátorů URI Pack, který je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ca6fe-299">These resource dictionaries can be identified and loaded using pack URIs, which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="ca6fe-300">Přehled motivů v WPF naleznete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ca6fe-300">For an overview of themes in WPF, see [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca6fe-301">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca6fe-301">See also</span></span>

- [<span data-ttu-id="ca6fe-302">Prostředek, obsah a datové soubory aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="ca6fe-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
