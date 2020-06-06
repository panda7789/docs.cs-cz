---
title: Element <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117397"
---
# <a name="etwenable-element"></a><span data-ttu-id="21190-102">Element \<etwEnable></span><span class="sxs-lookup"><span data-stu-id="21190-102">\<etwEnable> Element</span></span>
<span data-ttu-id="21190-103">Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="21190-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="21190-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21190-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21190-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21190-105">Attributes and Elements</span></span>  
 <span data-ttu-id="21190-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21190-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21190-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="21190-107">Attributes</span></span>  
  
|<span data-ttu-id="21190-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="21190-108">Attribute</span></span>|<span data-ttu-id="21190-109">Popis</span><span class="sxs-lookup"><span data-stu-id="21190-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21190-110">enabled</span><span class="sxs-lookup"><span data-stu-id="21190-110">enabled</span></span>|<span data-ttu-id="21190-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="21190-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="21190-112">Určuje, zda má být povoleno trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="21190-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="21190-113">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="21190-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="21190-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="21190-114">Value</span></span>|<span data-ttu-id="21190-115">Description</span><span class="sxs-lookup"><span data-stu-id="21190-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="21190-116">true</span><span class="sxs-lookup"><span data-stu-id="21190-116">true</span></span>|<span data-ttu-id="21190-117">Povolte trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="21190-117">Enable ETW.</span></span> <span data-ttu-id="21190-118">Toto je výchozí nastavení pro verze Windows počínaje operačními systémy Windows Vista a Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="21190-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="21190-119">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="21190-119">false</span></span>|<span data-ttu-id="21190-120">Zakažte trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="21190-120">Disable ETW.</span></span> <span data-ttu-id="21190-121">Toto je výchozí nastavení pro dřívější verze systému Windows.</span><span class="sxs-lookup"><span data-stu-id="21190-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21190-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21190-122">Child Elements</span></span>  
 <span data-ttu-id="21190-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="21190-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21190-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21190-124">Parent Elements</span></span>  
  
|<span data-ttu-id="21190-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="21190-125">Element</span></span>|<span data-ttu-id="21190-126">Description</span><span class="sxs-lookup"><span data-stu-id="21190-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="21190-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21190-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="21190-128">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="21190-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21190-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21190-129">Remarks</span></span>  
 <span data-ttu-id="21190-130">Počínaje systémem Windows Vista je ETW ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="21190-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="21190-131">Tento prvek použijte k zakázání ETW pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="21190-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="21190-132">V dřívějších verzích Windows použijte tento prvek k povolení ETW pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="21190-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21190-133">ETW lze povolit nebo zakázat globálně na serveru pomocí nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="21190-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="21190-134">Viz [řízení protokolování .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="21190-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21190-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="21190-135">Example</span></span>  
 <span data-ttu-id="21190-136">Následující příklad ukazuje, jak povolit trasování ETW pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="21190-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21190-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="21190-137">See also</span></span>

- [<span data-ttu-id="21190-138">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="21190-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="21190-139">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="21190-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="21190-140">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21190-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
