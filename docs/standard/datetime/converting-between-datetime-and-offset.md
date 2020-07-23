---
title: Převádění mezi DateTime a DateTimeOffset
description: Převod mezi hodnotami DateTimeOffset a hodnotami DateTime v rozhraní .NET. Struktura DateTimeOffset poskytuje větší povědomí o časovém pásmu než struktura data a času.
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
ms.openlocfilehash: 86f2c982d7f87e83102933d1de73d6e13086dc87
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924900"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Převádění mezi DateTime a DateTimeOffset

I když <xref:System.DateTimeOffset> Struktura poskytuje větší stupeň povědomí o časovém pásmu než <xref:System.DateTime> struktura, <xref:System.DateTime> parametry jsou používány častěji při volání metody. Z tohoto důvodu je možnost převést <xref:System.DateTimeOffset> hodnoty na <xref:System.DateTime> hodnoty a naopak velmi důležitá. V tomto tématu se dozvíte, jak provádět tyto převody způsobem, který zachovává co možná nejvíce informací o časovém pásmu.

> [!NOTE]
> <xref:System.DateTime> <xref:System.DateTimeOffset> Typy i mají určitá omezení, pokud představují časy v časových pásmech. S jeho <xref:System.DateTime.Kind%2A> vlastností <xref:System.DateTime> je možné odrážet pouze koordinovaný světový čas (UTC) a místní časové pásmo systému. <xref:System.DateTimeOffset>odráží časový posun od času UTC, ale neodráží skutečné časové pásmo, do kterého tento posun patří. Podrobnosti o hodnotách času a podpoře časových pásem najdete v tématu [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Převody z DateTime na DateTimeOffset

<xref:System.DateTimeOffset>Struktura poskytuje dva podobné způsoby, jak provést <xref:System.DateTime> <xref:System.DateTimeOffset> převod, který je vhodný pro většinu převodů:

- <xref:System.DateTimeOffset.%23ctor%2A>Konstruktor, který vytvoří nový <xref:System.DateTimeOffset> objekt založený na <xref:System.DateTime> hodnotě.

- Operátor implicitního převodu, který umožňuje přiřadit <xref:System.DateTime> hodnotu <xref:System.DateTimeOffset> objektu.

Pro UTC a místní <xref:System.DateTime> hodnoty <xref:System.DateTimeOffset.Offset%2A> vlastnost výsledné <xref:System.DateTimeOffset> hodnoty přesně odráží časový posun UTC nebo místní časové pásmo. Například následující kód převede čas UTC na jeho ekvivalentní <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

V tomto případě `utcTime2` je posun proměnné 00:00. Podobně následující kód převede místní čas na odpovídající <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Nicméně pro <xref:System.DateTime> hodnoty, jejichž <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , tyto dvě metody převodu vytvoří <xref:System.DateTimeOffset> hodnotu, jejíž posun je v místním časovém pásmu. To je znázorněno v následujícím příkladu, který je spuštěn v oblasti USA – Tichomoří (běžný čas).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Pokud <xref:System.DateTime> hodnota odráží datum a čas v jiném než místním časovém pásmu nebo UTC, můžete ji převést na <xref:System.DateTimeOffset> hodnotu a zachovat informace o časovém pásmu voláním přetíženého <xref:System.DateTimeOffset.%23ctor%2A> konstruktoru. Například následující příklad vytvoří instanci <xref:System.DateTimeOffset> objektu, který odráží centrální standardní čas.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Druhý parametr pro přetížení tohoto konstruktoru, <xref:System.TimeSpan> objekt, který představuje posun času od času UTC, by měl být načten voláním <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> metody odpovídajícího časového pásma času. Jediným parametrem metody je <xref:System.DateTime> hodnota, která představuje datum a čas, který má být převeden. Pokud časové pásmo podporuje letní čas, tento parametr umožňuje metodě určit odpovídající posun pro konkrétní datum a čas.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Převody z DateTimeOffset na DateTime

<xref:System.DateTimeOffset.DateTime%2A>Vlastnost se nejčastěji používá k <xref:System.DateTimeOffset> <xref:System.DateTime> převodu. Nicméně vrátí <xref:System.DateTime> hodnotu <xref:System.DateTime.Kind%2A> , jejíž vlastnost je <xref:System.DateTimeKind.Unspecified> , jak ukazuje následující příklad.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

To znamená, že <xref:System.DateTimeOffset> při použití vlastnosti jsou všechny informace o vztahu hodnoty ke standardu UTC ztraceny převodem <xref:System.DateTimeOffset.DateTime%2A> . To má vliv <xref:System.DateTimeOffset> na hodnoty, které odpovídají času UTC nebo místnímu času systému, protože <xref:System.DateTimeOffset.DateTime%2A> struktura odráží pouze dvě časová pásma ve své <xref:System.DateTime.Kind%2A> Vlastnosti.

Chcete-li zachovat co nejvíce informací o časovém pásmu při převodu <xref:System.DateTimeOffset> na <xref:System.DateTime> hodnotu, můžete použít <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> vlastnosti a <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> .

### <a name="converting-a-utc-time"></a>Převod času UTC

Pro indikaci, že převedená <xref:System.DateTimeOffset.DateTime%2A> hodnota je čas UTC, můžete načíst hodnotu <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> Vlastnosti. Liší se od <xref:System.DateTimeOffset.DateTime%2A> vlastnosti dvěma způsoby:

- Vrátí hodnotu, <xref:System.DateTime> jejíž <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Utc> .

- Pokud se <xref:System.DateTimeOffset.Offset%2A> hodnota vlastnosti nerovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType> , převede se čas na čas UTC.

> [!NOTE]
> Pokud vaše aplikace vyžaduje <xref:System.DateTime> jednoznačně identifikovat konkrétní bod v čase, měli byste zvážit použití <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> vlastnosti pro zpracování všech <xref:System.DateTimeOffset> <xref:System.DateTime> převodů.

Následující kód používá <xref:System.DateTimeOffset.UtcDateTime%2A> vlastnost k převedení <xref:System.DateTimeOffset> hodnoty, jejíž posun se rovná <xref:System.TimeSpan.Zero?displayProperty=nameWithType> <xref:System.DateTime> hodnotě.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Následující kód používá <xref:System.DateTimeOffset.UtcDateTime%2A> vlastnost k provedení převodu časového pásma a převodu typu na <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Převod místního času

Chcete-li označit, že <xref:System.DateTimeOffset> hodnota představuje místní čas, můžete předat <xref:System.DateTime> hodnotu vrácenou <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> vlastností do `static` `Shared` metody (in Visual Basic) <xref:System.DateTime.SpecifyKind%2A> . Metoda vrátí datum a čas předaný do tohoto parametru jako svůj první parametr, ale nastaví <xref:System.DateTime.Kind%2A> vlastnost na hodnotu určenou jeho druhým parametrem. Následující kód používá <xref:System.DateTime.SpecifyKind%2A> metodu při převodu <xref:System.DateTimeOffset> hodnoty, jejíž posun odpovídá místnímu časovému pásmu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Vlastnost můžete použít také <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> k převedení <xref:System.DateTimeOffset> hodnoty na lokální <xref:System.DateTime> hodnotu. <xref:System.DateTime.Kind%2A>Vlastnost vrácené <xref:System.DateTime> hodnoty je <xref:System.DateTimeKind.Local> . Následující kód používá <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnost při převodu <xref:System.DateTimeOffset> hodnoty, jejíž posun odpovídá místnímu časovému pásmu.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Když načtete <xref:System.DateTime> hodnotu pomocí <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnosti, `get` přistupující objekt vlastnosti nejprve PŘEVEDE <xref:System.DateTimeOffset> hodnotu na UTC a pak ji převede na místní čas voláním <xref:System.DateTimeOffset.ToLocalTime%2A> metody. To znamená, že můžete načíst hodnotu z <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> vlastnosti a provést konverzi časového pásma ve stejnou dobu, jakou provádíte převod typu. Také to znamená, že pravidla úpravy v místním časovém pásmu jsou aplikována při provádění převodu. Následující kód ilustruje použití <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Vlastnosti k provedení jak typu, tak konverze časového pásma. Vzorový výstup je pro počítač nastavený na tichomořské časové pásmo (USA a Kanada). Datum listopadu je Tichomoří (běžný čas), což je UTC-8, zatímco datum června je letní čas, což je UTC-7.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda převodu pro obecné účely

Následující příklad definuje metodu s názvem `ConvertFromDateTimeOffset` , která převádí <xref:System.DateTimeOffset> hodnoty na <xref:System.DateTime> hodnoty. Na základě jeho posunu určuje, zda <xref:System.DateTimeOffset> je hodnota čas UTC, místní čas nebo nějaký jiný čas, a podle toho definuje vrácenou vlastnost hodnoty data a času <xref:System.DateTime.Kind%2A> .

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Následující příklad volá `ConvertFromDateTimeOffset` metodu pro převod <xref:System.DateTimeOffset> hodnot, které reprezentují čas UTC, místní čas a čas v centrálním časovém pásmu USA – střed.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Všimněte si, že tento kód vytváří dvě předpoklady, které v závislosti na aplikaci a zdroji svých hodnot data a času nemusí být vždy platné:

- Předpokládá, že hodnota data a času, jejíž posun je <xref:System.TimeSpan.Zero?displayProperty=nameWithType> reprezentující čas UTC. Ve skutečnosti UTC není čas v konkrétním časovém pásmu, ale čas ve vztahu k tomu, kdy jsou standardizovány časy v časových pásmech světa. Časová pásma mohou také mít posun na <xref:System.TimeSpan.Zero> .

- Předpokládá, že datum a čas, jehož posun se rovná tomuto místnímu časovému pásmu, představuje místní časové pásmo. Vzhledem k tomu, že hodnoty data a času jsou z původního časového pásma odasociovány, nemusí se jednat o případ; Datum a čas mohou mít původ v jiném časovém pásmu se stejným posunem.

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
