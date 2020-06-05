---
title: Převádění časů mezi časovými pásmy
description: Naučte se převádět časy mezi z jednoho časového pásma do jiného v .NET. Naučte se také převést hodnoty DateTimeOffset, které mají omezené povědomí o časovém pásmu.
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
ms.openlocfilehash: 7d1984866c5eacdfe21834389b8f0be4caf78fb7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446838"
---
# <a name="converting-times-between-time-zones"></a>Převádění časů mezi časovými pásmy

U každé aplikace, která pracuje s daty a časy, je stále důležitější pro zpracování rozdílů mezi časovými pásmy. Aplikace již nemůže předpokládat, že všechny časy mohou být vyjádřeny v místním čase, což je čas dostupný ze <xref:System.DateTime> struktury. Například webová stránka, která zobrazuje aktuální čas ve východní části USA, nebude mít u zákazníka ve východní Asie hodnotu věrohodnosti. Toto téma vysvětluje, jak převést časy z jednoho časového pásma na jiný a jak převést <xref:System.DateTimeOffset> hodnoty, které mají omezené povědomí o časovém pásmu.

## <a name="converting-to-coordinated-universal-time"></a>Převod na koordinovaný světový čas

Koordinovaný světový čas (UTC) je Standard s vysokou přesností. Světová časová pásma jsou vyjádřena jako kladná nebo záporná posun od času UTC. UTC tedy poskytuje typ časového pásma volná a neutrální čas v časovém pásmu. Použití času UTC se doporučuje v případě, kdy je důležité přenositelnost data a času napříč počítači. (Podrobnosti a další osvědčené postupy, které používají data a časy, najdete v tématu [osvědčené postupy pro kódování pomocí DateTime v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Převod jednotlivých časových pásem na čas UTC usnadňuje porovnávání času.

> [!NOTE]
> Můžete také serializovat <xref:System.DateTimeOffset> strukturu tak, aby jednoznačně představovala jediný bod v čase. Vzhledem <xref:System.DateTimeOffset> k tomu, že objekty ukládají hodnotu data a času spolu s jejich posunem od času UTC, vždy reprezentují konkrétní bod v čase ve vztahu k času UTC.

Nejjednodušší způsob, jak převést čas na čas UTC, je zavolat `static` metodu ( `Shared` v Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> . Přesný převod prováděný metodou závisí na hodnotě `dateTime` <xref:System.DateTime.Kind%2A> Vlastnosti parametru, jak je uvedeno v následující tabulce.

| `DateTime.Kind`            | Převod                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Převede místní čas na čas UTC.                                                    |
| `DateTimeKind.Unspecified` | Předpokládá, že `dateTime` parametr je místní čas a převede místní čas na UTC. |
| `DateTimeKind.Utc`         | Vrátí `dateTime` parametr beze změny.                                    |

Následující kód převede aktuální místní čas na čas UTC a zobrazí výsledek pro konzolu.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Pokud hodnota data a času nepředstavuje buď místní čas, nebo UTC, <xref:System.DateTime.ToUniversalTime%2A> Metoda bude nejspíš vracet chybný výsledek. Můžete však použít <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metodu k převedení data a času ze zadaného časového pásma. (Podrobnosti o načtení <xref:System.TimeZoneInfo> objektu, který představuje cílové časové pásmo, najdete v tématu [vyhledání časových pásem definovaných v místním systému](finding-the-time-zones-on-local-system.md).) Následující kód používá <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metodu k převodu východního standardního času na čas UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Všimněte si, že tato metoda vyvolá výjimku, <xref:System.ArgumentException> Pokud se <xref:System.DateTime> <xref:System.DateTime.Kind%2A> neshoduje vlastnost objektu a časové pásmo. K neshodě dojde, pokud <xref:System.DateTime.Kind%2A> je vlastnost, <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> objekt nepředstavuje místní časové pásmo, nebo pokud <xref:System.DateTime.Kind%2A> je vlastnost, <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ale objekt se <xref:System.TimeZoneInfo> nerovná <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType> .

Všechny tyto metody přijímají <xref:System.DateTime> hodnoty jako parametry a vracejí <xref:System.DateTime> hodnotu. Pro <xref:System.DateTimeOffset> hodnoty <xref:System.DateTimeOffset> má struktura <xref:System.DateTimeOffset.ToUniversalTime%2A> metodu instance, která převede datum a čas aktuální instance na čas UTC. Následující příklad volá <xref:System.DateTimeOffset.ToUniversalTime%2A> metodu pro převod místního času a několik dalších časů na koordinovaný světový čas (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Převod UTC na určené časové pásmo

Chcete-li převést čas UTC na místní čas, přečtěte si následující oddíl "převod UTC na místní čas". Chcete-li převést čas UTC na čas v jakémkoli časovém pásmu, které určíte, zavolejte <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> metodu. Metoda používá dva parametry:

- ČAS UTC, který se má převést. Musí to být <xref:System.DateTime> hodnota, jejíž <xref:System.DateTime.Kind%2A> vlastnost je nastavena na `Unspecified` nebo `Utc` .

- Časové pásmo k převedení UTC na.

Následující kód převede čas UTC na střední (běžný čas).

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Převod UTC na místní čas

Chcete-li převést čas UTC na místní čas, zavolejte <xref:System.DateTime.ToLocalTime%2A> metodu <xref:System.DateTime> objektu, jehož čas chcete převést. Přesné chování metody závisí na hodnotě <xref:System.DateTime.Kind%2A> vlastnosti objektu, jak je uvedeno v následující tabulce.

| `DateTime.Kind`            | Převod                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Vrátí <xref:System.DateTime> hodnotu beze změny.                                      |
| `DateTimeKind.Unspecified` | Předpokládá, že <xref:System.DateTime> hodnota je UTC a převede čas UTC na místní čas. |
| `DateTimeKind.Utc`         | Převede <xref:System.DateTime> hodnotu na místní čas.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>Metoda se chová stejně jako `DateTime.ToLocalTime` metoda. Přijímá jeden parametr, což je hodnota data a času, která se má převést.

Můžete také převést čas v jakémkoli určeném časovém pásmu na místní čas pomocí `static` metody ( `Shared` v Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> . Tato technika je popsána v následující části.

## <a name="converting-between-any-two-time-zones"></a>Převod mezi dvěma časovými pásmy

Můžete převádět mezi dvěma časovými pásmy pomocí kterékoli z následujících dvou `static` metod ( `Shared` v Visual Basic) <xref:System.TimeZoneInfo> třídy:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Parametry této metody jsou hodnota data a času, která se má převést, `TimeZoneInfo` objekt, který představuje časové pásmo hodnoty data a času, a `TimeZoneInfo` objekt, který představuje časové pásmo pro převod hodnoty data a času na.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Parametry této metody jsou hodnota data a času pro převod, identifikátor časového pásma hodnoty data a času a identifikátor časového pásma, na které má být převedena hodnota data a času.

Obě metody vyžadují, aby <xref:System.DateTime.Kind%2A> vlastnost hodnoty data a času pro převod a <xref:System.TimeZoneInfo> objekt nebo identifikátor časového pásma, který představuje své časové pásmo, odpovídala sobě. V opačném případě <xref:System.ArgumentException> je vyvolána výjimka. Například pokud `Kind` vlastnost hodnoty data a času je `DateTimeKind.Local` , je vyvolána výjimka, pokud je `TimeZoneInfo` objekt předán jako parametr metody, nerovná se `TimeZoneInfo.Local` . Výjimka je také vyvolána, pokud se identifikátor předaný jako parametr metodě nerovná `TimeZoneInfo.Local.Id` .

Následující příklad používá <xref:System.TimeZoneInfo.ConvertTime%2A> metodu pro převod z havajština standardního času na místní čas.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Převádění hodnot DateTimeOffset

Hodnoty data a času reprezentované <xref:System.DateTimeOffset> objekty nejsou plně v časovém pásmu, protože objekt je v době, kdy je vytvořen, odstraněný v časovém pásmu. V mnoha případech však aplikace jednoduše potřebuje převést datum a čas na základě dvou různých posunů od času UTC, nikoli podle času v konkrétních časových pásmech. Chcete-li provést tento převod, můžete zavolat metodu aktuální instance <xref:System.DateTimeOffset.ToOffset%2A> . Jediným parametrem metody je posun nové hodnoty data a času, kterou metoda vrátí.

Například pokud je datum a čas požadavku uživatele na webovou stránku známo a serializován jako řetězec ve formátu MM/dd/rrrr hh: mm: SS zzzz, následující `ReturnTimeOnServer` Metoda převede tuto hodnotu data a času na webový server na datum a čas.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]

Pokud je metodě předán řetězec "9/1/2007 5:32:07 -05:00", který představuje datum a čas v časovém pásmu 5 hodin před časem UTC, vrátí 9/1/2007 3:32:07 dop. 07:00 pro server umístěný v oblasti USA (běžný čas).

<xref:System.TimeZoneInfo>Třída také obsahuje přetížení <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody, která provádí převody časového pásma s <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> hodnotami. Parametry metody jsou <xref:System.DateTimeOffset> hodnota a odkaz na časové pásmo, do kterého má být čas převeden. Volání metody vrací <xref:System.DateTimeOffset> hodnotu. Například `ReturnTimeOnServer` metoda v předchozím příkladu může být přepsána následujícím způsobem pro volání <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> metody.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Viz také

- <xref:System.TimeZoneInfo>
- [Data, časy a časová pásma](index.md)
- [Hledání časových pásem definovaných v lokálním systému](finding-the-time-zones-on-local-system.md)
