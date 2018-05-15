---
title: '&lt;Thread_UseAllCpuGroups&gt; – Element'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47d8bcdb9bbb7ec6f5a5386a5ac5951ad8891c28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="da384-102">&lt;Thread_UseAllCpuGroups&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="da384-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="da384-103">Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="da384-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="da384-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="da384-104">\<configuration></span></span>  
<span data-ttu-id="da384-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="da384-105">\<runtime></span></span>  
<span data-ttu-id="da384-106">< Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="da384-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da384-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da384-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da384-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da384-108">Attributes and Elements</span></span>  
 <span data-ttu-id="da384-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da384-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da384-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="da384-110">Attributes</span></span>  
  
|<span data-ttu-id="da384-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="da384-111">Attribute</span></span>|<span data-ttu-id="da384-112">Popis</span><span class="sxs-lookup"><span data-stu-id="da384-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="da384-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="da384-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="da384-114">Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="da384-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="da384-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="da384-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="da384-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="da384-116">Value</span></span>|<span data-ttu-id="da384-117">Popis</span><span class="sxs-lookup"><span data-stu-id="da384-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="da384-118">Modul runtime neprovede distribuci spravovaných vláknech v několika skupinách pro využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="da384-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="da384-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="da384-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="da384-120">Modul runtime distribuuje spravovaných vláknech v několika skupinách pro procesor, pokud má počítač více skupin procesoru a [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element je povoleno.</span><span class="sxs-lookup"><span data-stu-id="da384-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da384-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="da384-121">Child Elements</span></span>  
 <span data-ttu-id="da384-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="da384-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da384-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="da384-123">Parent Elements</span></span>  
  
|<span data-ttu-id="da384-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="da384-124">Element</span></span>|<span data-ttu-id="da384-125">Popis</span><span class="sxs-lookup"><span data-stu-id="da384-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="da384-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da384-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="da384-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="da384-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da384-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da384-128">Remarks</span></span>  
 <span data-ttu-id="da384-129">Pokud počítač obsahuje více skupin procesoru, povolení tohoto elementu způsobí, že modul runtime pro distribuci spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="da384-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="da384-130">Chcete-li tuto funkci používat, musíte také povolit [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, který rozšiřuje uvolňování paměti pro všechny skupiny procesoru a bere v potaz při vytváření a vyrovnávání haldách všechny jader.</span><span class="sxs-lookup"><span data-stu-id="da384-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="da384-131">Povolení [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) prvek vyžaduje povolení [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="da384-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="da384-132">Pokud nejsou povolené tyto prvky, povolení `<Thread_UseAllCpuGroups>` element nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="da384-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da384-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="da384-133">Example</span></span>  
 <span data-ttu-id="da384-134">Následující příklad ukazuje, jak povolit podporu pro více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="da384-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="da384-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="da384-135">See Also</span></span>  
 [<span data-ttu-id="da384-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="da384-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="da384-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="da384-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="da384-138">\<Gccpugroup – > elementu</span><span class="sxs-lookup"><span data-stu-id="da384-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
