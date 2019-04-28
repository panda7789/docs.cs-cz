---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 854b58a1f57008326874b5e5ee60cc9e6297960b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674038"
---
# <a name="netfx45cultureawarecomparergethashcodelongstrings-element"></a><span data-ttu-id="438f7-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span><span class="sxs-lookup"><span data-stu-id="438f7-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>
<span data-ttu-id="438f7-103">Určuje, zda modul runtime používá pro výpočet kódů hash pro pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="438f7-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="438f7-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="438f7-104">\<configuration></span></span>  
<span data-ttu-id="438f7-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="438f7-105">\<runtime></span></span>  
<span data-ttu-id="438f7-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="438f7-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438f7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="438f7-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="438f7-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="438f7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="438f7-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="438f7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="438f7-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="438f7-110">Attributes</span></span>  
  
|<span data-ttu-id="438f7-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="438f7-111">Attribute</span></span>|<span data-ttu-id="438f7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="438f7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="438f7-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="438f7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="438f7-114">Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="438f7-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="438f7-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="438f7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="438f7-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="438f7-116">Value</span></span>|<span data-ttu-id="438f7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="438f7-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="438f7-118">0</span><span class="sxs-lookup"><span data-stu-id="438f7-118">0</span></span>|<span data-ttu-id="438f7-119">Modul common language runtime přiděluje variabilní velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="438f7-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="438f7-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="438f7-120">This is the default.</span></span>|  
|<span data-ttu-id="438f7-121">1</span><span class="sxs-lookup"><span data-stu-id="438f7-121">1</span></span>|<span data-ttu-id="438f7-122">Modul CLR přidělí pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="438f7-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="438f7-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="438f7-123">Child Elements</span></span>  
 <span data-ttu-id="438f7-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="438f7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="438f7-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="438f7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="438f7-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="438f7-126">Element</span></span>|<span data-ttu-id="438f7-127">Popis</span><span class="sxs-lookup"><span data-stu-id="438f7-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="438f7-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="438f7-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="438f7-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="438f7-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="438f7-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="438f7-130">Remarks</span></span>  
 <span data-ttu-id="438f7-131">Ve výchozím nastavení, modul common language runtime přiděluje variabilní velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody a <xref:System.ArgumentException> může být vyvolána, když se metoda se pokusí výpočtu kódů hash velmi dlouhých řetězců (přes několik milion znaků).</span><span class="sxs-lookup"><span data-stu-id="438f7-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="438f7-132">Přidáním tohoto prvku do konfiguračního souboru aplikace a nastavení jeho `enabled` atribut na hodnotu "1", můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda použila alternativní algoritmus, který pro výpočet kódů hash přidělí pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="438f7-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="438f7-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Není použit element v [!INCLUDE[win8](../../../../../includes/win8-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="438f7-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438f7-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="438f7-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="438f7-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="438f7-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="438f7-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="438f7-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
