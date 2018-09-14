---
title: Převádění časových údajů mezi časovými pásmy
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c77832a4c578ddb2c8a427b133e53ab4ab5c5e3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595623"
---
# <a name="converting-times-between-time-zones"></a>Převádění časových údajů mezi časovými pásmy

Se stává čím dál důležitější pro každou aplikaci, která pracuje s daty a časy zpracovávat rozdíly v časových pásmech. Aplikace již nebude předpokládat, který celou dobu může být vyjádřena v místním čase, což je čas k dispozici <xref:System.DateTime> struktury. Webové stránky, která zobrazí aktuální čas ve východní části USA, například chybět důvěryhodnost zákazníkovi ve východní Asii. Toto téma vysvětluje, jak převést časy z jedné časové pásmo, jakož i jak převést <xref:System.DateTimeOffset> hodnoty, které mají omezenou časové pásmo.

## <a name="converting-to-coordinated-universal-time"></a>Převod na koordinovaný univerzální čas

Koordinovaný univerzální čas (UTC) je standardní čas vysokou přesností, atomické. Na světě časových pásem jsou vyjádřeny jako kladné nebo záporné posun od času UTC. Čas UTC poskytne druh časového pásma zdarma nebo neutrální času časového pásma. Pomocí času UTC se doporučuje, pokud datum a čas pro přenositelnost mezi počítači je důležité. (Podrobnosti a další osvědčené postupy použití dat a časů, naleznete v tématu [kódování osvědčených postupů pomocí data a času v rozhraní .NET Framework](https://msdn.microsoft.com/library/ms973825.aspx).) Převod na standard UTC jednotlivých časových pásmech usnadňuje porovnávání času.

> [!NOTE]
> Můžete také serializovat <xref:System.DateTimeOffset> struktura jednoznačně představují jediný bod v čase. Protože <xref:System.DateTimeOffset> objekty ukládají hodnoty data a času spolu s jeho posun od času UTC, vždy představují určitého bodu v čase ve vztahu k času UTC.

Nejjednodušší způsob, jak převést čas na čas UTC je volání `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> metody. Přesné převodu provedený metodou závisí na hodnotu `dateTime` parametru <xref:System.DateTime.Kind%2A> vlastnost, jak ukazuje následující tabulka.

| `DateTime.Kind`            | Převod                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Místní čas převede na UTC.                                                    |
| `DateTimeKind.Unspecified` | Předpokládá, `dateTime` parametr je místní čas a převede místní čas na čas UTC. |
| `DateTimeKind.Utc`         | Vrátí `dateTime` parametr beze změny.                                    |

Následující kód aktuální místní čas převede na UTC a zobrazí výsledek do konzoly.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> Metoda nevytvoří nutně výsledky, které jsou stejné jako <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metody. Pokud je hostitelský systém místní časové pásmo obsahuje víc úpravy pravidel <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> příslušné pravidlo se vztahuje na konkrétní datum a čas. Tyto dvě metody vždy použít nejnovější pravidla úpravy.

Pokud se hodnoty data a času nepředstavuje UTC, nebo místního času <xref:System.DateTime.ToUniversalTime%2A> vrátí metoda pravděpodobně chybný výsledek. Můžete však použít <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> způsobů, jak převést datum a čas, od zadané časové pásmo. (Další informace o načítání <xref:System.TimeZoneInfo> najdete v článku, který představuje cílové časové pásmo [hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Následující kód používá <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> způsobů, jak převést východní běžný čas na čas UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Všimněte si, že tato metoda vyvolá <xref:System.ArgumentException> Pokud <xref:System.DateTime> objektu <xref:System.DateTime.Kind%2A> vlastnost a časové pásmo se neshodují. Pokud dojde k neshodě <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> objekt nepředstavuje místnímu časovému pásmu, nebo, pokud <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> objektu se nerovná <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.

Provést všechny tyto metody <xref:System.DateTime> hodnoty jako parametry a vraťte se <xref:System.DateTime> hodnotu. Pro <xref:System.DateTimeOffset> hodnot, <xref:System.DateTimeOffset> má strukturu <xref:System.DateTimeOffset.ToUniversalTime%2A> instanci metody, která převede datum a čas aktuální instance na čas UTC. Následující příklad volá <xref:System.DateTimeOffset.ToUniversalTime%2A> způsobů, jak převést místním časem a dalších několikrát koordinovaný univerzální čas (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Převod na požadovaném časovém pásmu UTC

Převod času UTC na místní čas, najdete v části "převodu času UTC na místní čas", který následuje. Chcete-li převést UTC na čas v časovém pásmu, který určíte, zavolejte <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> metody. Tato metoda přebírá dva parametry:

* Chcete-li převést na UTC. Musí se jednat <xref:System.DateTime> hodnota, jejíž <xref:System.DateTime.Kind%2A> je nastavena na `Unspecified` nebo `Utc`.

* Časové pásmo pro čas UTC pro převod.

Následující kód UTC převede na střed (běžný čas).

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Převod času UTC na místní čas

Chcete-li převést UTC na místní čas, zavolejte <xref:System.DateTime.ToLocalTime%2A> metodu <xref:System.DateTime> objekt, jehož čas, který chcete převést. Přesné chování metody závisí na hodnotě objektu <xref:System.DateTime.Kind%2A> vlastnost, jak ukazuje následující tabulka.

| `DateTime.Kind`            | Převod                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Vrátí <xref:System.DateTime> nezměněnou hodnotu.                                      |
| `DateTimeKind.Unspecified` | Předpokládá, že <xref:System.DateTime> hodnota a převede na UTC na místní čas UTC. |
| `DateTimeKind.Utc`         | Převede <xref:System.DateTime> hodnotu na místní čas.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Metoda chová stejně jako `DateTime.ToLocalTime` metody. To přijímá jeden parametr, což je hodnota data a času pro převod.

Čas v libovolném požadovaném časovém pásmu na místní čas můžete také převádět pomocí `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> metody. Tato technika je popsáno v další části.

## <a name="converting-between-any-two-time-zones"></a>Převod mezi každými dvěma časovými pásmy

Je možné převádět mezi dvě časová pásma pomocí některé z následujících dvou `static` (`Shared` v jazyce Visual Basic) metody <xref:System.TimeZoneInfo> třídy:

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  Tato metoda parametry jsou hodnoty data a času pro převod, `TimeZoneInfo` objekt, který reprezentuje časovém pásmu z hodnoty data a času a `TimeZoneInfo` objekt, který představuje časové pásmo, které chcete převést na hodnotu data a času.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Tato metoda parametry jsou datum a čas k převedení, identifikátor datum a časové pásmo času a identifikátor časového pásma převést na hodnotu data a času.

Obě metody vyžadují, aby <xref:System.DateTime.Kind%2A> vlastnosti hodnoty data a času pro převod a <xref:System.TimeZoneInfo> odpovídají objektu nebo časové pásmo identifikátor, který představuje jeho časového pásma mezi sebou. V opačném případě <xref:System.ArgumentException> je vyvolána výjimka. Například pokud `Kind` vlastnosti hodnoty data a času je `DateTimeKind.Local`, je vyvolána výjimka, pokud `TimeZoneInfo` objekt předán jako parametr do metody není shodný s `TimeZoneInfo.Local`. Pokud identifikátor jako parametr předán metodě není roven také vyvolána výjimka `TimeZoneInfo.Local.Id`.

V následujícím příkladu <xref:System.TimeZoneInfo.ConvertTime%2A> způsobů, jak převést z Havajské ostrovy (běžný čas) na místní čas.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Převod hodnoty DateTimeOffset

Hodnoty data a času reprezentována <xref:System.DateTimeOffset> objekty nejsou plně časového pásma vědět, protože objekt je oddělen od svého časového pásma v době, kdy je vytvořen. Ale v mnoha případech aplikace jednoduše převést datum a čas založený na dvou různých posun od času UTC, nikoli na čas zejména časových pásem. Chcete-li provést tento převod, můžete volat aktuální instance <xref:System.DateTimeOffset.ToOffset%2A> metody. Jediný parametr metody je posun novou hodnotu data a času, která metoda se vrátí.

Například pokud datum a čas uživatele o pro webové stránky se označuje a serializuje jako řetězec ve formátu MM/dd/rrrr hh: mm: zzzz následující `ReturnTimeOnServer` metoda převede na datum a čas na webovém serveru této hodnotě data a času.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Pokud metodě je předána řetězec "9/1/2007 5:32:07 -05:00", která představuje datum a čas v časovém pásmu dříve než čas UTC pět hodin, vrátí hodnotu 9/1/2007 3:32:07: 00 -07:00 pro server umístěný v USA. Tichomořském časovém pásmu.

<xref:System.TimeZoneInfo> Třída také obsahuje přetížení <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metodu, která provádí převody s <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> hodnoty. Parametry metody <xref:System.DateTimeOffset> hodnoty a odkazu na časové pásmo, do kterého se má převést čas. Volání metody vrátí <xref:System.DateTimeOffset> hodnotu. Například `ReturnTimeOnServer` metoda v předchozím příkladu může být přepsán následujícím způsobem pro volání <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> metody.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Viz také:

* <xref:System.TimeZoneInfo>
* [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
* [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
