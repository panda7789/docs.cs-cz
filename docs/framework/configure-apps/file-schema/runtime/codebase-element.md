---
title: "&lt;codeBase&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b30f1dc3ccade3028c31c57ffdab521802f086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="bec6f-102">&lt;codeBase&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="bec6f-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="bec6f-103">Určuje, kde sestavení modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="bec6f-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="bec6f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="bec6f-104">\<configuration></span></span>  
<span data-ttu-id="bec6f-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="bec6f-105">\<runtime></span></span>  
<span data-ttu-id="bec6f-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="bec6f-106">\<assemblyBinding></span></span>  
<span data-ttu-id="bec6f-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="bec6f-107">\<dependentAssembly></span></span>  
<span data-ttu-id="bec6f-108">\<codeBase ></span><span class="sxs-lookup"><span data-stu-id="bec6f-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec6f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bec6f-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bec6f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bec6f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bec6f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bec6f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bec6f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bec6f-112">Attributes</span></span>  
  
|<span data-ttu-id="bec6f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="bec6f-113">Attribute</span></span>|<span data-ttu-id="bec6f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bec6f-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="bec6f-115">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bec6f-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="bec6f-116">Určuje adresu URL, kde zadaná verze sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bec6f-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="bec6f-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="bec6f-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="bec6f-118">Určuje verzi sestavení, ve kterém základu kódu se vztahuje na.</span><span class="sxs-lookup"><span data-stu-id="bec6f-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="bec6f-119">Formát čísla verze sestavení je *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="bec6f-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="bec6f-120">verze atribut</span><span class="sxs-lookup"><span data-stu-id="bec6f-120">version Attribute</span></span>  
  
|<span data-ttu-id="bec6f-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bec6f-121">Value</span></span>|<span data-ttu-id="bec6f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="bec6f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bec6f-123">Platné hodnoty pro každou část číslo verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="bec6f-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="bec6f-124">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="bec6f-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bec6f-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bec6f-125">Child Elements</span></span>  
 <span data-ttu-id="bec6f-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="bec6f-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bec6f-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bec6f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bec6f-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="bec6f-128">Element</span></span>|<span data-ttu-id="bec6f-129">Popis</span><span class="sxs-lookup"><span data-stu-id="bec6f-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="bec6f-130">Definuje kolekci zprostředkovatelů sestavení používá ke kompilaci vlastních souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="bec6f-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="bec6f-131">Může mít libovolný počet poskytovatele sestavení.</span><span class="sxs-lookup"><span data-stu-id="bec6f-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="bec6f-132">Nakonfiguruje všechna nastavení kompilace, která používá technologii ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bec6f-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="bec6f-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bec6f-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="bec6f-134">Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bec6f-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bec6f-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bec6f-135">Remarks</span></span>  
 <span data-ttu-id="bec6f-136">Pro modul runtime používat  **\<codeBase >** nastavení v konfiguračním souboru počítače nebo soubor zásad vydavatele, soubor musí také přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="bec6f-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="bec6f-137">Konfigurační soubory aplikace mohou mít nastavení codebase bez přesměrování verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="bec6f-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="bec6f-138">Po určení, které verze sestavení se má použít, se vztahuje codebase nastavení ze souboru, který určuje verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bec6f-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="bec6f-139">Pokud je uvedené žádné codebase, sondy modulu runtime pro sestavení obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="bec6f-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="bec6f-140">Pokud sestavení se silným názvem, codebase nastavení může být kdekoli na místního intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="bec6f-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="bec6f-141">Pokud je sestavení privátní sestavení, nastavení codebase musí být cesta relativní vzhledem k adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="bec6f-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="bec6f-142">Pro sestavení bez silný název, verze ignorováno a zavaděč používá první vzhled \<codebase > uvnitř \<dependentAssembly >.</span><span class="sxs-lookup"><span data-stu-id="bec6f-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="bec6f-143">Pokud je položka v konfiguračním souboru aplikace, který provede přesměrování vazby sestavení, přesměrování bude mít přednost i v případě, že verze sestavení neshoduje vazby požadavku.</span><span class="sxs-lookup"><span data-stu-id="bec6f-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bec6f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="bec6f-144">Example</span></span>  
 <span data-ttu-id="bec6f-145">Následující příklad ukazuje, jak k určení, kde sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bec6f-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bec6f-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="bec6f-146">See Also</span></span>  
 [<span data-ttu-id="bec6f-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="bec6f-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="bec6f-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="bec6f-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="bec6f-149">Určení umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="bec6f-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="bec6f-150">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="bec6f-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
