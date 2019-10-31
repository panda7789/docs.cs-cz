---
title: Element <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115204"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="aa522-102">\<element > TimeSpan_LegacyFormatMode</span><span class="sxs-lookup"><span data-stu-id="aa522-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="aa522-103">Určuje, zda modul runtime zachovává starší chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnotami.</span><span class="sxs-lookup"><span data-stu-id="aa522-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="aa522-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aa522-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aa522-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="aa522-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="aa522-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**</span><span class="sxs-lookup"><span data-stu-id="aa522-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="aa522-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa522-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa522-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aa522-108">Attributes and Elements</span></span>

<span data-ttu-id="aa522-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aa522-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa522-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa522-110">Attributes</span></span>

|<span data-ttu-id="aa522-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="aa522-111">Attribute</span></span>|<span data-ttu-id="aa522-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aa522-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="aa522-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa522-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="aa522-114">Určuje, zda modul runtime používá chování při formátování starší verze s <xref:System.TimeSpan?displayProperty=nameWithType>mi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="aa522-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="aa522-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="aa522-115">enabled Attribute</span></span>

|<span data-ttu-id="aa522-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aa522-116">Value</span></span>|<span data-ttu-id="aa522-117">Popis</span><span class="sxs-lookup"><span data-stu-id="aa522-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="aa522-118">Modul runtime neobnovuje chování při formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="aa522-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="aa522-119">Modul runtime obnoví chování formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="aa522-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="aa522-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aa522-120">Child Elements</span></span>

<span data-ttu-id="aa522-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="aa522-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa522-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aa522-122">Parent Elements</span></span>

|<span data-ttu-id="aa522-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa522-123">Element</span></span>|<span data-ttu-id="aa522-124">Popis</span><span class="sxs-lookup"><span data-stu-id="aa522-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="aa522-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa522-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="aa522-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="aa522-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aa522-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa522-127">Remarks</span></span>

<span data-ttu-id="aa522-128">Počínaje .NET Framework 4 struktura <xref:System.TimeSpan?displayProperty=nameWithType> implementuje rozhraní <xref:System.IFormattable> a podporuje operace formátování pomocí standardních a vlastních formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="aa522-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="aa522-129">Pokud metoda analýzy narazí na nepodporovaný specifikátor formátu nebo formátovací řetězec, vyvolá <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="aa522-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="aa522-130">V předchozích verzích .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovala řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="aa522-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="aa522-131">Mnoho vývojářů však omylem nepředpokládalo, že <xref:System.TimeSpan> podporovala sadu formátovacích řetězců a použila je ve [složených operacích formátování](../../../../standard/base-types/composite-formatting.md) s metodami, jako je <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa522-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aa522-132">V případě, že typ implementuje <xref:System.IFormattable> a podporuje řetězce formátu, volání metod formátování s nepodporovanými řetězci formátu obvykle vyvolají <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="aa522-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="aa522-133">Vzhledem k tomu, že <xref:System.TimeSpan> neimplementoval <xref:System.IFormattable>, modul runtime ignoruje řetězec formátu a místo toho volal metodu <xref:System.TimeSpan.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa522-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="aa522-134">To znamená, že přestože formátovací řetězce neobsahovaly žádný vliv na operaci formátování, jejich přítomnost nemá za následek <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="aa522-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="aa522-135">V případech, kdy starší verze kódu projde metodou složeného formátování a neplatným formátovacím řetězcem, a tento kód nelze znovu zkompilovat, lze použít prvek `<TimeSpan_LegacyFormatMode>` k obnovení starších <xref:System.TimeSpan> chování.</span><span class="sxs-lookup"><span data-stu-id="aa522-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="aa522-136">Nastavíte-li atribut `enabled` tohoto prvku na hodnotu `true`, výsledkem metody složeného formátování je volání <xref:System.TimeSpan.ToString?displayProperty=nameWithType> spíše než <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="aa522-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="aa522-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa522-137">Example</span></span>

<span data-ttu-id="aa522-138">Následující příklad vytvoří instanci objektu <xref:System.TimeSpan> a pokusí se ho naformátovat pomocí metody <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> pomocí nepodporovaného standardního formátovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="aa522-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="aa522-139">Když spustíte příklad na .NET Framework 3,5 nebo v dřívější verzi, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="aa522-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="aa522-140">To se liší od výstupu, pokud spustíte příklad na .NET Framework 4 nebo novější verzi:</span><span class="sxs-lookup"><span data-stu-id="aa522-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="aa522-141">Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a potom spustíte příklad na .NET Framework 4 nebo novější verzi, výstup je stejný jako v příkladu, který je vytvořen v příkladu při spuštění v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="aa522-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="aa522-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa522-142">See also</span></span>

- [<span data-ttu-id="aa522-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="aa522-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aa522-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="aa522-144">Configuration File Schema</span></span>](../index.md)
