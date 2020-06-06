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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802109"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="20369-102">Element \<NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="20369-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="20369-103">Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="20369-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="20369-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20369-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20369-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="20369-105">Attributes and Elements</span></span>

<span data-ttu-id="20369-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20369-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="20369-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="20369-107">Attributes</span></span>

|<span data-ttu-id="20369-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="20369-108">Attribute</span></span>|<span data-ttu-id="20369-109">Popis</span><span class="sxs-lookup"><span data-stu-id="20369-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="20369-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="20369-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="20369-111">Určuje, zda modul Common Language Runtime (CLR) přidělí při výpočtu kódů hash pevnou velikost paměti.</span><span class="sxs-lookup"><span data-stu-id="20369-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="20369-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="20369-112">enabled Attribute</span></span>

|<span data-ttu-id="20369-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="20369-113">Value</span></span>|<span data-ttu-id="20369-114">Description</span><span class="sxs-lookup"><span data-stu-id="20369-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="20369-115">0</span><span class="sxs-lookup"><span data-stu-id="20369-115">0</span></span>|<span data-ttu-id="20369-116">Modul CLR (Common Language Runtime) přiděluje proměnnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu výpočtu kódů hash.</span><span class="sxs-lookup"><span data-stu-id="20369-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="20369-117">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="20369-117">This is the default.</span></span>|
|<span data-ttu-id="20369-118">1</span><span class="sxs-lookup"><span data-stu-id="20369-118">1</span></span>|<span data-ttu-id="20369-119">Modul CLR (Common Language Runtime) přiděluje pevnou velikost paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu výpočtu kódů hash.</span><span class="sxs-lookup"><span data-stu-id="20369-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="20369-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="20369-120">Child Elements</span></span>

<span data-ttu-id="20369-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="20369-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20369-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="20369-122">Parent Elements</span></span>

|<span data-ttu-id="20369-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="20369-123">Element</span></span>|<span data-ttu-id="20369-124">Description</span><span class="sxs-lookup"><span data-stu-id="20369-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="20369-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20369-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="20369-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="20369-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20369-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20369-127">Remarks</span></span>

<span data-ttu-id="20369-128">Ve výchozím nastavení modul CLR (Common Language Runtime) přiděluje proměnlivé množství paměti pro <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodu a <xref:System.ArgumentException> může být vyvolána, když se metoda pokusí vypočítat hash kód velmi velkých řetězců (více než 1 milion znaků).</span><span class="sxs-lookup"><span data-stu-id="20369-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="20369-129">Přidáním tohoto elementu do konfiguračního souboru aplikace a nastavením jeho `enabled` atributu na hodnotu "1" můžete určit, že <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> Metoda používá alternativní algoritmus, který přiděluje pevnou velikost paměti pro výpočet kódů hash.</span><span class="sxs-lookup"><span data-stu-id="20369-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20369-130">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Element se nepoužívá v systému Windows 8 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="20369-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="20369-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="20369-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="20369-132">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="20369-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="20369-133">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="20369-133">Configuration File Schema</span></span>](../index.md)
