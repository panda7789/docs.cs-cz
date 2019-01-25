---
title: 'Postupy: Vytváření časových pásem s pravidly úpravy'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83905c97f37a0e49f6219da47e2f640ecfb8edfb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721172"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Postupy: Vytváření časových pásem s pravidly úpravy

Informace přesné časové pásmo, který vyžaduje aplikace nemusí být k dispozici na konkrétní systém z několika důvodů:

* Časové pásmo je nikdy definována v registru místního systému.

* Data o časovém pásmu, byla změněna nebo odebrána z registru.

* Časové pásmo nemá žádné přesné informace o úpravách časové pásmo pro konkrétní období historické.

V těchto případech můžete volat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda k definování časové pásmo požadovaná vaší aplikací. Přetížení této metody můžete použít k vytvoření časové pásmo s nebo bez pravidel úpravy. Podporuje-li časové pásmo letního času, můžete definovat úpravy pomocí pravidla buď pevnou nebo plovoucí úpravy. (Definice těchto pojmů najdete v části "Časové pásmo terminologie" v [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časové pásmo vytvořených voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nejsou přidány do registru. Místo toho jsou dostupné jenom prostřednictvím odkazu na objekt vrácený <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> volání metody.

Toto téma ukazuje, jak vytváření časových pásem s pravidly úpravy. Vytvoření časového pásma, která nepodporuje pravidly úpravy letního času, najdete v tématu [jak: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Chcete-li vytvořit časové pásmo s plovoucí pravidly úpravy

1. Pro každou úpravu (který je pro každý přechod ze a zpět v konkrétním časovém intervalu (běžný čas)) postupujte takto:

    1. Definujte výchozí dobu přechodu pro úpravu časového pásma.

       Je nutné volat <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> – metoda a předejte jej <xref:System.DateTime> hodnotu, která definuje čas přechodu, celočíselnou hodnotu, která definuje měsíc přechodu, celočíselnou hodnotu, která definuje v týdnu, ve kterém má dojít k přechodu a <xref:System.DayOfWeek> hodnota, která definuje dne v týdnu, ve kterém dojde k přechodu. Vytvoří instanci volání této metody <xref:System.TimeZoneInfo.TransitionTime> objektu.

    2. Definujte čas dokončení přechodu pro úpravu časového pásma. To vyžaduje další volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody. Toto volání metody vytváří sekundy <xref:System.TimeZoneInfo.TransitionTime> objektu.

    3. Volání <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> metoda a předejte jí efektivní počáteční a koncové datum úpravy, <xref:System.TimeSpan> objekt, který definuje množství času v přechodu a dva <xref:System.TimeZoneInfo.TransitionTime> objekty, které definují při přechody do a z letní čas dojde k času. Vytvoří instanci volání této metody <xref:System.TimeZoneInfo.AdjustmentRule> objektu.

    4. Přiřazení <xref:System.TimeZoneInfo.AdjustmentRule> objekt na pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty.

2. Definujte časové pásmo zobrazovaný název. Zobrazovaný název následuje poměrně standardní formát, ve kterém časovém pásmu posun od koordinovaného světového času (UTC) není uzavřen v závorkách a následuje řetězec, který určí časové pásmo, jeden nebo více měst v časovém pásmu, nebo v jednom nebo více následujících cou oložky nebo oblasti v časovém pásmu.

3. Definujte název časového pásma (běžný čas). Obvykle tento řetězec se také používá jako identifikátor časového pásma.

4. Definujte název časového pásma letního času.

5. Pokud chcete použít jiný identifikátor než název standardního časového pásma, definujte identifikátor časového pásma.

6. Vytvořit instanci <xref:System.TimeSpan> objekt, který definuje posun časového pásma UTC. Časových pásem s časem, které jsou novější než čas UTC mít kladný posun. Časových pásem s časem, které jsou starší než čas UTC, mají negativní posun.

7. Volání <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metoda pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

Následující příklad definuje střed standardní časové pásmo pro USA, který obsahuje pravidla úpravy pro širokou škálu časových intervalech od 1918 až po současnost.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Časové pásmo vytvořené v tomto příkladu má víc úpravy pravidel. Musí se dbát na to, že efektivní počáteční a koncové datum u libovolného pravidla úprav nepřekrývají s daty z jiné pravidlo úpravy. Pokud dojde k překrytí <xref:System.InvalidTimeZoneException> je vyvolána výjimka.

Pro plovoucí úpravy pravidel, je předána hodnota 5 `week` parametr <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> indikace, že dojde k přechodu na poslední týden v daném měsíci.

Při vytváření pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty používané <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> volání metody, kód může inicializovat pole na velikost požadovanou podle počtu úpravy mají být vytvořeny pro časové pásmo. Místo toho tento příklad kódu volá <xref:System.Collections.Generic.List%601.Add%2A> způsob, jak přidat každého pravidla úpravy pro obecný <xref:System.Collections.Generic.List%601> kolekce <xref:System.TimeZoneInfo.AdjustmentRule> objekty. Kód poté volá <xref:System.Collections.Generic.List%601.CopyTo%2A> metoda kopírování členy této kolekce do pole.

V příkladu se také používá <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metoda k definování úprav s pevným datem. Podobá se to volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, s tím rozdílem, že se vyžaduje jenom čas, měsícem a dnem v parametrech přechod.

V příkladu lze otestovat pomocí kódu, jako jsou následující:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Core.dll přidán do projektu.

* Aby byly importované následující obory názvů:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
