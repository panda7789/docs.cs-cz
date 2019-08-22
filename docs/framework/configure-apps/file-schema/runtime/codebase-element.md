---
title: Element <codeBase>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663870"
---
# <a name="codebase-element"></a><span data-ttu-id="5baf8-102">\<> – element codeBase</span><span class="sxs-lookup"><span data-stu-id="5baf8-102">\<codeBase> Element</span></span>

<span data-ttu-id="5baf8-103">Určuje, kde modul CLR (Common Language Runtime) může najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="5baf8-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="5baf8-104">\<Configuration > \<runtime > \<assemblyBinding > \<dependentAssembly – \<> kódu ></span><span class="sxs-lookup"><span data-stu-id="5baf8-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="5baf8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5baf8-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5baf8-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5baf8-106">Attributes and Elements</span></span>

<span data-ttu-id="5baf8-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5baf8-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5baf8-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="5baf8-108">Attributes</span></span>

|<span data-ttu-id="5baf8-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="5baf8-109">Attribute</span></span>|<span data-ttu-id="5baf8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5baf8-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="5baf8-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5baf8-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="5baf8-112">Určuje adresu URL, kde může modul runtime najít určenou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="5baf8-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="5baf8-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5baf8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5baf8-114">Určuje verzi sestavení, na kterou se základ kódu vztahuje.</span><span class="sxs-lookup"><span data-stu-id="5baf8-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="5baf8-115">Formát čísla verze sestavení je *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="5baf8-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="5baf8-116">Atribut Version</span><span class="sxs-lookup"><span data-stu-id="5baf8-116">version Attribute</span></span>

|<span data-ttu-id="5baf8-117">Value</span><span class="sxs-lookup"><span data-stu-id="5baf8-117">Value</span></span>|<span data-ttu-id="5baf8-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5baf8-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="5baf8-119">Platné hodnoty pro každou část čísla verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="5baf8-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="5baf8-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5baf8-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5baf8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5baf8-121">Child Elements</span></span>

<span data-ttu-id="5baf8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="5baf8-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5baf8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5baf8-123">Parent Elements</span></span>

|<span data-ttu-id="5baf8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5baf8-124">Element</span></span>|<span data-ttu-id="5baf8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5baf8-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="5baf8-126">Definuje kolekci poskytovatelů sestavení použitých ke kompilaci vlastních souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="5baf8-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="5baf8-127">Můžete mít libovolný počet poskytovatelů sestavení.</span><span class="sxs-lookup"><span data-stu-id="5baf8-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="5baf8-128">Konfiguruje všechna nastavení kompilace, která ASP.NET používá.</span><span class="sxs-lookup"><span data-stu-id="5baf8-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="5baf8-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5baf8-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="5baf8-130">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5baf8-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5baf8-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5baf8-131">Remarks</span></span>

<span data-ttu-id="5baf8-132">Aby modul runtime používal  **\<>** nastavení v konfiguračním souboru počítače nebo souboru zásad vydavatele, soubor musí také přesměrovat verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="5baf8-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="5baf8-133">Konfigurační soubory aplikace mohou mít nastavení základu kódu bez přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="5baf8-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="5baf8-134">Po určení používané verze sestavení používá modul runtime nastavení základu kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="5baf8-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="5baf8-135">Pokud není uveden žádný základ kódu, běhové testy pro sestavení obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="5baf8-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="5baf8-136">Pokud má sestavení silný název, může být nastavení základu kdekoli na místním intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="5baf8-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="5baf8-137">Pokud je sestavení privátní sestavení, musí být nastavení základu cesty relativní vzhledem k adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="5baf8-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="5baf8-138">U sestavení bez silného názvu je verze ignorována a zavaděč používá první vzhled \<základu kódu > uvnitř \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="5baf8-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="5baf8-139">Pokud existuje položka v konfiguračním souboru aplikace, která přesměrovává vazby na jiné sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neodpovídá požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="5baf8-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="5baf8-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="5baf8-140">Example</span></span>

<span data-ttu-id="5baf8-141">Následující příklad ukazuje, jak určit, kde modul runtime může najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="5baf8-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5baf8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5baf8-142">See also</span></span>

- [<span data-ttu-id="5baf8-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="5baf8-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5baf8-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5baf8-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5baf8-145">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="5baf8-145">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="5baf8-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="5baf8-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
