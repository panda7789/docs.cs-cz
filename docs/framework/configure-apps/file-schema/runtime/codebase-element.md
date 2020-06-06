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
ms.openlocfilehash: 475b7df55ed509157c1da0aeb8f979de238c72b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70971888"
---
# <a name="codebase-element"></a><span data-ttu-id="c3d31-102">Element \<codeBase></span><span class="sxs-lookup"><span data-stu-id="c3d31-102">\<codeBase> Element</span></span>

<span data-ttu-id="c3d31-103">Určuje, kde modul CLR (Common Language Runtime) může najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d31-103">Specifies where the common language runtime can find an assembly.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**

## <a name="syntax"></a><span data-ttu-id="c3d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3d31-104">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3d31-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c3d31-105">Attributes and Elements</span></span>

<span data-ttu-id="c3d31-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c3d31-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3d31-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c3d31-107">Attributes</span></span>

|<span data-ttu-id="c3d31-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="c3d31-108">Attribute</span></span>|<span data-ttu-id="c3d31-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c3d31-109">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="c3d31-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c3d31-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="c3d31-111">Určuje adresu URL, kde může modul runtime najít určenou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d31-111">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="c3d31-112">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c3d31-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="c3d31-113">Určuje verzi sestavení, na kterou se základ kódu vztahuje.</span><span class="sxs-lookup"><span data-stu-id="c3d31-113">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="c3d31-114">Formát čísla verze sestavení je *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="c3d31-114">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="c3d31-115">Atribut Version</span><span class="sxs-lookup"><span data-stu-id="c3d31-115">version Attribute</span></span>

|<span data-ttu-id="c3d31-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3d31-116">Value</span></span>|<span data-ttu-id="c3d31-117">Description</span><span class="sxs-lookup"><span data-stu-id="c3d31-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="c3d31-118">Platné hodnoty pro každou část čísla verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="c3d31-118">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="c3d31-119">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="c3d31-119">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c3d31-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c3d31-120">Child Elements</span></span>

<span data-ttu-id="c3d31-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="c3d31-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3d31-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c3d31-122">Parent Elements</span></span>

|<span data-ttu-id="c3d31-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="c3d31-123">Element</span></span>|<span data-ttu-id="c3d31-124">Description</span><span class="sxs-lookup"><span data-stu-id="c3d31-124">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="c3d31-125">Definuje kolekci poskytovatelů sestavení použitých ke kompilaci vlastních souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="c3d31-125">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="c3d31-126">Můžete mít libovolný počet poskytovatelů sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d31-126">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="c3d31-127">Konfiguruje všechna nastavení kompilace, která ASP.NET používá.</span><span class="sxs-lookup"><span data-stu-id="c3d31-127">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="c3d31-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3d31-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="c3d31-129">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c3d31-129">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c3d31-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3d31-130">Remarks</span></span>

<span data-ttu-id="c3d31-131">Aby modul runtime mohl použít **\<codeBase>** nastavení v konfiguračním souboru počítače nebo souboru zásad vydavatele, soubor musí také přesměrovat verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d31-131">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="c3d31-132">Konfigurační soubory aplikace mohou mít nastavení základu kódu bez přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d31-132">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="c3d31-133">Po určení používané verze sestavení používá modul runtime nastavení základu kódu ze souboru, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="c3d31-133">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="c3d31-134">Pokud není uveden žádný základ kódu, běhové testy pro sestavení obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="c3d31-134">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="c3d31-135">Pokud má sestavení silný název, může být nastavení základu kdekoli na místním intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="c3d31-135">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="c3d31-136">Pokud je sestavení privátní sestavení, musí být nastavení základu cesty relativní vzhledem k adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="c3d31-136">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="c3d31-137">U sestavení bez silného názvu je verze ignorována a zavaděč používá první vzhled v \<codebase> rámci \<dependentAssembly> .</span><span class="sxs-lookup"><span data-stu-id="c3d31-137">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="c3d31-138">Pokud existuje položka v konfiguračním souboru aplikace, která přesměrovává vazby na jiné sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neodpovídá požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="c3d31-138">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="c3d31-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3d31-139">Example</span></span>

<span data-ttu-id="c3d31-140">Následující příklad ukazuje, jak určit, kde modul runtime může najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3d31-140">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c3d31-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3d31-141">See also</span></span>

- [<span data-ttu-id="c3d31-142">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="c3d31-142">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="c3d31-143">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c3d31-143">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="c3d31-144">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="c3d31-144">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="c3d31-145">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="c3d31-145">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
