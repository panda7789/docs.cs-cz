---
title: Element <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3510cbf0a63a8031669bb7a819a8b3c7321aaea4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920765"
---
# <a name="etwenable-element"></a><span data-ttu-id="23b90-102">\<etwEnable – element ></span><span class="sxs-lookup"><span data-stu-id="23b90-102">\<etwEnable> Element</span></span>
<span data-ttu-id="23b90-103">Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="23b90-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="23b90-104">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="23b90-104">\<configuration> Element</span></span>  
<span data-ttu-id="23b90-105">\<Běhový > element</span><span class="sxs-lookup"><span data-stu-id="23b90-105">\<runtime> Element</span></span>  
<span data-ttu-id="23b90-106">\<etwEnabled></span><span class="sxs-lookup"><span data-stu-id="23b90-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b90-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23b90-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23b90-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="23b90-108">Attributes and Elements</span></span>  
 <span data-ttu-id="23b90-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="23b90-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23b90-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="23b90-110">Attributes</span></span>  
  
|<span data-ttu-id="23b90-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="23b90-111">Attribute</span></span>|<span data-ttu-id="23b90-112">Popis</span><span class="sxs-lookup"><span data-stu-id="23b90-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23b90-113">enabled</span><span class="sxs-lookup"><span data-stu-id="23b90-113">enabled</span></span>|<span data-ttu-id="23b90-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="23b90-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="23b90-115">Určuje, zda má být povoleno trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="23b90-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="23b90-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="23b90-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="23b90-117">Value</span><span class="sxs-lookup"><span data-stu-id="23b90-117">Value</span></span>|<span data-ttu-id="23b90-118">Popis</span><span class="sxs-lookup"><span data-stu-id="23b90-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23b90-119">true</span><span class="sxs-lookup"><span data-stu-id="23b90-119">true</span></span>|<span data-ttu-id="23b90-120">Povolte trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="23b90-120">Enable ETW.</span></span> <span data-ttu-id="23b90-121">Toto je výchozí nastavení pro verze Windows počínaje operačními systémy Windows Vista a Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="23b90-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="23b90-122">false</span><span class="sxs-lookup"><span data-stu-id="23b90-122">false</span></span>|<span data-ttu-id="23b90-123">Zakažte trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="23b90-123">Disable ETW.</span></span> <span data-ttu-id="23b90-124">Toto je výchozí nastavení pro dřívější verze systému Windows.</span><span class="sxs-lookup"><span data-stu-id="23b90-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23b90-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="23b90-125">Child Elements</span></span>  
 <span data-ttu-id="23b90-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="23b90-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23b90-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="23b90-127">Parent Elements</span></span>  
  
|<span data-ttu-id="23b90-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="23b90-128">Element</span></span>|<span data-ttu-id="23b90-129">Popis</span><span class="sxs-lookup"><span data-stu-id="23b90-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="23b90-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23b90-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="23b90-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="23b90-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b90-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23b90-132">Remarks</span></span>  
 <span data-ttu-id="23b90-133">Počínaje systémem Windows Vista je ETW ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="23b90-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="23b90-134">Tento prvek použijte k zakázání ETW pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="23b90-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="23b90-135">V dřívějších verzích Windows použijte tento prvek k povolení ETW pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="23b90-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23b90-136">ETW lze povolit nebo zakázat globálně na serveru pomocí nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="23b90-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="23b90-137">Viz [řízení protokolování .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="23b90-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b90-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="23b90-138">Example</span></span>  
 <span data-ttu-id="23b90-139">Následující příklad ukazuje, jak povolit trasování ETW pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="23b90-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23b90-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23b90-140">See also</span></span>

- [<span data-ttu-id="23b90-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="23b90-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="23b90-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="23b90-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="23b90-143">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="23b90-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
