---
title: '&lt;etwenable –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 788eee71c718c003110ad8242505f2d7868e836c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506924"
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="37b1b-102">&lt;etwenable –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="37b1b-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="37b1b-103">Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro common language runtime události.</span><span class="sxs-lookup"><span data-stu-id="37b1b-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="37b1b-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="37b1b-104">\<configuration> Element</span></span>  
<span data-ttu-id="37b1b-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="37b1b-105">\<runtime> Element</span></span>  
<span data-ttu-id="37b1b-106">\<etwEnabled></span><span class="sxs-lookup"><span data-stu-id="37b1b-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b1b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37b1b-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37b1b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37b1b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37b1b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="37b1b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37b1b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="37b1b-110">Attributes</span></span>  
  
|<span data-ttu-id="37b1b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="37b1b-111">Attribute</span></span>|<span data-ttu-id="37b1b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="37b1b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37b1b-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="37b1b-113">enabled</span></span>|<span data-ttu-id="37b1b-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="37b1b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="37b1b-115">Určuje, zda by měly být povolené trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="37b1b-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="37b1b-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="37b1b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="37b1b-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37b1b-117">Value</span></span>|<span data-ttu-id="37b1b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="37b1b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37b1b-119">true</span><span class="sxs-lookup"><span data-stu-id="37b1b-119">true</span></span>|<span data-ttu-id="37b1b-120">Povolte trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="37b1b-120">Enable ETW.</span></span> <span data-ttu-id="37b1b-121">Toto je výchozí verze Windows od verze operačních systémů Windows Vista a Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="37b1b-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="37b1b-122">false</span><span class="sxs-lookup"><span data-stu-id="37b1b-122">false</span></span>|<span data-ttu-id="37b1b-123">Zakážete trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="37b1b-123">Disable ETW.</span></span> <span data-ttu-id="37b1b-124">Toto je výchozí hodnota u starších verzí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="37b1b-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37b1b-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37b1b-125">Child Elements</span></span>  
 <span data-ttu-id="37b1b-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="37b1b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37b1b-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37b1b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="37b1b-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="37b1b-128">Element</span></span>|<span data-ttu-id="37b1b-129">Popis</span><span class="sxs-lookup"><span data-stu-id="37b1b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="37b1b-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37b1b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="37b1b-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="37b1b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37b1b-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37b1b-132">Remarks</span></span>  
 <span data-ttu-id="37b1b-133">Od verze Windows Vista, je ve výchozím nastavení povolené trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="37b1b-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="37b1b-134">Tento element slouží k zakázání trasování událostí pro Windows pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37b1b-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="37b1b-135">V dřívějších verzích Windows použijte tento prvek povolit trasování událostí pro Windows pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37b1b-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37b1b-136">Trasování událostí pro Windows můžete povolit nebo zakázat globálně na serveru s použitím nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="37b1b-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="37b1b-137">Zobrazit [řízení přihlašování rozhraní .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="37b1b-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37b1b-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="37b1b-138">Example</span></span>  
 <span data-ttu-id="37b1b-139">Následující příklad ukazuje, jak povolit trasování událostí pro Windows pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37b1b-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37b1b-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37b1b-140">See also</span></span>
- [<span data-ttu-id="37b1b-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="37b1b-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="37b1b-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="37b1b-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="37b1b-143">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="37b1b-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
