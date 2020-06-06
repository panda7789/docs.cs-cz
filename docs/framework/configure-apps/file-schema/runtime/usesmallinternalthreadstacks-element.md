---
title: Element <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 2fd776ce8605e6dcf288dcb3852ded16638a1873
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73114926"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="de8c1-102">Element \<UseSmallInternalThreadStacks></span><span class="sxs-lookup"><span data-stu-id="de8c1-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="de8c1-103">Požadavky, které modul CLR (Common Language Runtime) omezuje využití paměti tím, že při vytváření určitých vláken, která používá interně, nepoužijí výchozí velikost zásobníku pro tato vlákna, a to zadáním explicitní velikosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="de8c1-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="de8c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de8c1-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de8c1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de8c1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="de8c1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de8c1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de8c1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="de8c1-107">Attributes</span></span>  
  
|<span data-ttu-id="de8c1-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="de8c1-108">Attribute</span></span>|<span data-ttu-id="de8c1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="de8c1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de8c1-110">enabled</span><span class="sxs-lookup"><span data-stu-id="de8c1-110">enabled</span></span>|<span data-ttu-id="de8c1-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="de8c1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="de8c1-112">Určuje, zda má být vyžádat, aby CLR používal explicitní velikosti zásobníku namísto výchozí velikosti zásobníku, když vytvoří určitá vlákna, která používá interně.</span><span class="sxs-lookup"><span data-stu-id="de8c1-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="de8c1-113">Explicitní velikosti zásobníku jsou menší než výchozí velikost zásobníku 1 MB.</span><span class="sxs-lookup"><span data-stu-id="de8c1-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="de8c1-114">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="de8c1-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="de8c1-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="de8c1-115">Value</span></span>|<span data-ttu-id="de8c1-116">Description</span><span class="sxs-lookup"><span data-stu-id="de8c1-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de8c1-117">true</span><span class="sxs-lookup"><span data-stu-id="de8c1-117">true</span></span>|<span data-ttu-id="de8c1-118">Požádejte o explicitní velikosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="de8c1-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="de8c1-119">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="de8c1-119">false</span></span>|<span data-ttu-id="de8c1-120">Použijte výchozí velikost zásobníku.</span><span class="sxs-lookup"><span data-stu-id="de8c1-120">Use the default stack size.</span></span> <span data-ttu-id="de8c1-121">Toto je výchozí nastavení pro .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="de8c1-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de8c1-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de8c1-122">Child Elements</span></span>  
 <span data-ttu-id="de8c1-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="de8c1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de8c1-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de8c1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="de8c1-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="de8c1-125">Element</span></span>|<span data-ttu-id="de8c1-126">Description</span><span class="sxs-lookup"><span data-stu-id="de8c1-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de8c1-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de8c1-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="de8c1-128">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="de8c1-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de8c1-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de8c1-129">Remarks</span></span>  
 <span data-ttu-id="de8c1-130">Tento prvek konfigurace se používá k vyžádání omezeného využití virtuální paměti v procesu, protože explicitní velikosti vláken, které modul CLR používá pro vnitřní vlákna, je-li požadavek splněn, je menší než výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="de8c1-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="de8c1-131">Tento prvek konfigurace je požadavek na CLR místo absolutního požadavku.</span><span class="sxs-lookup"><span data-stu-id="de8c1-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="de8c1-132">V .NET Framework 4 se požadavek splní jenom v architektuře x86.</span><span class="sxs-lookup"><span data-stu-id="de8c1-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="de8c1-133">Tento element může být zcela ignorován v budoucích verzích CLR nebo nahrazen explicitními velikostmi zásobníků, které jsou vždy použity pro vybraná interní vlákna.</span><span class="sxs-lookup"><span data-stu-id="de8c1-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="de8c1-134">Zadáním tohoto elementu konfigurace zajistíte spolehlivost pro menší využití virtuální paměti, pokud CLR požadavek splní, protože menší velikosti zásobníků by mohly způsobit vyšší natečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="de8c1-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de8c1-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="de8c1-135">Example</span></span>  
 <span data-ttu-id="de8c1-136">Následující příklad ukazuje, jak požadovat, aby CLR používal explicitní velikosti zásobníku pro určitá vlákna, která používá interně.</span><span class="sxs-lookup"><span data-stu-id="de8c1-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de8c1-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="de8c1-137">See also</span></span>

- [<span data-ttu-id="de8c1-138">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="de8c1-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="de8c1-139">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="de8c1-139">Configuration File Schema</span></span>](../index.md)
