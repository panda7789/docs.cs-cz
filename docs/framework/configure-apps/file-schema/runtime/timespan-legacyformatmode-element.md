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
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968910"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="cafff-102">Element \<TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="cafff-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="cafff-103">Určuje, zda modul runtime zachovává starší chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnotami.</span><span class="sxs-lookup"><span data-stu-id="cafff-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="cafff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cafff-104">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cafff-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cafff-105">Attributes and Elements</span></span>

<span data-ttu-id="cafff-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cafff-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cafff-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="cafff-107">Attributes</span></span>

|<span data-ttu-id="cafff-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="cafff-108">Attribute</span></span>|<span data-ttu-id="cafff-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cafff-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="cafff-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="cafff-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="cafff-111">Určuje, zda modul runtime používá chování formátování starší verze s <xref:System.TimeSpan?displayProperty=nameWithType> hodnotami.</span><span class="sxs-lookup"><span data-stu-id="cafff-111">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="cafff-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="cafff-112">enabled Attribute</span></span>

|<span data-ttu-id="cafff-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cafff-113">Value</span></span>|<span data-ttu-id="cafff-114">Description</span><span class="sxs-lookup"><span data-stu-id="cafff-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="cafff-115">Modul runtime neobnovuje chování při formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="cafff-115">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="cafff-116">Modul runtime obnoví chování formátování starší verze.</span><span class="sxs-lookup"><span data-stu-id="cafff-116">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="cafff-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cafff-117">Child Elements</span></span>

<span data-ttu-id="cafff-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="cafff-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cafff-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cafff-119">Parent Elements</span></span>

|<span data-ttu-id="cafff-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="cafff-120">Element</span></span>|<span data-ttu-id="cafff-121">Description</span><span class="sxs-lookup"><span data-stu-id="cafff-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="cafff-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cafff-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="cafff-123">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cafff-123">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cafff-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cafff-124">Remarks</span></span>

<span data-ttu-id="cafff-125">Počínaje .NET Framework 4 <xref:System.TimeSpan?displayProperty=nameWithType> struktura implementuje <xref:System.IFormattable> rozhraní a podporuje operace formátování pomocí standardních a vlastních formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="cafff-125">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="cafff-126">Pokud metoda analýzy narazí na nepodporovaný specifikátor formátu nebo formátovací řetězec, vyvolá <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="cafff-126">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="cafff-127">V předchozích verzích .NET Framework <xref:System.TimeSpan> Struktura neimplementovala <xref:System.IFormattable> a nepodporovala řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="cafff-127">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="cafff-128">Mnoho vývojářů však omylem nepředpokládalo, že <xref:System.TimeSpan> podporovaly sadu formátovacích řetězců a používají je ve [složených formátovacích operacích](../../../../standard/base-types/composite-formatting.md) s metodami, jako je například <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cafff-128">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cafff-129">V případě, že typ implementuje <xref:System.IFormattable> a podporuje řetězce formátu, volání metod formátování s nepodporovanými řetězci formátu obvykle vyvolají <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="cafff-129">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="cafff-130">Protože však <xref:System.TimeSpan> neimplementoval <xref:System.IFormattable> , modul runtime ignoruje řetězec formátu a místo toho se nazývá <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="cafff-130">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cafff-131">To znamená, že přestože formátovací řetězce neobsahovaly žádný vliv na operaci formátování, jejich přítomnost nezpůsobila <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="cafff-131">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="cafff-132">V případech, kdy starší verze kódu projde metodou složeného formátování a neplatným formátovacím řetězcem a tento kód nelze znovu zkompilovat, lze pomocí `<TimeSpan_LegacyFormatMode>` elementu obnovit starší verze <xref:System.TimeSpan> chování.</span><span class="sxs-lookup"><span data-stu-id="cafff-132">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="cafff-133">Když nastavíte `enabled` atribut tohoto elementu na `true` , metoda složeného formátování způsobí volání <xref:System.TimeSpan.ToString?displayProperty=nameWithType> namísto <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a není <xref:System.FormatException> vyvolána.</span><span class="sxs-lookup"><span data-stu-id="cafff-133">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="cafff-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="cafff-134">Example</span></span>

<span data-ttu-id="cafff-135">Následující příklad vytvoří instanci <xref:System.TimeSpan> objektu a pokusí se ho naformátovat pomocí <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metody pomocí nepodporovaného standardního formátovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="cafff-135">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="cafff-136">Když spustíte příklad na .NET Framework 3,5 nebo v dřívější verzi, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cafff-136">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="cafff-137">To se liší od výstupu, pokud spustíte příklad na .NET Framework 4 nebo novější verzi:</span><span class="sxs-lookup"><span data-stu-id="cafff-137">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="cafff-138">Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a potom spustíte příklad na .NET Framework 4 nebo novější verzi, výstup je stejný jako v příkladu, který je vytvořen v příkladu při spuštění v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="cafff-138">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="cafff-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="cafff-139">See also</span></span>

- [<span data-ttu-id="cafff-140">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="cafff-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cafff-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="cafff-141">Configuration File Schema</span></span>](../index.md)
