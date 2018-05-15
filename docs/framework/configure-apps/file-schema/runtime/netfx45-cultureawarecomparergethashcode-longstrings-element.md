---
title: '&lt;Netfx45_cultureawarecomparergethashcode_longstrings –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41fc4bc7a6a10a6f99752112f951b66f80d493fe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a><span data-ttu-id="8ffe9-102">&lt;Netfx45_cultureawarecomparergethashcode_longstrings –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="8ffe9-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element</span></span>
<span data-ttu-id="8ffe9-103">Určuje, zda modul runtime používá k výpočtu kódů hash pro pevné velikosti paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8ffe9-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8ffe9-104">\<configuration></span></span>  
<span data-ttu-id="8ffe9-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="8ffe9-105">\<runtime></span></span>  
<span data-ttu-id="8ffe9-106">< netfx45_cultureawarecomparergethashcode_longstrings – ></span><span class="sxs-lookup"><span data-stu-id="8ffe9-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ffe9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ffe9-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ffe9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8ffe9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8ffe9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ffe9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8ffe9-110">Attributes</span></span>  
  
|<span data-ttu-id="8ffe9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8ffe9-111">Attribute</span></span>|<span data-ttu-id="8ffe9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8ffe9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8ffe9-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8ffe9-114">Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8ffe9-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="8ffe9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8ffe9-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8ffe9-116">Value</span></span>|<span data-ttu-id="8ffe9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8ffe9-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ffe9-118">0</span><span class="sxs-lookup"><span data-stu-id="8ffe9-118">0</span></span>|<span data-ttu-id="8ffe9-119">Modul common language runtime přiděluje proměnné množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="8ffe9-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-120">This is the default.</span></span>|  
|<span data-ttu-id="8ffe9-121">1</span><span class="sxs-lookup"><span data-stu-id="8ffe9-121">1</span></span>|<span data-ttu-id="8ffe9-122">Modul common language runtime přiděluje pevné velikosti paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ffe9-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8ffe9-123">Child Elements</span></span>  
 <span data-ttu-id="8ffe9-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="8ffe9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ffe9-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8ffe9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8ffe9-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ffe9-126">Element</span></span>|<span data-ttu-id="8ffe9-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8ffe9-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8ffe9-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8ffe9-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ffe9-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ffe9-130">Remarks</span></span>  
 <span data-ttu-id="8ffe9-131">Ve výchozím nastavení modul common language runtime přiděluje proměnné množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí výpočtu hash velké řetězců (přes několik mil. znaků).</span><span class="sxs-lookup"><span data-stu-id="8ffe9-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="8ffe9-132">Přidáním tohoto prvku do konfiguračního souboru aplikace a nastavení jeho `enabled` atributu na hodnotu "1", můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu používají alternativní algoritmus, který přiděluje pevné velikosti paměti pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ffe9-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element není používáno ve [!INCLUDE[win8](../../../../../includes/win8-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="8ffe9-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffe9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ffe9-134">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8ffe9-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="8ffe9-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="8ffe9-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8ffe9-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
