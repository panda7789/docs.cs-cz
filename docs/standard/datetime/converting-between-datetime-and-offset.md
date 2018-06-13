---
title: Převádění mezi DateTime a DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dec0e5138ecf08783f11d21cd28d7291d27ea68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578245"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Převádění mezi DateTime a DateTimeOffset

I když <xref:System.DateTimeOffset> struktura nabízí vyšší úroveň povědomí o časovém pásmu než <xref:System.DateTime> struktury <xref:System.DateTime> parametry jsou častěji používají při volání metody. Z toho důvodu schopnost převést <xref:System.DateTimeOffset> hodnoty k <xref:System.DateTime> hodnoty a naopak je obzvláště důležité. Toto téma ukazuje, jak provést tyto převody způsobem, který zachovává co nejvíce informací časové pásmo.

> [!NOTE]
> Jak <xref:System.DateTime> a <xref:System.DateTimeOffset> typy mají určitá omezení, když představují časy v časových pásem. S jeho <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTime> může obsahovat pouze koordinovaný světový čas (UTC) a místní časové pásmo. <xref:System.DateTimeOffset> Zobrazuje čas posun od času UTC, ale neodráží aktuální časové pásmo, ke kterému posun patří. Podrobnosti o časových hodnotách a podpoře časových pásem najdete v tématu [volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Převod datového typu DateTime na DateTimeOffset

<xref:System.DateTimeOffset> Struktura poskytuje dva ekvivalentní způsoby, jak provést <xref:System.DateTime> k <xref:System.DateTimeOffset> převodu, které jsou vhodné pro většinu převodů:

* <xref:System.DateTimeOffset.%23ctor%2A> Konstruktor, který vytvoří nový <xref:System.DateTimeOffset> na základě objektu <xref:System.DateTime> hodnotu.

* Implicitní převod operátor, který umožňuje přiřadit <xref:System.DateTime> hodnotu <xref:System.DateTimeOffset> objektu.

Pro čas UTC a místní <xref:System.DateTime> hodnoty, <xref:System.DateTimeOffset.Offset%2A> vlastnost výsledná <xref:System.DateTimeOffset> hodnota přesně odráží posun pásma UTC nebo místního času. Například následující kód převede čas UTC na ekvivalentní <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

V tomto případě posun `utcTime2` proměnné je 00:00. Podobně následující kód převede místní čas na ekvivalentní <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ale pro <xref:System.DateTime> hodnoty, jehož <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, tyto dvě převod metody vytvoření <xref:System.DateTimeOffset> hodnota, jejíž posun je, že z místního časového pásma. To je znázorněno v následujícím příkladu, který běží v USA Tichomořském časovém pásmu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Pokud <xref:System.DateTime> odráží hodnota, datum a čas v něco jiného než v místním časovém pásmu nebo času UTC, můžete ji chcete převést <xref:System.DateTimeOffset> hodnotu a zachovat své informace o časovém pásmu voláním přetížené <xref:System.DateTimeOffset.%23ctor%2A> konstruktor. Například v následujícím příkladu vytvoří <xref:System.DateTimeOffset> objekt, který se vztahuje k centrální běžný čas.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Druhý parametr tohoto přetížení konstruktoru <xref:System.TimeSpan> objekt, který reprezentuje časový posun od času UTC, mají být načtena voláním <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> metoda časové odpovídajícího časového pásma. Jeden parametr metody je <xref:System.DateTime> hodnotu, která představuje datum a čas, který má být převeden. Pokud časové pásmo podporuje letní čas, tento parametr umožňuje metoda určit příslušné posun pro tento konkrétní datum a čas.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Převody z DateTimeOffset datum a čas

<xref:System.DateTimeOffset.DateTime%2A> Vlastnost se nejčastěji používá k provádění <xref:System.DateTimeOffset> k <xref:System.DateTime> převod. Avšak vrátí <xref:System.DateTime> hodnotu jehož <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified>, jak ukazuje následující příklad.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

To znamená, že všechny informace o <xref:System.DateTimeOffset> vztahu hodnoty na čas UTC je ztracena při převodu při <xref:System.DateTimeOffset.DateTime%2A> vlastnost se používá. Tato akce ovlivní <xref:System.DateTimeOffset> hodnot, které odpovídají čas UTC nebo místního času systému, protože <xref:System.DateTimeOffset.DateTime%2A> struktura odráží pouze dvě časová pásma v jeho <xref:System.DateTime.Kind%2A> vlastnost.

Chcete-li zachovat tolik informace o časovém pásmu jako možné při převodu <xref:System.DateTimeOffset> k <xref:System.DateTime> hodnotu, můžete použít <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnosti.

### <a name="converting-a-utc-time"></a>Převod času UTC

K označení, že převedená <xref:System.DateTimeOffset.DateTime%2A> hodnota je čas UTC, můžete načíst hodnotu <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> vlastnost. Liší se od <xref:System.DateTimeOffset.DateTime%2A> vlastnost dvěma způsoby:

* Vrátí <xref:System.DateTime> hodnotu jehož <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Utc>.

* Pokud <xref:System.DateTimeOffset.Offset%2A> hodnotu vlastnosti se nerovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, převede čas na čas UTC.

> [!NOTE]
> Pokud vaše aplikace vyžaduje, aby převést <xref:System.DateTime> hodnoty jednoznačně identifikovat jediný bod v čase, měli byste zvážit použití <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> vlastnost, aby se zpracovávaly všechny <xref:System.DateTimeOffset> k <xref:System.DateTime> převody.

Následující kód používá <xref:System.DateTimeOffset.UtcDateTime%2A> vlastnost převést <xref:System.DateTimeOffset> hodnota, jejíž posun se rovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType> k <xref:System.DateTime> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Následující kód používá <xref:System.DateTimeOffset.UtcDateTime%2A> vlastnost při převodu časového pásma a typ převod na <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Převod místního času

K označení, že <xref:System.DateTimeOffset> hodnota představuje místní čas, můžete předat <xref:System.DateTime> hodnoty vrácené <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> vlastnost, která má `static` (`Shared` v jazyce Visual Basic) <xref:System.DateTime.SpecifyKind%2A> metoda. Metoda vrátí datum a čas do ní předán jako svůj první parametr, ale nastaví <xref:System.DateTime.Kind%2A> vlastnost na hodnotu zadanou pomocí její druhý parametr. Následující kód používá <xref:System.DateTime.SpecifyKind%2A> metoda při převodu <xref:System.DateTimeOffset> hodnota, jejíž posun odpovídá posunu místního časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Můžete také <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost převést <xref:System.DateTimeOffset> hodnotu místní <xref:System.DateTime> hodnotu. <xref:System.DateTime.Kind%2A> Vlastnost vrácený <xref:System.DateTime> hodnota je <xref:System.DateTimeKind.Local>. Následující kód používá <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost při převodu <xref:System.DateTimeOffset> hodnota, jejíž posun odpovídá posunu místního časového pásma. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Při načtení <xref:System.DateTime> hodnotu pomocí <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost, vlastnosti `get` přistupující objekt nejprve převede <xref:System.DateTimeOffset> hodnotu na čas UTC, převede ji na místní čas voláním <xref:System.DateTimeOffset.ToLocalTime%2A> metoda. To znamená, že můžete načíst hodnotu z <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost, která má-li provést konverzi časové pásmo současně provést převod typů. Taky to znamená, že místní časovou zónu úpravu pravidla se používají při provádění převod. Následující kód ukazuje použití <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost k provádění typu a převodu časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda pro obecné účely převod

V následujícím příkladu definuje metodu s názvem `ConvertFromDateTimeOffset` , která převádí <xref:System.DateTimeOffset> hodnoty k <xref:System.DateTime> hodnoty. Na základě jeho posunu určuje, zda <xref:System.DateTimeOffset> hodnota je čas UTC, místní čas nebo později a definuje vrácený datum a čas hodnotu <xref:System.DateTime.Kind%2A> vlastnost odpovídajícím způsobem.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Následující příklad volá `ConvertFromDateTimeOffset` způsobů, jak převést <xref:System.DateTimeOffset> hodnoty, které představuje čas UTC, místní čas a čas v USA Střed standardního časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Všimněte si, že tento kód má dva předpoklady, které v závislosti na aplikaci a zdroj jeho hodnoty data a času, nemusí být vždy platný:

* Předpokládá, že datum a čas hodnotu jejíž posun je <xref:System.TimeSpan.Zero?displayProperty=nameWithType> představuje čas UTC. Ve skutečnosti UTC není čas v určitém časovém pásmu, ale čas ve vztahu k, které jsou standardizované časy v časových pásmech na světě. Časová pásma může mít posunem <xref:System.TimeSpan.Zero>.

* Předpokládá, že datum a čas, jejichž posun se rovná místní časovou zónu představuje místní časové pásmo. Protože hodnoty data a času nejsou přidruženy k původní časové pásmo, nemusí být případ. Datum a čas, můžete mít vytvořena v jiném časovém pásmu s posunem od stejné.

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
