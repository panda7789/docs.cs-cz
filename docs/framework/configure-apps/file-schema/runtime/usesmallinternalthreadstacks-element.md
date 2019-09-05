---
title: Element <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 515ea076c5eaead50b41e45e415725d0439914bc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252210"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="c39c8-102">\<UseSmallInternalThreadStacks – element ></span><span class="sxs-lookup"><span data-stu-id="c39c8-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="c39c8-103">Požadavky, které modul CLR (Common Language Runtime) omezuje využití paměti tím, že při vytváření určitých vláken, která používá interně, nepoužijí výchozí velikost zásobníku pro tato vlákna, a to zadáním explicitní velikosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c39c8-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
<span data-ttu-id="c39c8-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c39c8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c39c8-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c39c8-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c39c8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseSmallInternalThreadStacks>**</span><span class="sxs-lookup"><span data-stu-id="c39c8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c39c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c39c8-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c39c8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c39c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c39c8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c39c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c39c8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c39c8-110">Attributes</span></span>  
  
|<span data-ttu-id="c39c8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c39c8-111">Attribute</span></span>|<span data-ttu-id="c39c8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c39c8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c39c8-113">enabled</span><span class="sxs-lookup"><span data-stu-id="c39c8-113">enabled</span></span>|<span data-ttu-id="c39c8-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c39c8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c39c8-115">Určuje, zda má být vyžádat, aby CLR používal explicitní velikosti zásobníku namísto výchozí velikosti zásobníku, když vytvoří určitá vlákna, která používá interně.</span><span class="sxs-lookup"><span data-stu-id="c39c8-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="c39c8-116">Explicitní velikosti zásobníku jsou menší než výchozí velikost zásobníku 1 MB.</span><span class="sxs-lookup"><span data-stu-id="c39c8-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c39c8-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="c39c8-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="c39c8-118">Value</span><span class="sxs-lookup"><span data-stu-id="c39c8-118">Value</span></span>|<span data-ttu-id="c39c8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c39c8-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c39c8-120">true</span><span class="sxs-lookup"><span data-stu-id="c39c8-120">true</span></span>|<span data-ttu-id="c39c8-121">Požádejte o explicitní velikosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c39c8-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="c39c8-122">false</span><span class="sxs-lookup"><span data-stu-id="c39c8-122">false</span></span>|<span data-ttu-id="c39c8-123">Použijte výchozí velikost zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c39c8-123">Use the default stack size.</span></span> <span data-ttu-id="c39c8-124">Toto je výchozí nastavení pro .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c39c8-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c39c8-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c39c8-125">Child Elements</span></span>  
 <span data-ttu-id="c39c8-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="c39c8-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c39c8-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c39c8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c39c8-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="c39c8-128">Element</span></span>|<span data-ttu-id="c39c8-129">Popis</span><span class="sxs-lookup"><span data-stu-id="c39c8-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c39c8-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c39c8-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c39c8-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c39c8-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c39c8-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c39c8-132">Remarks</span></span>  
 <span data-ttu-id="c39c8-133">Tento prvek konfigurace se používá k vyžádání omezeného využití virtuální paměti v procesu, protože explicitní velikosti vláken, které modul CLR používá pro vnitřní vlákna, je-li požadavek splněn, je menší než výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="c39c8-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c39c8-134">Tento prvek konfigurace je požadavek na CLR místo absolutního požadavku.</span><span class="sxs-lookup"><span data-stu-id="c39c8-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="c39c8-135">V .NET Framework 4 se požadavek splní jenom v architektuře x86.</span><span class="sxs-lookup"><span data-stu-id="c39c8-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="c39c8-136">Tento element může být zcela ignorován v budoucích verzích CLR nebo nahrazen explicitními velikostmi zásobníků, které jsou vždy použity pro vybraná interní vlákna.</span><span class="sxs-lookup"><span data-stu-id="c39c8-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="c39c8-137">Zadáním tohoto elementu konfigurace zajistíte spolehlivost pro menší využití virtuální paměti, pokud CLR požadavek splní, protože menší velikosti zásobníků by mohly způsobit vyšší natečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c39c8-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c39c8-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="c39c8-138">Example</span></span>  
 <span data-ttu-id="c39c8-139">Následující příklad ukazuje, jak požadovat, aby CLR používal explicitní velikosti zásobníku pro určitá vlákna, která používá interně.</span><span class="sxs-lookup"><span data-stu-id="c39c8-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c39c8-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c39c8-140">See also</span></span>

- [<span data-ttu-id="c39c8-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="c39c8-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c39c8-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c39c8-142">Configuration File Schema</span></span>](../index.md)
