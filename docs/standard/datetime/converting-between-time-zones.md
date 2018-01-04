---
title: "Převádění časových údajů mezi časovými pásmy"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 58ed01520a9bbed53d32fc10e48a479e68f6ef7c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="converting-times-between-time-zones"></a>Převádění časových údajů mezi časovými pásmy

Se stává stále důležité pro každou aplikaci, která funguje s daty a časy pro zpracování rozdíly mezi časová pásma. Aplikace už můžete předpokládat, že všechny časy mohou být vyjádřeny v místním čase, který čas je k dispozici <xref:System.DateTime> struktura. Webové stránky, které se zobrazí aktuální čas v části východní USA, například chybět důvěryhodnosti, aby zákazníka ve východní Asii. Toto téma vysvětluje, jak převést časy z jednoho časového pásma, a také jak převést <xref:System.DateTimeOffset> hodnoty, které mají omezenou časové pásmo.

## <a name="converting-to-coordinated-universal-time"></a>Převádění na koordinovaný světový čas

Koordinovaný světový čas (UTC) je standardní vysokou přesnost, atomic doba. Časová pásma na světě jsou vyjádřené jako kladné nebo záporné posun od času UTC. UTC tak poskytuje druh časových pásem volné nebo neutrální času časového pásma. Použití čas UTC se doporučuje, když datum a časové přenositelnost mezi počítači je důležité. (Podrobnosti a ostatní osvědčené postupy, pomocí data a časy najdete v tématu [kódování osvědčených postupů pomocí data a času v rozhraní .NET Framework](http://go.microsoft.com/fwlink/?LinkId=92342).) Převod jednotlivých časových pásem na čas UTC usnadňuje porovnávání času.

> [!NOTE]
> Můžete také serializovat <xref:System.DateTimeOffset> struktury pro jednoznačné určení jediný bod v čase. Protože <xref:System.DateTimeOffset> objekty ukládání hodnot data a času společně s její posun od času UTC, vždy představují do konkrétního bodu v čase ve vztahu k UTC.

Nejjednodušší způsob, jak převést čas UTC je volat `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> metoda. Přesný převod provádí metodu závisí na hodnotu `dateTime` parametru <xref:System.DateTime.Kind%2A> vlastnost, jak ukazuje následující tabulka.

| `DateTime.Kind`            | Převod                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Převede místního času na čas UTC.                                                    |
| `DateTimeKind.Unspecified` | Předpokládá `dateTime` parametr je místní čas a převede místního času na čas UTC. |
| `DateTimeKind.Utc`         | Vrátí `dateTime` parametr beze změny.                                    |

Následující kód převede na UTC aktuálním místním časem a zobrazí výsledek do konzoly.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> Metoda nevrátí nutně výsledky, které jsou stejné jako <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metody. Pokud systém hostitele je místní časové pásmo obsahuje více pravidel úpravy, <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> příslušné pravidlo se vztahuje na určité datum a čas. Tyto dvě metody vždy použít nejnovější pravidlo úpravy.

Pokud hodnota data a času nepředstavuje UTC, nebo místního času <xref:System.DateTime.ToUniversalTime%2A> metoda vrátí pravděpodobně chybný výsledek. Můžete však použít <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> způsobů, jak převést datum a čas ze zadaného časového pásma. (Další informace o načítání <xref:System.TimeZoneInfo> objekt, který reprezentuje cílové časové pásmo, najdete v části [hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Následující kód používá <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metoda převést východní běžný čas UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Všimněte si, že tato metoda vyvolá <xref:System.ArgumentException> Pokud <xref:System.DateTime> objektu <xref:System.DateTime.Kind%2A> vlastnost a časové pásmo neshodují. Nesoulad nastává, pokud <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> objekt nepředstavuje místní časové pásmo, nebo pokud <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> objekt se nerovná <xref:System.DateTimeKind?displayProperty=nameWithType>.

Všechny tyto metody trvat <xref:System.DateTime> hodnoty jako parametry a vraťte se <xref:System.DateTime> hodnotu. Pro <xref:System.DateTimeOffset> hodnoty, <xref:System.DateTimeOffset> má struktura <xref:System.DateTimeOffset.ToUniversalTime%2A> instance metoda, která převede datum a čas aktuální instance na čas UTC. Následující příklad volání <xref:System.DateTimeOffset.ToUniversalTime%2A> způsobů, jak převést místní čas a dalších několikrát koordinovaný světový čas (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Převádění na určené časové pásmo UTC

Převést na místní čas UTC, najdete v části "převod na místní čas UTC", který následuje dále. Chcete-li převést UTC na čas v časovém pásmu, který určíte, volejte <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> metoda. Metoda přebírá dva parametry:

* Chcete-li převést na UTC. Tato hodnota musí být <xref:System.DateTime> hodnotu jehož <xref:System.DateTime.Kind%2A> je nastavena na <xref:System.DateTimeKind?displayProperty=nameWithType> nebo <xref:System.DateTimeKind?displayProperty=nameWithType>.

* Časové pásmo a převádět na UTC.

Následující kód převede na čas UTC.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Převádění na místní čas UTC

Chcete-li převést na místní čas UTC, volejte <xref:System.DateTime.ToLocalTime%2A> metodu <xref:System.DateTime> objekt, jehož čas, který chcete převést. Přesné chování metody závisí na hodnotu objektu <xref:System.DateTime.Kind%2A> vlastnost, jak ukazuje následující tabulka.

| `DateTime.Kind`            | Převod                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Vrátí <xref:System.DateTime> hodnotu beze změny.                                      |
| `DateTimeKind.Unspecified` | Předpokládá, že <xref:System.DateTime> hodnota a převede na UTC na místní čas UTC. |
| `DateTimeKind.Utc`         | Převede <xref:System.DateTime> hodnotu na místní čas.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Metoda se chová stejně jako `DateTime.ToLocalTime` metoda. Trvá jeden parametr, který je hodnota, datum a čas převést.

Také můžete převést čas v jakékoli časovém pásmu na místní čas s použitím `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> metoda. Tato technika je popsána v další části.

## <a name="converting-between-any-two-time-zones"></a>Převádění mezi každými dvěma časovými pásmy

Můžete převádět mezi dvěma časovými pásmy pomocí některé z následujících dvou `static` (`Shared` v jazyce Visual Basic) metody <xref:System.TimeZoneInfo> třídy:

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  Tato metoda parametry jsou hodnoty data a času, které chcete převést, `TimeZoneInfo` objekt, který reprezentuje časové pásmo hodnoty data a času a `TimeZoneInfo` objekt, který reprezentuje časové pásmo na převést na hodnotu data a času.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Tato metoda parametry jsou datum a čas hodnotu převést, identifikátor datum a čas hodnota časové pásmo a identifikátor časového pásma převést na hodnotu data a času.

Obě metody vyžadují, aby <xref:System.DateTime.Kind%2A> vlastnost hodnota data a času pro převod a <xref:System.TimeZoneInfo> objektu nebo identifikátor, který představuje jeho časové pásmo odpovídají na sebe navzájem. Jinak <xref:System.ArgumentException> je vyvolána výjimka. Například pokud `Kind` vlastnost hodnota data a času je `DateTimeKind.Local`, je vyvolána výjimka, pokud `TimeZoneInfo` objekt jako parametr předaný metodě není rovno `TimeZoneInfo.Local`. Pokud není rovno identifikátor jako parametr předaný metodě je také vyvolána výjimka `TimeZoneInfo.Local.Id`.

Následující příklad používá <xref:System.TimeZoneInfo.ConvertTime%2A> způsobů, jak převést z havajského standardního času na místní čas.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Převádění hodnot DateTimeOffset

Hodnoty data a času reprezentována <xref:System.DateTimeOffset> objekty nejsou plně časových pásem vědět, protože objekt je oddělen od svého časového pásma v době, kdy je vytvořen. Ale v mnoha případech aplikace jednoduše převést datum a čas na základě na dvou různých posun od času UTC místo v době na konkrétní časová pásma. Chcete-li provést tento převod, můžete zavolat aktuální instance <xref:System.DateTimeOffset.ToOffset%2A> metoda. Jeden parametr metody je posun nové datum a čas hodnotu, která metoda se má vrátit.

Například v případě požadavku na datum a čas uživatele pro webové stránky je známý a serializován jako řetězec ve formátu MM/dd/rrrr hh: mm: zzzz, následující `ReturnTimeOnServer` metoda převede tuto hodnotu data a času na datum a čas na webovém serveru.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Pokud metoda je předán řetězec "9/1/2007 5:32:07 -05:00", která představuje datum a čas v časovém pásmu pět hodin dříve než čas UTC, vrátí 9/1/2007 3:32:07: 00 -07:00 pro server nachází v USA Tichomořském časovém pásmu.

<xref:System.TimeZoneInfo> Třída také obsahuje přetížení <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda, která provádí převody časové pásmo s <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> hodnoty. Parametry metody jsou <xref:System.DateTimeOffset> hodnota a odkaz na časové pásmo, na které má být převeden čas. Volání metody vrátí <xref:System.DateTimeOffset> hodnotu. Například `ReturnTimeOnServer` metoda v předchozím příkladu může být přepsána takto pro volání <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> metoda.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Viz také

<xref:System.TimeZoneInfo>[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
