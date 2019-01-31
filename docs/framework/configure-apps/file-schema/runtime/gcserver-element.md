---
title: Element <gcServer>
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
ms.openlocfilehash: 4c5cfe52d37c3ce2e78d07886b0856be46bfaadc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287557"
---
# <a name="gcserver-element"></a><span data-ttu-id="d6b6a-102">\<gcServer> Element</span><span class="sxs-lookup"><span data-stu-id="d6b6a-102">\<gcServer> Element</span></span>
<span data-ttu-id="d6b6a-103">Určuje, zda modul common language runtime spustí uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="d6b6a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d6b6a-104">\<configuration></span></span>  
<span data-ttu-id="d6b6a-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="d6b6a-105">\<runtime></span></span>  
<span data-ttu-id="d6b6a-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="d6b6a-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b6a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b6a-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6b6a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6b6a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d6b6a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6b6a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6b6a-110">Attributes</span></span>  
  
|<span data-ttu-id="d6b6a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6b6a-111">Attribute</span></span>|<span data-ttu-id="d6b6a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b6a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d6b6a-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d6b6a-114">Určuje, zda modul runtime spustí uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d6b6a-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d6b6a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d6b6a-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d6b6a-116">Value</span></span>|<span data-ttu-id="d6b6a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b6a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d6b6a-118">Nejde spustit uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-118">Does not run server garbage collection.</span></span> <span data-ttu-id="d6b6a-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d6b6a-120">Spustí uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6b6a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b6a-121">Child Elements</span></span>  
 <span data-ttu-id="d6b6a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6b6a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6b6a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b6a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d6b6a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6b6a-124">Element</span></span>|<span data-ttu-id="d6b6a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b6a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d6b6a-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d6b6a-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6b6a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6b6a-128">Remarks</span></span>  
 <span data-ttu-id="d6b6a-129">Modul CLR (CLR) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, která je dostupná na všech systémech, a uvolňování paměti serveru, který je k dispozici v systémech s více procesory.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="d6b6a-130">Můžete použít `<gcServer>` elementu k řízení typu CLR uvolňování paměti provede.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="d6b6a-131">Použití <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> a určí, zda je povoleno uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="d6b6a-132">Jednoprocesorových počítačích výchozí kolekce uvolnění paměti pracovní stanice by měl být nejrychlejší možnost.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="d6b6a-133">Pracovní stanice nebo serveru lze použít pro počítače se dvěma procesory.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="d6b6a-134">Uvolnění paměti serveru by měl být nejrychlejší možnost pro více než dva procesory.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="d6b6a-135">Tento element lze použít pouze v konfiguračním souboru aplikace; je ignorován, pokud je v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6b6a-136">V rozhraní .NET Framework 4 a dřívějších verzích souběžné uvolňování paměti není k dispozici při uvolnění paměti serveru je povolená.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="d6b6a-137">Počínaje [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], je souběžné uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="d6b6a-138">Chcete-li použít nesouběžné uvolňování, nastavte `<gcServer>` elementu `true` a [ \<gcConcurrent > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) k `false`.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6b6a-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b6a-139">Example</span></span>  
 <span data-ttu-id="d6b6a-140">Následující příklad umožňuje uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d6b6a-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6b6a-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6b6a-141">See also</span></span>
- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d6b6a-142">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d6b6a-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d6b6a-143">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d6b6a-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d6b6a-144">Postupy: Zakázat souběžné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="d6b6a-144">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
