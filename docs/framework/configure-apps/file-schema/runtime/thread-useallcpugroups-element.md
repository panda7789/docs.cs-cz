---
title: "&lt;Thread_UseAllCpuGroups&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 187e391acf3b80a5ae2dfe795c4a3b397af815ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="5a1ec-102">&lt;Thread_UseAllCpuGroups&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="5a1ec-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="5a1ec-103">Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="5a1ec-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5a1ec-104">\<configuration></span></span>  
<span data-ttu-id="5a1ec-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="5a1ec-105">\<runtime></span></span>  
<span data-ttu-id="5a1ec-106">< Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="5a1ec-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a1ec-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a1ec-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a1ec-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a1ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a1ec-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a1ec-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a1ec-110">Attributes</span></span>  
  
|<span data-ttu-id="5a1ec-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a1ec-111">Attribute</span></span>|<span data-ttu-id="5a1ec-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5a1ec-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5a1ec-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a1ec-114">Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5a1ec-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="5a1ec-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5a1ec-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5a1ec-116">Value</span></span>|<span data-ttu-id="5a1ec-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5a1ec-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5a1ec-118">Modul runtime neprovede distribuci spravovaných vláknech v několika skupinách pro využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="5a1ec-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5a1ec-120">Modul runtime distribuuje spravovaných vláknech v několika skupinách pro procesor, pokud má počítač více skupin procesoru a [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element je povoleno.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a1ec-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a1ec-121">Child Elements</span></span>  
 <span data-ttu-id="5a1ec-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a1ec-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a1ec-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a1ec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5a1ec-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a1ec-124">Element</span></span>|<span data-ttu-id="5a1ec-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5a1ec-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a1ec-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a1ec-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a1ec-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a1ec-128">Remarks</span></span>  
 <span data-ttu-id="5a1ec-129">Pokud počítač obsahuje více skupin procesoru, povolení tohoto elementu způsobí, že modul runtime pro distribuci spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="5a1ec-130">Chcete-li tuto funkci používat, musíte také povolit [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, který rozšiřuje uvolňování paměti pro všechny skupiny procesoru a bere v potaz při vytváření a vyrovnávání haldách všechny jader.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="5a1ec-131">Povolení [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) prvek vyžaduje povolení [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="5a1ec-132">Pokud nejsou povolené tyto prvky, povolení `<Thread_UseAllCpuGroups>` element nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a1ec-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a1ec-133">Example</span></span>  
 <span data-ttu-id="5a1ec-134">Následující příklad ukazuje, jak povolit podporu pro více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="5a1ec-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a1ec-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a1ec-135">See Also</span></span>  
 [<span data-ttu-id="5a1ec-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="5a1ec-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5a1ec-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5a1ec-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5a1ec-138">\<Gccpugroup – > elementu</span><span class="sxs-lookup"><span data-stu-id="5a1ec-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
