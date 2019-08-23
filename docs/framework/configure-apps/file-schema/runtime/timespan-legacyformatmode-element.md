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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f16a2bbd2470b4aec9e95ab67ccb0e736c4c6d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920692"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="58ff0-102">\<TimeSpan_LegacyFormatMode – element ></span><span class="sxs-lookup"><span data-stu-id="58ff0-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="58ff0-103">Určuje, zda modul runtime zachovává starší chování při formátování operací <xref:System.TimeSpan?displayProperty=nameWithType> s hodnotami.</span><span class="sxs-lookup"><span data-stu-id="58ff0-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="58ff0-104">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="58ff0-104">\<configuration></span></span>\
<span data-ttu-id="58ff0-105">\<běhové > </span><span class="sxs-lookup"><span data-stu-id="58ff0-105">\<runtime></span></span>\
<span data-ttu-id="58ff0-106">\<TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="58ff0-106">\<TimeSpan_LegacyFormatMode></span></span>

## <a name="syntax"></a><span data-ttu-id="58ff0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58ff0-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="58ff0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58ff0-108">Attributes and Elements</span></span>

<span data-ttu-id="58ff0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58ff0-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="58ff0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="58ff0-110">Attributes</span></span>

|<span data-ttu-id="58ff0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="58ff0-111">Attribute</span></span>|<span data-ttu-id="58ff0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="58ff0-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="58ff0-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="58ff0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="58ff0-114">Určuje, zda modul runtime používá chování formátování starší <xref:System.TimeSpan?displayProperty=nameWithType> verze s hodnotami.</span><span class="sxs-lookup"><span data-stu-id="58ff0-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="58ff0-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="58ff0-115">enabled Attribute</span></span>

|<span data-ttu-id="58ff0-116">Value</span><span class="sxs-lookup"><span data-stu-id="58ff0-116">Value</span></span>|<span data-ttu-id="58ff0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="58ff0-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="58ff0-118">Modul runtime neobnovuje chování při formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="58ff0-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="58ff0-119">Modul runtime obnoví chování formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="58ff0-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="58ff0-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58ff0-120">Child Elements</span></span>

<span data-ttu-id="58ff0-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="58ff0-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="58ff0-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58ff0-122">Parent Elements</span></span>

|<span data-ttu-id="58ff0-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="58ff0-123">Element</span></span>|<span data-ttu-id="58ff0-124">Popis</span><span class="sxs-lookup"><span data-stu-id="58ff0-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="58ff0-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58ff0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="58ff0-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="58ff0-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="58ff0-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58ff0-127">Remarks</span></span>

<span data-ttu-id="58ff0-128">Počínaje .NET Framework 4 <xref:System.TimeSpan?displayProperty=nameWithType> struktura <xref:System.IFormattable> implementuje rozhraní a podporuje operace formátování pomocí standardních a vlastních formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="58ff0-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="58ff0-129">Pokud metoda analýzy narazí na nepodporovaný specifikátor formátu nebo formátovací řetězec, vyvolá <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="58ff0-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="58ff0-130">V předchozích verzích .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovala řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="58ff0-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="58ff0-131">Mnoho vývojářů však omylem nepředpokládalo <xref:System.TimeSpan> , že podporovaly sadu formátovacích řetězců a používají je ve [složených formátovacích operacích](../../../../standard/base-types/composite-formatting.md) s <xref:System.String.Format%2A?displayProperty=nameWithType>metodami, jako je například.</span><span class="sxs-lookup"><span data-stu-id="58ff0-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58ff0-132">V případě, že typ implementuje <xref:System.IFormattable> a podporuje řetězce formátu, volání metod formátování s nepodporovanými řetězci formátu obvykle <xref:System.FormatException>vyvolají.</span><span class="sxs-lookup"><span data-stu-id="58ff0-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="58ff0-133">Protože <xref:System.TimeSpan> však neimplementoval <xref:System.IFormattable>, modul runtime ignoruje <xref:System.TimeSpan.ToString?displayProperty=nameWithType> řetězec formátu a místo toho se nazývá metoda.</span><span class="sxs-lookup"><span data-stu-id="58ff0-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="58ff0-134">To znamená, že přestože formátovací řetězce neobsahovaly žádný vliv na operaci formátování, jejich přítomnost nezpůsobila <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="58ff0-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="58ff0-135">V případech, kdy starší verze kódu projde metodou složeného formátování a neplatným formátovacím řetězcem a tento kód nelze znovu zkompilovat, lze pomocí `<TimeSpan_LegacyFormatMode>` elementu obnovit starší verze <xref:System.TimeSpan> chování.</span><span class="sxs-lookup"><span data-stu-id="58ff0-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="58ff0-136">Když `enabled` nastavíte atribut tohoto elementu na `true`, metoda složeného formátování <xref:System.TimeSpan.ToString?displayProperty=nameWithType> způsobí volání namísto <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="58ff0-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="58ff0-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="58ff0-137">Example</span></span>

<span data-ttu-id="58ff0-138">Následující příklad vytvoří instanci <xref:System.TimeSpan> objektu a pokusí se ho naformátovat <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> pomocí metody pomocí nepodporovaného standardního formátovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="58ff0-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="58ff0-139">Když spustíte příklad na .NET Framework 3,5 nebo v dřívější verzi, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58ff0-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="58ff0-140">To se liší od výstupu, pokud spustíte příklad na .NET Framework 4 nebo novější verzi:</span><span class="sxs-lookup"><span data-stu-id="58ff0-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="58ff0-141">Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a potom spustíte příklad na .NET Framework 4 nebo novější verzi, výstup je stejný jako v příkladu, který je vytvořen v příkladu při spuštění v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="58ff0-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="58ff0-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58ff0-142">See also</span></span>

- [<span data-ttu-id="58ff0-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="58ff0-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="58ff0-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="58ff0-144">Configuration File Schema</span></span>](../index.md)
