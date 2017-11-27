---
title: "&lt;Netfx45_cultureawarecomparergethashcode_longstrings –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e21377b28adb7668108064b770c2c5e0f9fee8f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a><span data-ttu-id="afdec-102">&lt;Netfx45_cultureawarecomparergethashcode_longstrings –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="afdec-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element</span></span>
<span data-ttu-id="afdec-103">Určuje, zda modul runtime používá k výpočtu kódů hash pro pevné velikosti paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="afdec-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="afdec-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="afdec-104">\<configuration></span></span>  
<span data-ttu-id="afdec-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="afdec-105">\<runtime></span></span>  
<span data-ttu-id="afdec-106">< netfx45_cultureawarecomparergethashcode_longstrings – ></span><span class="sxs-lookup"><span data-stu-id="afdec-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afdec-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afdec-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afdec-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="afdec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="afdec-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="afdec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afdec-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="afdec-110">Attributes</span></span>  
  
|<span data-ttu-id="afdec-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="afdec-111">Attribute</span></span>|<span data-ttu-id="afdec-112">Popis</span><span class="sxs-lookup"><span data-stu-id="afdec-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="afdec-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="afdec-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="afdec-114">Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="afdec-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="afdec-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="afdec-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="afdec-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="afdec-116">Value</span></span>|<span data-ttu-id="afdec-117">Popis</span><span class="sxs-lookup"><span data-stu-id="afdec-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="afdec-118">0</span><span class="sxs-lookup"><span data-stu-id="afdec-118">0</span></span>|<span data-ttu-id="afdec-119">Modul common language runtime přiděluje proměnné množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="afdec-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="afdec-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="afdec-120">This is the default.</span></span>|  
|<span data-ttu-id="afdec-121">1</span><span class="sxs-lookup"><span data-stu-id="afdec-121">1</span></span>|<span data-ttu-id="afdec-122">Modul common language runtime přiděluje pevné velikosti paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="afdec-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afdec-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="afdec-123">Child Elements</span></span>  
 <span data-ttu-id="afdec-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="afdec-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afdec-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="afdec-125">Parent Elements</span></span>  
  
|<span data-ttu-id="afdec-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="afdec-126">Element</span></span>|<span data-ttu-id="afdec-127">Popis</span><span class="sxs-lookup"><span data-stu-id="afdec-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="afdec-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="afdec-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="afdec-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="afdec-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afdec-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afdec-130">Remarks</span></span>  
 <span data-ttu-id="afdec-131">Ve výchozím nastavení modul common language runtime přiděluje proměnné množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí výpočtu hash velké řetězců (přes několik mil. znaků).</span><span class="sxs-lookup"><span data-stu-id="afdec-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="afdec-132">Přidáním tohoto prvku do konfiguračního souboru aplikace a nastavení jeho `enabled` atributu na hodnotu "1", můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu používají alternativní algoritmus, který přiděluje pevné velikosti paměti pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="afdec-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="afdec-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element není používáno ve [!INCLUDE[win8](../../../../../includes/win8-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="afdec-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdec-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="afdec-134">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="afdec-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="afdec-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="afdec-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="afdec-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
