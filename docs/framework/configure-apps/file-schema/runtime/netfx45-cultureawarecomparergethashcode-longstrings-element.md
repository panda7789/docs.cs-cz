---
title: Element <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802109"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="1da6b-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span><span class="sxs-lookup"><span data-stu-id="1da6b-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="1da6b-103">Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="1da6b-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1da6b-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1da6b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1da6b-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1da6b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1da6b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**</span><span class="sxs-lookup"><span data-stu-id="1da6b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="1da6b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1da6b-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1da6b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1da6b-108">Attributes and Elements</span></span>

<span data-ttu-id="1da6b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1da6b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1da6b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1da6b-110">Attributes</span></span>

|<span data-ttu-id="1da6b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1da6b-111">Attribute</span></span>|<span data-ttu-id="1da6b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1da6b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1da6b-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1da6b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1da6b-114">Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="1da6b-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="1da6b-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="1da6b-115">enabled Attribute</span></span>

|<span data-ttu-id="1da6b-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1da6b-116">Value</span></span>|<span data-ttu-id="1da6b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1da6b-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="1da6b-118">0</span><span class="sxs-lookup"><span data-stu-id="1da6b-118">0</span></span>|<span data-ttu-id="1da6b-119">Modul CLR (Common Language Runtime) přiděluje proměnnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="1da6b-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="1da6b-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1da6b-120">This is the default.</span></span>|
|<span data-ttu-id="1da6b-121">1</span><span class="sxs-lookup"><span data-stu-id="1da6b-121">1</span></span>|<span data-ttu-id="1da6b-122">Modul CLR (Common Language Runtime) přiděluje pevnou velikost paměti pro metodu <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> k výpočtu kódů hash.</span><span class="sxs-lookup"><span data-stu-id="1da6b-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1da6b-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1da6b-123">Child Elements</span></span>

<span data-ttu-id="1da6b-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="1da6b-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1da6b-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1da6b-125">Parent Elements</span></span>

|<span data-ttu-id="1da6b-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="1da6b-126">Element</span></span>|<span data-ttu-id="1da6b-127">Popis</span><span class="sxs-lookup"><span data-stu-id="1da6b-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1da6b-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1da6b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1da6b-129">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1da6b-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1da6b-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1da6b-130">Remarks</span></span>

<span data-ttu-id="1da6b-131">Ve výchozím nastavení modul CLR (Common Language Runtime) přiděluje proměnlivou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí vypočítat hash kód velmi velkých řetězců (více než 1 milion znaků).</span><span class="sxs-lookup"><span data-stu-id="1da6b-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="1da6b-132">Přidáním tohoto elementu do konfiguračního souboru aplikace a nastavením jeho `enabled` atributu na hodnotu "1" můžete určit, že metoda <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> používá alternativní algoritmus, který přiděluje pevnou velikost paměti pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="1da6b-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1da6b-133">Element `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` se nepoužívá v systému Windows 8 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="1da6b-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="1da6b-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1da6b-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1da6b-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="1da6b-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1da6b-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="1da6b-136">Configuration File Schema</span></span>](../index.md)
