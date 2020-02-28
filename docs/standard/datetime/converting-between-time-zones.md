---
title: Převádění časů mezi časovými pásmy
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
ms.openlocfilehash: fbb59dbe364763209f44a4e2241d1d5275036c40
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156020"
---
# <a name="converting-times-between-time-zones"></a>Převádění časů mezi časovými pásmy

U každé aplikace, která pracuje s daty a časy, je stále důležitější pro zpracování rozdílů mezi časovými pásmy. Aplikace už nemůže předpokládat, že všechny časy můžou být vyjádřené v místním čase, což je čas dostupný z <xref:System.DateTime> struktury. Například webová stránka, která zobrazuje aktuální čas ve východní části USA, nebude mít u zákazníka ve východní Asie hodnotu věrohodnosti. Toto téma vysvětluje, jak převést časy z jednoho časového pásma na jiný a jak převést <xref:System.DateTimeOffset> hodnoty, které mají omezené povědomí o časovém pásmu.

## <a name="converting-to-coordinated-universal-time"></a>Převod na koordinovaný světový čas

Koordinovaný světový čas (UTC) je Standard s vysokou přesností. Světová časová pásma jsou vyjádřena jako kladná nebo záporná posun od času UTC. UTC tedy poskytuje typ časového pásma volná a neutrální čas v časovém pásmu. Použití času UTC se doporučuje v případě, kdy je důležité přenositelnost data a času napříč počítači. (Podrobnosti a další osvědčené postupy, které používají data a časy, najdete v tématu [osvědčené postupy pro kódování pomocí DateTime v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Převod jednotlivých časových pásem na čas UTC usnadňuje porovnávání času.

> [!NOTE]
> Můžete také serializovat <xref:System.DateTimeOffset> strukturu, aby jednoznačně představovala jediný bod v čase. Vzhledem k tomu, že <xref:System.DateTimeOffset> objekty ukládají hodnotu data a času spolu s posunem od času UTC, vždy představuje konkrétní bod v čase ve vztahu k času UTC.

Nejjednodušší způsob, jak převést čas na čas UTC, je zavolat metodu `static` (`Shared` v Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>. Přesný převod prováděný metodou závisí na hodnotě vlastnosti <xref:System.DateTime.Kind%2A> parametru `dateTime`, jak je uvedeno v následující tabulce.

| `DateTime.Kind`            | Převod                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Převede místní čas na čas UTC.                                                    |
| `DateTimeKind.Unspecified` | Předpokládá, že parametr `dateTime` je místní čas a převede místní čas na UTC. |
| `DateTimeKind.Utc`         | Vrátí parametr `dateTime` beze změny.                                    |

Následující kód převede aktuální místní čas na čas UTC a zobrazí výsledek pro konzolu.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Pokud hodnota data a času nepředstavuje místní čas nebo UTC, <xref:System.DateTime.ToUniversalTime%2A> metoda bude nejspíš vracet chybný výsledek. Můžete však použít metodu <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> k převodu data a času ze zadaného časového pásma. (Podrobnosti o načtení <xref:System.TimeZoneInfo>ho objektu, který představuje časové pásmo cíle, najdete v tématu [vyhledání časových pásem definovaných v místním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Následující kód používá metodu <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> k převodu východního standardního času na čas UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Všimněte si, že tato metoda vyvolá <xref:System.ArgumentException>, pokud se neshoduje vlastnost <xref:System.DateTime.Kind%2A> objektu <xref:System.DateTime> a časové pásmo. K neshodě dojde, pokud je vlastnost <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, ale objekt <xref:System.TimeZoneInfo> nepředstavuje místní časové pásmo, nebo pokud je vlastnost <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, ale objekt <xref:System.TimeZoneInfo> se nerovná <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.

Všechny tyto metody přebírají <xref:System.DateTime> hodnoty jako parametry a vracejí hodnotu <xref:System.DateTime>. Pro <xref:System.DateTimeOffset> hodnoty má struktura <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToUniversalTime%2A> metodu instance, která převede datum a čas aktuální instance na čas UTC. Následující příklad volá metodu <xref:System.DateTimeOffset.ToUniversalTime%2A> pro převod místního času a několik dalších časů na koordinovaný světový čas (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Převod UTC na určené časové pásmo

Chcete-li převést čas UTC na místní čas, přečtěte si následující oddíl "převod UTC na místní čas". Chcete-li převést čas UTC na čas v jakémkoli časovém pásmu, které určíte, zavolejte metodu <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>. Metoda používá dva parametry:

- ČAS UTC, který se má převést. Musí se jednat o hodnotu <xref:System.DateTime>, jejíž vlastnost <xref:System.DateTime.Kind%2A> je nastavena na `Unspecified` nebo `Utc`.

- Časové pásmo k převedení UTC na.

Následující kód převede čas UTC na střední (běžný čas).

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Převod UTC na místní čas

Chcete-li převést čas UTC na místní čas, zavolejte metodu <xref:System.DateTime.ToLocalTime%2A> objektu <xref:System.DateTime>, jehož čas chcete převést. Přesné chování metody závisí na hodnotě vlastnosti <xref:System.DateTime.Kind%2A> objektu, jak je uvedeno v následující tabulce.

| `DateTime.Kind`            | Převod                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Vrátí hodnotu <xref:System.DateTime> beze změny.                                      |
| `DateTimeKind.Unspecified` | Předpokládá, že hodnota <xref:System.DateTime> je UTC a převede čas UTC na místní čas. |
| `DateTimeKind.Utc`         | Převede hodnotu <xref:System.DateTime> na místní čas.                                 |

> [!NOTE]
> Metoda <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> se chová stejně jako metoda `DateTime.ToLocalTime`. Přijímá jeden parametr, což je hodnota data a času, která se má převést.

Můžete také převést čas v jakémkoli určeném časovém pásmu na místní čas pomocí <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> metody `static` (`Shared` in Visual Basic). Tato technika je popsána v následující části.

## <a name="converting-between-any-two-time-zones"></a>Převod mezi dvěma časovými pásmy

Můžete převádět mezi dvěma časovými pásmy pomocí kterékoli z následujících dvou metod `static` (`Shared` v Visual Basic) třídy <xref:System.TimeZoneInfo>:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Parametry této metody jsou hodnota data a času, která se má převést, `TimeZoneInfo` objekt, který představuje časové pásmo hodnoty data a času, a objekt `TimeZoneInfo`, který představuje časové pásmo pro převod hodnoty data a času na.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Parametry této metody jsou hodnota data a času pro převod, identifikátor časového pásma hodnoty data a času a identifikátor časového pásma, na které má být převedena hodnota data a času.

Obě metody vyžadují, aby vlastnost <xref:System.DateTime.Kind%2A> hodnoty data a času, která se má převést, a <xref:System.TimeZoneInfo> objektu nebo identifikátoru časového pásma, který představuje své časové pásmo, odpovídá sobě navzájem. V opačném případě je vyvolána <xref:System.ArgumentException>. Například pokud je vlastnost `Kind` hodnoty data a času `DateTimeKind.Local`, je vyvolána výjimka, pokud se objekt `TimeZoneInfo` předaný jako parametr metodě nerovná `TimeZoneInfo.Local`. Výjimka je také vyvolána, pokud se identifikátor předaný jako parametr metodě nerovná `TimeZoneInfo.Local.Id`.

Následující příklad používá metodu <xref:System.TimeZoneInfo.ConvertTime%2A> pro převod z havajština standardního času na místní čas.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Převádění hodnot DateTimeOffset

Hodnoty data a času reprezentované <xref:System.DateTimeOffset> objekty nejsou plně v časovém pásmu, protože objekt je v době, kdy je vytvořen, odasociován z jeho časového pásma. V mnoha případech však aplikace jednoduše potřebuje převést datum a čas na základě dvou různých posunů od času UTC, nikoli podle času v konkrétních časových pásmech. Chcete-li provést tento převod, můžete zavolat metodu <xref:System.DateTimeOffset.ToOffset%2A> aktuální instance. Jediným parametrem metody je posun nové hodnoty data a času, kterou metoda vrátí.

Například pokud je datum a čas požadavku uživatele na webovou stránku známo a serializován jako řetězec ve formátu MM/dd/rrrr hh: mm: SS zzzz, převede následující `ReturnTimeOnServer` metoda tuto hodnotu data a času na webový server.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]

Pokud je metodě předán řetězec "9/1/2007 5:32:07 -05:00", který představuje datum a čas v časovém pásmu 5 hodin před časem UTC, vrátí 9/1/2007 3:32:07 dop. 07:00 pro server umístěný v oblasti USA (běžný čas).

Třída <xref:System.TimeZoneInfo> také obsahuje přetížení metody <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>, která provádí převody časových pásem s <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>mi hodnotami. Parametry metody jsou <xref:System.DateTimeOffset> hodnota a odkaz na časové pásmo, do kterého má být čas převeden. Volání metody vrací <xref:System.DateTimeOffset> hodnotu. Například metoda `ReturnTimeOnServer` v předchozím příkladu může být přepsána následujícím způsobem pro volání metody <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Viz také

- <xref:System.TimeZoneInfo>
- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
