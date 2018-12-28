---
title: '&lt;Gccpugroup –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25d083b730117a791fb8ab550b36f7b2e6c5f5be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613710"
---
# <a name="ltgccpugroupgt-element"></a><span data-ttu-id="feb20-102">&lt;Gccpugroup –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="feb20-102">&lt;GCCpuGroup&gt; Element</span></span>
<span data-ttu-id="feb20-103">Určuje, zda uvolňování podporuje více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="feb20-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>  
  
 <span data-ttu-id="feb20-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="feb20-104">\<configuration></span></span>  
<span data-ttu-id="feb20-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="feb20-105">\<runtime></span></span>  
<span data-ttu-id="feb20-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="feb20-106">\<GCCpuGroup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb20-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feb20-107">Syntax</span></span>  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="feb20-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="feb20-108">Attributes and Elements</span></span>  
 <span data-ttu-id="feb20-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="feb20-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="feb20-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="feb20-110">Attributes</span></span>  
  
|<span data-ttu-id="feb20-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="feb20-111">Attribute</span></span>|<span data-ttu-id="feb20-112">Popis</span><span class="sxs-lookup"><span data-stu-id="feb20-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="feb20-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="feb20-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="feb20-114">Určuje, zda uvolňování podporuje více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="feb20-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="feb20-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="feb20-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="feb20-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="feb20-116">Value</span></span>|<span data-ttu-id="feb20-117">Popis</span><span class="sxs-lookup"><span data-stu-id="feb20-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="feb20-118">Uvolňování paměti kolekce nepodporuje více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="feb20-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="feb20-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="feb20-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="feb20-120">Uvolňování paměti podporuje více skupin procesorů, pokud je povolené uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="feb20-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="feb20-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="feb20-121">Child Elements</span></span>  
 <span data-ttu-id="feb20-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="feb20-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="feb20-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="feb20-123">Parent Elements</span></span>  
  
|<span data-ttu-id="feb20-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="feb20-124">Element</span></span>|<span data-ttu-id="feb20-125">Popis</span><span class="sxs-lookup"><span data-stu-id="feb20-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="feb20-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="feb20-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="feb20-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="feb20-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feb20-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="feb20-128">Remarks</span></span>  
 <span data-ttu-id="feb20-129">Když počítač má více skupin procesorů a uvolňování paměti serveru je povolená (najdete v článku [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru a přejde do všech jader účet při vytváření a rozložení zátěže haldy.</span><span class="sxs-lookup"><span data-stu-id="feb20-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feb20-130">Tento element se vztahují pouze k vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="feb20-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="feb20-131">Pokud chcete povolit modul runtime bude distribuovat Uživatelská vlákna ve všech skupinách procesoru, musíte také povolit [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="feb20-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb20-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="feb20-132">Example</span></span>  
 <span data-ttu-id="feb20-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="feb20-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="feb20-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="feb20-134">See Also</span></span>  
- [<span data-ttu-id="feb20-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="feb20-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="feb20-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="feb20-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="feb20-137">Postupy: Zakázat souběžné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="feb20-137">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
- [<span data-ttu-id="feb20-138">Uvolňování paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="feb20-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
