---
title: "&lt;etwenable –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d94d49fcb2c395de5172a730923dbe42f67cf35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="a3185-102">&lt;etwenable –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="a3185-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="a3185-103">Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro běžné události modulu runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="a3185-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="a3185-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="a3185-104">\<configuration> Element</span></span>  
<span data-ttu-id="a3185-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="a3185-105">\<runtime> Element</span></span>  
<span data-ttu-id="a3185-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="a3185-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3185-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3185-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3185-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3185-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3185-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3185-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3185-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3185-110">Attributes</span></span>  
  
|<span data-ttu-id="a3185-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a3185-111">Attribute</span></span>|<span data-ttu-id="a3185-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a3185-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3185-113">povoleno</span><span class="sxs-lookup"><span data-stu-id="a3185-113">enabled</span></span>|<span data-ttu-id="a3185-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a3185-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3185-115">Určuje, zda se má povolit trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a3185-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a3185-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a3185-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="a3185-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a3185-117">Value</span></span>|<span data-ttu-id="a3185-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a3185-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a3185-119">true</span><span class="sxs-lookup"><span data-stu-id="a3185-119">true</span></span>|<span data-ttu-id="a3185-120">Povolte trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a3185-120">Enable ETW.</span></span> <span data-ttu-id="a3185-121">Toto je výchozí hodnota pro verze systému Windows od verze operačních systémů Windows Vista a Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a3185-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="a3185-122">false</span><span class="sxs-lookup"><span data-stu-id="a3185-122">false</span></span>|<span data-ttu-id="a3185-123">Zakážete trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a3185-123">Disable ETW.</span></span> <span data-ttu-id="a3185-124">Toto je výchozí hodnota u starších verzí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a3185-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3185-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3185-125">Child Elements</span></span>  
 <span data-ttu-id="a3185-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="a3185-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3185-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3185-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a3185-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3185-128">Element</span></span>|<span data-ttu-id="a3185-129">Popis</span><span class="sxs-lookup"><span data-stu-id="a3185-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a3185-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3185-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a3185-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a3185-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3185-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3185-132">Remarks</span></span>  
 <span data-ttu-id="a3185-133">Počínaje Windows Vista, je ve výchozím nastavení povolené trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a3185-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="a3185-134">Pomocí tohoto elementu zakázat trasování pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a3185-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="a3185-135">V dřívějších verzích systému Windows tento prvek slouží k povolení trasování pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a3185-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3185-136">Trasování událostí pro Windows můžete povolit nebo zakázat globálně na serveru pomocí nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="a3185-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="a3185-137">V tématu [řízení přihlašování rozhraní .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="a3185-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3185-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3185-138">Example</span></span>  
 <span data-ttu-id="a3185-139">Následující příklad ukazuje, jak povolit trasování událostí pro Windows pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a3185-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3185-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3185-140">See Also</span></span>  
 [<span data-ttu-id="a3185-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a3185-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a3185-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a3185-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a3185-143">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a3185-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
