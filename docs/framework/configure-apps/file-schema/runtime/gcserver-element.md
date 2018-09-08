---
title: '&lt;gcServer&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bfe0db3d6fcbdbbcfb90ff488ab19cdbfaab75e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216142"
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="0fcad-102">&lt;gcServer&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="0fcad-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="0fcad-103">Určuje, zda modul common language runtime spustí uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="0fcad-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="0fcad-104">\<configuration></span></span>  
<span data-ttu-id="0fcad-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="0fcad-105">\<runtime></span></span>  
<span data-ttu-id="0fcad-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="0fcad-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fcad-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fcad-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fcad-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0fcad-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0fcad-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0fcad-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fcad-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0fcad-110">Attributes</span></span>  
  
|<span data-ttu-id="0fcad-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0fcad-111">Attribute</span></span>|<span data-ttu-id="0fcad-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0fcad-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0fcad-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0fcad-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0fcad-114">Určuje, zda modul runtime spustí uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0fcad-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0fcad-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0fcad-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0fcad-116">Value</span></span>|<span data-ttu-id="0fcad-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0fcad-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0fcad-118">Nejde spustit uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-118">Does not run server garbage collection.</span></span> <span data-ttu-id="0fcad-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="0fcad-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0fcad-120">Spustí uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fcad-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0fcad-121">Child Elements</span></span>  
 <span data-ttu-id="0fcad-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0fcad-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fcad-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0fcad-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0fcad-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fcad-124">Element</span></span>|<span data-ttu-id="0fcad-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0fcad-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0fcad-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fcad-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0fcad-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0fcad-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fcad-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fcad-128">Remarks</span></span>  
 <span data-ttu-id="0fcad-129">Modul CLR (CLR) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, která je dostupná na všech systémech, a uvolňování paměti serveru, který je k dispozici v systémech s více procesory.</span><span class="sxs-lookup"><span data-stu-id="0fcad-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="0fcad-130">Můžete použít `<gcServer>` elementu k řízení typu CLR uvolňování paměti provede.</span><span class="sxs-lookup"><span data-stu-id="0fcad-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="0fcad-131">Použití <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> a určí, zda je povoleno uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="0fcad-132">Jednoprocesorových počítačích výchozí kolekce uvolnění paměti pracovní stanice by měl být nejrychlejší možnost.</span><span class="sxs-lookup"><span data-stu-id="0fcad-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="0fcad-133">Pracovní stanice nebo serveru lze použít pro počítače se dvěma procesory.</span><span class="sxs-lookup"><span data-stu-id="0fcad-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="0fcad-134">Uvolnění paměti serveru by měl být nejrychlejší možnost pro více než dva procesory.</span><span class="sxs-lookup"><span data-stu-id="0fcad-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="0fcad-135">Tento element lze použít pouze v konfiguračním souboru aplikace; je ignorován, pokud je v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="0fcad-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fcad-136">V rozhraní .NET Framework 4 a dřívějších verzích souběžné uvolňování paměti není k dispozici při uvolnění paměti serveru je povolená.</span><span class="sxs-lookup"><span data-stu-id="0fcad-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="0fcad-137">Počínaje [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], je souběžné uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="0fcad-138">Chcete-li použít nesouběžné uvolňování, nastavte `<gcServer>` elementu `true` a [ \<gcConcurrent > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) k `false`.</span><span class="sxs-lookup"><span data-stu-id="0fcad-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fcad-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fcad-139">Example</span></span>  
 <span data-ttu-id="0fcad-140">Následující příklad umožňuje uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0fcad-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fcad-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fcad-141">See Also</span></span>  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0fcad-142">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0fcad-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0fcad-143">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0fcad-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0fcad-144">Postupy: zakázat souběžné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0fcad-144">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
