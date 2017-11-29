---
title: "&lt;Gccpugroup –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abcb6d1b5f9dbb7a866b55628aabfe996a0a747c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="29db0-102">&lt;Gccpugroup –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="29db0-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="29db0-103">Určuje, jestli uvolňování paměti podporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="29db0-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="29db0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="29db0-104">\<configuration></span></span>  
<span data-ttu-id="29db0-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="29db0-105">\<runtime></span></span>  
<span data-ttu-id="29db0-106">\<Gccpugroup – ></span><span class="sxs-lookup"><span data-stu-id="29db0-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29db0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29db0-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29db0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29db0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29db0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29db0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29db0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="29db0-110">Attributes</span></span>  
  
|<span data-ttu-id="29db0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="29db0-111">Attribute</span></span>|<span data-ttu-id="29db0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="29db0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="29db0-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="29db0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="29db0-114">Určuje, jestli uvolňování paměti podporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="29db0-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="29db0-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="29db0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="29db0-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="29db0-116">Value</span></span>|<span data-ttu-id="29db0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="29db0-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="29db0-118">Uvolňování paměti nepodporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="29db0-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="29db0-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="29db0-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="29db0-120">Uvolňování paměti podporuje více skupin procesoru, pokud je povolená kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="29db0-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29db0-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29db0-121">Child Elements</span></span>  
 <span data-ttu-id="29db0-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="29db0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29db0-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29db0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="29db0-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="29db0-124">Element</span></span>|<span data-ttu-id="29db0-125">Popis</span><span class="sxs-lookup"><span data-stu-id="29db0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="29db0-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29db0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="29db0-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="29db0-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29db0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29db0-128">Remarks</span></span>  
 <span data-ttu-id="29db0-129">Pokud počítač obsahuje více skupin procesoru, kolekce paměti na serveru je povoleno (najdete v článku [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti ve všech skupinách procesoru a trvá všechny jader do účet při vytváření a vyrovnávání haldách.</span><span class="sxs-lookup"><span data-stu-id="29db0-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29db0-130">Tento prvek se vztahuje pouze na kolekce vláken uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="29db0-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="29db0-131">Pokud chcete povolit distribuci vlákna uživatelského ve všech skupinách procesoru modulu runtime, musíte zároveň povolit [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="29db0-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29db0-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="29db0-132">Example</span></span>  
 <span data-ttu-id="29db0-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="29db0-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29db0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="29db0-134">See Also</span></span>  
 [<span data-ttu-id="29db0-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="29db0-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="29db0-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="29db0-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="29db0-137">Postupy: zakázat souběžná kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="29db0-137">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/en-us/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [<span data-ttu-id="29db0-138">Uvolňování paměti serveru a pracovní stanice</span><span class="sxs-lookup"><span data-stu-id="29db0-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
