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
ms.openlocfilehash: b5825efcc613689e73fb56b6695fe7c75ff09136
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674191"
---
# <a name="codebase-element"></a><span data-ttu-id="70349-102">\<codeBase > – Element</span><span class="sxs-lookup"><span data-stu-id="70349-102">\<codeBase> Element</span></span>

<span data-ttu-id="70349-103">Určuje, kde najít sestavení modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="70349-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="70349-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span><span class="sxs-lookup"><span data-stu-id="70349-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="70349-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70349-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70349-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="70349-106">Attributes and Elements</span></span>

<span data-ttu-id="70349-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="70349-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="70349-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="70349-108">Attributes</span></span>

|<span data-ttu-id="70349-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="70349-109">Attribute</span></span>|<span data-ttu-id="70349-110">Popis</span><span class="sxs-lookup"><span data-stu-id="70349-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="70349-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="70349-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="70349-112">Určuje adresu URL, kde modul runtime může najít zadanou verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="70349-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="70349-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="70349-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="70349-114">Určuje verzi sestavení, ve kterém základu kódu se vztahuje na.</span><span class="sxs-lookup"><span data-stu-id="70349-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="70349-115">Číslo verze sestavení má *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="70349-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="70349-116">verze atribut</span><span class="sxs-lookup"><span data-stu-id="70349-116">version Attribute</span></span>

|<span data-ttu-id="70349-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="70349-117">Value</span></span>|<span data-ttu-id="70349-118">Popis</span><span class="sxs-lookup"><span data-stu-id="70349-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="70349-119">Platné hodnoty pro každou část čísla verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="70349-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="70349-120">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="70349-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="70349-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="70349-121">Child Elements</span></span>

<span data-ttu-id="70349-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="70349-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70349-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="70349-123">Parent Elements</span></span>

|<span data-ttu-id="70349-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="70349-124">Element</span></span>|<span data-ttu-id="70349-125">Popis</span><span class="sxs-lookup"><span data-stu-id="70349-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="70349-126">Definuje kolekci zprostředkovatelů sestavení používá ke kompilaci soubory vlastních prostředků.</span><span class="sxs-lookup"><span data-stu-id="70349-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="70349-127">Můžete mít libovolný počet poskytovatelé sestavení.</span><span class="sxs-lookup"><span data-stu-id="70349-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="70349-128">Nakonfiguruje všechna nastavení kompilace, která používá ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="70349-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="70349-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70349-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="70349-130">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="70349-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70349-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70349-131">Remarks</span></span>

<span data-ttu-id="70349-132">Pro modul runtime pro použití  **\<codeBase >** nastavení v konfiguračním souboru počítače nebo soubor zásad vydavatele, soubor musíte také vytvořit přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="70349-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="70349-133">Konfigurační soubory aplikace mohou mít nastavení základu kódu bez přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="70349-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="70349-134">Po určení verze sestavení, které chcete použít, se vztahuje nastavení základu kódu ze souboru, který určuje verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="70349-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="70349-135">Pokud je uveden žádný základ kódu, modul runtime sondy pro sestavení obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="70349-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="70349-136">Pokud sestavení se silným názvem, nastavení základu kódu může být kdekoli na místním intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="70349-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="70349-137">Je-li soukromé sestavení je sestavení, nastavení základu kódu musí být cesta relativní k adresáři vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="70349-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="70349-138">Pro sestavení bez silného názvu, verze ignorovány a používá zavaděč první výskyt \<codebase > uvnitř \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="70349-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="70349-139">Pokud existuje položka v konfiguračním souboru aplikace, který přesměrovává vazby na jiné sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neshoduje požadavek na vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="70349-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="70349-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="70349-140">Example</span></span>

<span data-ttu-id="70349-141">Následující příklad ukazuje, jak určit, kde najít sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="70349-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="70349-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70349-142">See also</span></span>

- [<span data-ttu-id="70349-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="70349-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="70349-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="70349-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="70349-145">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="70349-145">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [<span data-ttu-id="70349-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="70349-146">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
