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
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154319"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="a9aec-102">\<assemblyBinding> – element pro \<runtime></span><span class="sxs-lookup"><span data-stu-id="a9aec-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="a9aec-103">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9aec-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="a9aec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9aec-104">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9aec-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a9aec-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a9aec-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a9aec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9aec-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a9aec-107">Attributes</span></span>  
  
|<span data-ttu-id="a9aec-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a9aec-108">Attribute</span></span>|<span data-ttu-id="a9aec-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a9aec-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9aec-110">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="a9aec-110">**xmlns**</span></span>|<span data-ttu-id="a9aec-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a9aec-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a9aec-112">Určuje obor názvů XML vyžadovaný pro vazbu sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9aec-112">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="a9aec-113">Jako hodnotu použijte řetězec "urn: schemas-microsoft-com: asm. v1".</span><span class="sxs-lookup"><span data-stu-id="a9aec-113">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="a9aec-114">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="a9aec-114">**appliesTo**</span></span>|<span data-ttu-id="a9aec-115">Určuje verzi modulu runtime, pro kterou je přesměrování sestavení .NET Framework použito.</span><span class="sxs-lookup"><span data-stu-id="a9aec-115">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="a9aec-116">Tento nepovinný atribut používá .NET Framework číslo verze k určení verze, na kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="a9aec-116">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="a9aec-117">Pokud není zadán žádný atribut **AppliesTo** , bude **\<assemblyBinding>** element platit pro všechny verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9aec-117">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="a9aec-118">Atribut **AppliesTo** byl představen v .NET Framework verze 1,1; ignoruje se .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="a9aec-118">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="a9aec-119">To znamená, že všechny **\<assemblyBinding>** prvky jsou aplikovány při použití .NET Framework verze 1,0, a to i v případě, že je zadán atribut **AppliesTo** .</span><span class="sxs-lookup"><span data-stu-id="a9aec-119">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9aec-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a9aec-120">Child Elements</span></span>  
  
|<span data-ttu-id="a9aec-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9aec-121">Element</span></span>|<span data-ttu-id="a9aec-122">Description</span><span class="sxs-lookup"><span data-stu-id="a9aec-122">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="a9aec-123">Zapouzdřuje zásady vazeb a umístění sestavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9aec-123">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="a9aec-124">**\<dependentAssembly>** Pro každé sestavení použijte jednu značku.</span><span class="sxs-lookup"><span data-stu-id="a9aec-124">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="a9aec-125">Určuje podadresáře, které modul CLR (Common Language Runtime) hledá při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9aec-125">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="a9aec-126">Určuje, zda modul runtime používá zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="a9aec-126">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="a9aec-127">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="a9aec-127">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9aec-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a9aec-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a9aec-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="a9aec-129">Element</span></span>|<span data-ttu-id="a9aec-130">Description</span><span class="sxs-lookup"><span data-stu-id="a9aec-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a9aec-131">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9aec-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a9aec-132">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a9aec-132">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a9aec-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9aec-133">Example</span></span>  
 <span data-ttu-id="a9aec-134">Následující příklad ukazuje, jak přesměrovat jednu verzi sestavení na jiný a poskytnout základ kódu.</span><span class="sxs-lookup"><span data-stu-id="a9aec-134">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
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
  
 <span data-ttu-id="a9aec-135">Následující příklad ukazuje, jak použít atribut **AppliesTo** pro přesměrování vazby .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="a9aec-135">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9aec-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9aec-136">See also</span></span>

- [<span data-ttu-id="a9aec-137">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a9aec-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a9aec-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a9aec-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a9aec-139">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="a9aec-139">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
