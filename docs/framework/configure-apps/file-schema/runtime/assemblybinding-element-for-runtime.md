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
ms.openlocfilehash: 84ec54eeb8adee90031057dadc4549cb73527be1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663904"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="16a00-102">\<assemblyBinding element > pro \<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="16a00-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="16a00-103">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="16a00-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
 <span data-ttu-id="16a00-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="16a00-104">\<configuration></span></span>  
<span data-ttu-id="16a00-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="16a00-105">\<runtime></span></span>  
<span data-ttu-id="16a00-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="16a00-106">\<assemblyBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a00-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16a00-107">Syntax</span></span>  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16a00-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="16a00-108">Attributes and Elements</span></span>  
 <span data-ttu-id="16a00-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="16a00-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16a00-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="16a00-110">Attributes</span></span>  
  
|<span data-ttu-id="16a00-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="16a00-111">Attribute</span></span>|<span data-ttu-id="16a00-112">Popis</span><span class="sxs-lookup"><span data-stu-id="16a00-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16a00-113">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="16a00-113">**xmlns**</span></span>|<span data-ttu-id="16a00-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="16a00-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="16a00-115">Určuje obor názvů XML vyžadovaný pro vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="16a00-115">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="16a00-116">Jako hodnotu použijte řetězec "urn: schemas-microsoft-com: asm. v1".</span><span class="sxs-lookup"><span data-stu-id="16a00-116">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="16a00-117">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="16a00-117">**appliesTo**</span></span>|<span data-ttu-id="16a00-118">Určuje verzi modulu runtime, pro kterou je přesměrování sestavení .NET Framework použito.</span><span class="sxs-lookup"><span data-stu-id="16a00-118">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="16a00-119">Tento nepovinný atribut používá .NET Framework číslo verze k určení verze, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="16a00-119">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="16a00-120">Pokud ne **appliesTo** atribut zadán, **\<assemblyBinding>** element platí pro všechny verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16a00-120">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="16a00-121">Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="16a00-121">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="16a00-122">To znamená, že všechny **\<assemblyBinding>** prvky se použijí při použití rozhraní .NET Framework verze 1.0, i když **appliesTo** je zadán atribut.</span><span class="sxs-lookup"><span data-stu-id="16a00-122">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16a00-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="16a00-123">Child Elements</span></span>  
  
|<span data-ttu-id="16a00-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="16a00-124">Element</span></span>|<span data-ttu-id="16a00-125">Popis</span><span class="sxs-lookup"><span data-stu-id="16a00-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16a00-126">\<> dependentAssembly</span><span class="sxs-lookup"><span data-stu-id="16a00-126">\<dependentAssembly></span></span>](dependentassembly-element.md)|<span data-ttu-id="16a00-127">Zapouzdřuje zásady vazeb a umístění sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="16a00-127">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="16a00-128">Pro každé sestavení použijte jednu  **\<značku > dependentAssembly** .</span><span class="sxs-lookup"><span data-stu-id="16a00-128">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[<span data-ttu-id="16a00-129">\<> zjišťování</span><span class="sxs-lookup"><span data-stu-id="16a00-129">\<probing></span></span>](probing-element.md)|<span data-ttu-id="16a00-130">Určuje podadresáře, které modul CLR (Common Language Runtime) hledá při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="16a00-130">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[<span data-ttu-id="16a00-131">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="16a00-131">\<publisherPolicy></span></span>](publisherpolicy-element.md)|<span data-ttu-id="16a00-132">Určuje, zda modul runtime používá zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="16a00-132">Specifies whether the runtime applies publisher policy.</span></span>|  
|[<span data-ttu-id="16a00-133">\<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="16a00-133">\<qualifyAssembly></span></span>](qualifyassembly-element.md)|<span data-ttu-id="16a00-134">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="16a00-134">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16a00-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="16a00-135">Parent Elements</span></span>  
  
|<span data-ttu-id="16a00-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="16a00-136">Element</span></span>|<span data-ttu-id="16a00-137">Popis</span><span class="sxs-lookup"><span data-stu-id="16a00-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16a00-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16a00-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16a00-139">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="16a00-139">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16a00-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="16a00-140">Example</span></span>  
 <span data-ttu-id="16a00-141">Následující příklad ukazuje, jak přesměrovat jednu verzi sestavení na jiný a poskytnout základ kódu.</span><span class="sxs-lookup"><span data-stu-id="16a00-141">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="16a00-142">Následující příklad ukazuje, jak použít atribut **AppliesTo** pro přesměrování vazby .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="16a00-142">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16a00-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16a00-143">See also</span></span>

- [<span data-ttu-id="16a00-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="16a00-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16a00-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="16a00-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="16a00-146">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="16a00-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
