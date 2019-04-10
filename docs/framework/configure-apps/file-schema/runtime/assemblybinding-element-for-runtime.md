---
title: <assemblyBinding> – element pro <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eec77d4dd42a7b95d1e2cd0e353e2e54746676b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225245"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="ab03b-102">\<assemblybinding – > – Element pro \<runtime ></span><span class="sxs-lookup"><span data-stu-id="ab03b-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="ab03b-103">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab03b-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="ab03b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ab03b-104">\<configuration></span></span>  
<span data-ttu-id="ab03b-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="ab03b-105">\<runtime></span></span>  
<span data-ttu-id="ab03b-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="ab03b-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab03b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab03b-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab03b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab03b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ab03b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab03b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab03b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab03b-110">Attributes</span></span>  
  
|<span data-ttu-id="ab03b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab03b-111">Attribute</span></span>|<span data-ttu-id="ab03b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ab03b-112">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="ab03b-113">xmlns</span><span class="sxs-lookup"><span data-stu-id="ab03b-113">xmlns</span></span>**|<span data-ttu-id="ab03b-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ab03b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ab03b-115">Určuje obor názvů XML, vyžaduje se pro vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab03b-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="ab03b-116">Použijte řetězec "urn: schémata-microsoft-com:asm.v1" jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ab03b-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|**<span data-ttu-id="ab03b-117">AppliesTo –</span><span class="sxs-lookup"><span data-stu-id="ab03b-117">appliesTo</span></span>**|<span data-ttu-id="ab03b-118">Určuje verzi modulu runtime, přesměrování sestavení rozhraní .NET Framework se týká.</span><span class="sxs-lookup"><span data-stu-id="ab03b-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="ab03b-119">Tento volitelný atribut používá pro určení verze, se vztahuje na číslo verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab03b-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="ab03b-120">Pokud ne **appliesTo** atribut zadán,  **\<assemblyBinding >** element platí pro všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab03b-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="ab03b-121">**AppliesTo** atribut byla zavedena v rozhraní .NET Framework verze 1.1; je ignorován v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="ab03b-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="ab03b-122">To znamená, že všechny  **\<assemblyBinding >** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.</span><span class="sxs-lookup"><span data-stu-id="ab03b-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab03b-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab03b-123">Child Elements</span></span>  
  
|<span data-ttu-id="ab03b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab03b-124">Element</span></span>|<span data-ttu-id="ab03b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ab03b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab03b-126">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="ab03b-126">\<dependentAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|<span data-ttu-id="ab03b-127">Zapouzdřuje umístění zásad a sestavení vazby pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab03b-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="ab03b-128">Použijte jednu  **\<dependentAssembly >** značky pro každé sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab03b-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="ab03b-129">\<zjišťování ></span><span class="sxs-lookup"><span data-stu-id="ab03b-129">\<probing></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|<span data-ttu-id="ab03b-130">Určuje modul common language runtime prohledá při načítání sestavení podadresářů.</span><span class="sxs-lookup"><span data-stu-id="ab03b-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="ab03b-131">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="ab03b-131">\<publisherPolicy></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|<span data-ttu-id="ab03b-132">Určuje, zda modul runtime použije zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="ab03b-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="ab03b-133">\<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="ab03b-133">\<qualifyAssembly></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|<span data-ttu-id="ab03b-134">Určuje úplný název sestavení, které se mají dynamicky načíst při použití částečný název.</span><span class="sxs-lookup"><span data-stu-id="ab03b-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab03b-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab03b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="ab03b-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab03b-136">Element</span></span>|<span data-ttu-id="ab03b-137">Popis</span><span class="sxs-lookup"><span data-stu-id="ab03b-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ab03b-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab03b-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ab03b-139">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ab03b-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ab03b-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab03b-140">Example</span></span>  
 <span data-ttu-id="ab03b-141">Následující příklad ukazuje způsob přesměrování jedné verze sestavení do druhého a poskytují základ kódu.</span><span class="sxs-lookup"><span data-stu-id="ab03b-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ab03b-142">Následující příklad ukazuje způsob použití **appliesTo** atribut pro přesměrování vazby sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab03b-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab03b-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab03b-143">See also</span></span>

- [<span data-ttu-id="ab03b-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ab03b-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ab03b-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ab03b-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ab03b-146">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="ab03b-146">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
