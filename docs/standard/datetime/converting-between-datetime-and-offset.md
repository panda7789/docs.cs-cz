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
ms.openlocfilehash: d4bce84d26e8f498f065c887b583e18d8ea7c786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61901924"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Převádění mezi DateTime a DateTimeOffset

I když <xref:System.DateTimeOffset> struktura zajišťuje vyšší stupeň časové pásmo než <xref:System.DateTime> strukturu, <xref:System.DateTime> ve volání metody se běžně používají parametry. Z toho důvodu schopnost převést <xref:System.DateTimeOffset> hodnoty <xref:System.DateTime> hodnoty a naopak je zvlášť důležité. Toto téma ukazuje, jak k provádění těchto převodů způsobem, který uchovává co nejvíce informací časové pásmo.

> [!NOTE]
> Jak <xref:System.DateTime> a <xref:System.DateTimeOffset> typy mají určitá omezení, když představují časy v časových pásmech. S jeho <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTime> může reflektovat pouze koordinovaný univerzální čas (UTC) a místní časové pásmo systému. <xref:System.DateTimeOffset> odráží časový posun od času UTC, ale neodráží aktuální časové pásmo, ke kterému posun patří. Podrobnosti o časové hodnoty a podpora pro časová pásma najdete v tématu [volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Převody z data a času do struktury DateTimeOffset

<xref:System.DateTimeOffset> Struktura poskytuje dva způsoby ekvivalentní k provedení <xref:System.DateTime> k <xref:System.DateTimeOffset> převodu, které jsou vhodné pro většinu převody:

* <xref:System.DateTimeOffset.%23ctor%2A> Konstruktor, který vytvoří nový <xref:System.DateTimeOffset> objektu na základě <xref:System.DateTime> hodnotu.

* Operátor implicitního převodu, který vám umožní přiřadit <xref:System.DateTime> hodnota, která se <xref:System.DateTimeOffset> objektu.

Pro čas UTC a místním <xref:System.DateTime> hodnot, <xref:System.DateTimeOffset.Offset%2A> vlastnost výsledné <xref:System.DateTimeOffset> hodnotu přesně odráží posun UTC nebo místního času. Například následující kód převede čas UTC na její ekvivalentní <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

V takovém případě posun `utcTime2` proměnná je 00:00. Podobně, následující kód převede místní čas na její ekvivalentní <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ale pro <xref:System.DateTime> hodnoty, jejichž <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, tyto převod dvě metody vytvoření <xref:System.DateTimeOffset> hodnota, jejíž posun je posun místního časového pásma. To je ukázáno v následujícím příkladu, který běží v USA. Tichomořském časovém pásmu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Pokud <xref:System.DateTime> hodnota odráží datum a čas ve něco jiného než místního časového pásma nebo čas UTC, můžete ji převést <xref:System.DateTimeOffset> hodnotu a zachování její informace o časovém pásmu voláním přetížené <xref:System.DateTimeOffset.%23ctor%2A> konstruktoru. Například následující příklad vytvoří instance <xref:System.DateTimeOffset> objekt, který odráží – střed (běžný čas).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Druhý parametr tohoto přetížení konstruktoru <xref:System.TimeSpan> objekt, který představuje časový posun od času UTC, by měl být načten voláním <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> metoda času od odpovídajícího časového pásma. Jediný parametr metody je <xref:System.DateTime> hodnotu, která představuje datum a čas, který má být převeden. Podporuje-li časové pásmo letního času, tento parametr umožňuje metodou ke zjištění odpovídající posun pro tento konkrétní datum a čas.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Převody z DateTimeOffset na data a času

<xref:System.DateTimeOffset.DateTime%2A> Vlastnost se nejčastěji používá k provedení <xref:System.DateTimeOffset> k <xref:System.DateTime> převodu. Vrátí se však <xref:System.DateTime> jehož hodnota <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified>, jak ukazuje následující příklad.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

To znamená, že všechny informace o <xref:System.DateTimeOffset> vztahu hodnoty na čas UTC je ztracena při převodu při <xref:System.DateTimeOffset.DateTime%2A> vlastnost se používá. Tato akce ovlivní <xref:System.DateTimeOffset> hodnoty, které odpovídají na čas UTC nebo místního času v systému, protože <xref:System.DateTimeOffset.DateTime%2A> struktura odráží pouze dva časových pásem v jeho <xref:System.DateTime.Kind%2A> vlastnost.

Pro zachování co nejvíce informací časové pásmo při převodu <xref:System.DateTimeOffset> k <xref:System.DateTime> hodnotu, můžete použít <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnosti.

### <a name="converting-a-utc-time"></a>Převod času UTC

Označuje, že převedená <xref:System.DateTimeOffset.DateTime%2A> hodnotu času UTC, můžete načíst hodnotu <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> vlastnost. Se liší od <xref:System.DateTimeOffset.DateTime%2A> vlastnost dvěma způsoby:

* Vrátí <xref:System.DateTime> hodnota, jejíž <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc>.

* Pokud <xref:System.DateTimeOffset.Offset%2A> není rovno hodnota vlastnosti <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, převede čas na čas UTC.

> [!NOTE]
> Pokud vaše aplikace vyžaduje, aby převést <xref:System.DateTime> hodnoty jednoznačně identifikují jediný bod v čase, měli byste zvážit použití <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> vlastnost, aby se zpracovávaly všechny <xref:System.DateTimeOffset> k <xref:System.DateTime> převody.

Následující kód používá <xref:System.DateTimeOffset.UtcDateTime%2A> vlastnost převést <xref:System.DateTimeOffset> hodnota, jejíž posun se rovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType> k <xref:System.DateTime> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Následující kód používá <xref:System.DateTimeOffset.UtcDateTime%2A> vlastnost k provedení převodu časového pásma a převod typu na <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Převod místní čas

Označuje, že <xref:System.DateTimeOffset> hodnota představuje místní čas, můžete předat <xref:System.DateTime> hodnoty vrácené <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> vlastnost `static` (`Shared` v jazyce Visual Basic) <xref:System.DateTime.SpecifyKind%2A> metoda. Metoda vrátí datum a čas do něho předaný jako svůj první parametr, ale nastaví <xref:System.DateTime.Kind%2A> vlastnost na hodnotu zadanou pomocí její druhý parametr. Následující kód používá <xref:System.DateTime.SpecifyKind%2A> metoda při převodu <xref:System.DateTimeOffset> hodnota, jejíž posun odpovídá u místního časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Můžete také použít <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost převést <xref:System.DateTimeOffset> hodnota, která má místní <xref:System.DateTime> hodnotu. <xref:System.DateTime.Kind%2A> Vlastnost vráceného <xref:System.DateTime> hodnotu <xref:System.DateTimeKind.Local>. Následující kód používá <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost při převodu <xref:System.DateTimeOffset> hodnota, jejíž posun odpovídá u místního časového pásma. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Při načtení <xref:System.DateTime> hodnotu pomocí <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnosti, vlastnosti `get` přistupující objekt nejprve převede <xref:System.DateTimeOffset> hodnotu na čas UTC, převede ho na místní čas voláním <xref:System.DateTimeOffset.ToLocalTime%2A> metoda. To znamená, že můžete načíst hodnotu z <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost k provedení převodu časového pásma ve stejnou dobu, že provádíte převod typů. Také znamená, že při provádění převodu se použijí pravidla úpravy místního časového pásma. Následující kód ukazuje použití <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost typu a převodu časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda převodu pro obecné účely

Následující příklad definuje metodu s názvem `ConvertFromDateTimeOffset` , která převede <xref:System.DateTimeOffset> hodnoty <xref:System.DateTime> hodnoty. Na základě jeho posunu, určuje, zda <xref:System.DateTimeOffset> hodnota je čas UTC nebo místního času, nějakou dobu a definuje vrácené datum a čas hodnotu <xref:System.DateTime.Kind%2A> vlastnost odpovídajícím způsobem.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Následující příklad volá `ConvertFromDateTimeOffset` způsobů, jak převést <xref:System.DateTimeOffset> hodnoty, které představuje čas UTC, místní čas a čas v USA. Centrální standardního časového pásma.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Všimněte si, že tento kód vytvoří dva předpoklady, které v závislosti na aplikaci a zdroj jeho hodnoty data a času, nemusí být vždy platný:

* Předpokládá, že datum a čas hodnota, jejíž posun je <xref:System.TimeSpan.Zero?displayProperty=nameWithType> představuje čas UTC. Ve skutečnosti UTC není čas v určitém časovém pásmu, ale čas, u kterých jsou standardizované časy v časových pásmech na světě. Časová pásma může mít také posun <xref:System.TimeSpan.Zero>.

* Předpokládá, že datum a čas, jejíž posun se rovná u místní časové pásmo představuje místní časové pásmo. Protože hodnoty data a času jsou oddělen od původní časové pásmo, nemusí to být případ. Datum a čas může být vytvořená v jiném časovém pásmu se stejný posun.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
