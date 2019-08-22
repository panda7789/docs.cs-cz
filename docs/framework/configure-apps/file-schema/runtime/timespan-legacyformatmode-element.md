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
ms.openlocfilehash: 2bd74460c7d5d077686c723936d140b07ac21dd0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663397"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="20965-102">\<TimeSpan_LegacyFormatMode – element ></span><span class="sxs-lookup"><span data-stu-id="20965-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="20965-103">Určuje, zda modul runtime zachovává starší chování při formátování operací <xref:System.TimeSpan?displayProperty=nameWithType> s hodnotami.</span><span class="sxs-lookup"><span data-stu-id="20965-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="20965-104">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="20965-104">\<configuration></span></span>\
<span data-ttu-id="20965-105">\<běhové > </span><span class="sxs-lookup"><span data-stu-id="20965-105">\<runtime></span></span>\
<span data-ttu-id="20965-106">\<TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="20965-106">\<TimeSpan_LegacyFormatMode></span></span>

## <a name="syntax"></a><span data-ttu-id="20965-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20965-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20965-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="20965-108">Attributes and Elements</span></span>

<span data-ttu-id="20965-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20965-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="20965-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="20965-110">Attributes</span></span>

|<span data-ttu-id="20965-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="20965-111">Attribute</span></span>|<span data-ttu-id="20965-112">Popis</span><span class="sxs-lookup"><span data-stu-id="20965-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="20965-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="20965-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="20965-114">Určuje, zda modul runtime používá chování formátování starší <xref:System.TimeSpan?displayProperty=nameWithType> verze s hodnotami.</span><span class="sxs-lookup"><span data-stu-id="20965-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="20965-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="20965-115">enabled Attribute</span></span>

|<span data-ttu-id="20965-116">Value</span><span class="sxs-lookup"><span data-stu-id="20965-116">Value</span></span>|<span data-ttu-id="20965-117">Popis</span><span class="sxs-lookup"><span data-stu-id="20965-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="20965-118">Modul runtime neobnovuje chování při formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="20965-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="20965-119">Modul runtime obnoví chování formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="20965-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="20965-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="20965-120">Child Elements</span></span>

<span data-ttu-id="20965-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="20965-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20965-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="20965-122">Parent Elements</span></span>

|<span data-ttu-id="20965-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="20965-123">Element</span></span>|<span data-ttu-id="20965-124">Popis</span><span class="sxs-lookup"><span data-stu-id="20965-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="20965-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20965-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="20965-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="20965-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20965-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20965-127">Remarks</span></span>

<span data-ttu-id="20965-128">Počínaje .NET Framework 4 <xref:System.TimeSpan?displayProperty=nameWithType> struktura <xref:System.IFormattable> implementuje rozhraní a podporuje operace formátování pomocí standardních a vlastních formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="20965-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="20965-129">Pokud metoda analýzy narazí na nepodporovaný specifikátor formátu nebo formátovací řetězec, vyvolá <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="20965-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="20965-130">V předchozích verzích .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovala řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="20965-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="20965-131">Mnoho vývojářů však omylem nepředpokládalo <xref:System.TimeSpan> , že podporovaly sadu formátovacích řetězců a používají je ve [složených formátovacích operacích](../../../../../docs/standard/base-types/composite-formatting.md) s <xref:System.String.Format%2A?displayProperty=nameWithType>metodami, jako je například.</span><span class="sxs-lookup"><span data-stu-id="20965-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="20965-132">V případě, že typ implementuje <xref:System.IFormattable> a podporuje řetězce formátu, volání metod formátování s nepodporovanými řetězci formátu obvykle <xref:System.FormatException>vyvolají.</span><span class="sxs-lookup"><span data-stu-id="20965-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="20965-133">Protože <xref:System.TimeSpan> však neimplementoval <xref:System.IFormattable>, modul runtime ignoruje <xref:System.TimeSpan.ToString?displayProperty=nameWithType> řetězec formátu a místo toho se nazývá metoda.</span><span class="sxs-lookup"><span data-stu-id="20965-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="20965-134">To znamená, že přestože formátovací řetězce neobsahovaly žádný vliv na operaci formátování, jejich přítomnost nezpůsobila <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="20965-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="20965-135">V případech, kdy starší verze kódu projde metodou složeného formátování a neplatným formátovacím řetězcem a tento kód nelze znovu zkompilovat, lze pomocí `<TimeSpan_LegacyFormatMode>` elementu obnovit starší verze <xref:System.TimeSpan> chování.</span><span class="sxs-lookup"><span data-stu-id="20965-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="20965-136">Když `enabled` nastavíte atribut tohoto elementu na `true`, metoda složeného formátování <xref:System.TimeSpan.ToString?displayProperty=nameWithType> způsobí volání namísto <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="20965-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="20965-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="20965-137">Example</span></span>

<span data-ttu-id="20965-138">Následující příklad vytvoří instanci <xref:System.TimeSpan> objektu a pokusí se ho naformátovat <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> pomocí metody pomocí nepodporovaného standardního formátovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="20965-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="20965-139">Když spustíte příklad na .NET Framework 3,5 nebo v dřívější verzi, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="20965-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="20965-140">To se liší od výstupu, pokud spustíte příklad na .NET Framework 4 nebo novější verzi:</span><span class="sxs-lookup"><span data-stu-id="20965-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="20965-141">Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a potom spustíte příklad na .NET Framework 4 nebo novější verzi, výstup je stejný jako v příkladu, který je vytvořen v příkladu při spuštění v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="20965-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="20965-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20965-142">See also</span></span>

- [<span data-ttu-id="20965-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="20965-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="20965-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="20965-144">Configuration File Schema</span></span>](../index.md)
