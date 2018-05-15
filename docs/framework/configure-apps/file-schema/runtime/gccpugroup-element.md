---
title: '&lt;Gccpugroup –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="7db66-102">&lt;Gccpugroup –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="7db66-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="7db66-103">Určuje, jestli uvolňování paměti podporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="7db66-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="7db66-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="7db66-104">\<configuration></span></span>  
<span data-ttu-id="7db66-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="7db66-105">\<runtime></span></span>  
<span data-ttu-id="7db66-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="7db66-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7db66-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7db66-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7db66-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7db66-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7db66-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7db66-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7db66-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7db66-110">Attributes</span></span>  
  
|<span data-ttu-id="7db66-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7db66-111">Attribute</span></span>|<span data-ttu-id="7db66-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7db66-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7db66-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7db66-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7db66-114">Určuje, jestli uvolňování paměti podporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="7db66-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7db66-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="7db66-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7db66-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7db66-116">Value</span></span>|<span data-ttu-id="7db66-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7db66-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7db66-118">Uvolňování paměti nepodporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="7db66-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="7db66-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7db66-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7db66-120">Uvolňování paměti podporuje více skupin procesoru, pokud je povolená kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="7db66-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7db66-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7db66-121">Child Elements</span></span>  
 <span data-ttu-id="7db66-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="7db66-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7db66-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7db66-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7db66-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7db66-124">Element</span></span>|<span data-ttu-id="7db66-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7db66-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7db66-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7db66-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7db66-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7db66-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7db66-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7db66-128">Remarks</span></span>  
 <span data-ttu-id="7db66-129">Pokud počítač obsahuje více skupin procesoru, kolekce paměti na serveru je povoleno (najdete v článku [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti ve všech skupinách procesoru a trvá všechny jader do účet při vytváření a vyrovnávání haldách.</span><span class="sxs-lookup"><span data-stu-id="7db66-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7db66-130">Tento prvek se vztahuje pouze na kolekce vláken uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7db66-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="7db66-131">Pokud chcete povolit distribuci vlákna uživatelského ve všech skupinách procesoru modulu runtime, musíte zároveň povolit [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="7db66-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7db66-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="7db66-132">Example</span></span>  
 <span data-ttu-id="7db66-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="7db66-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7db66-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7db66-134">See Also</span></span>  
 [<span data-ttu-id="7db66-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="7db66-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="7db66-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7db66-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7db66-137">Postupy: zakázat souběžná kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="7db66-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="7db66-138">Uvolňování paměti serveru a pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="7db66-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
