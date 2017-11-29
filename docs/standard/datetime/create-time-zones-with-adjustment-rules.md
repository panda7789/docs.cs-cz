---
title: "Postupy: vytváření časových pásem s pravidly úpravy"
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
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75e1867e810090bf35a0dfc7def5785747f94382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Postupy: vytváření časových pásem s pravidly úpravy

Informace o přesné časovém pásmu, který je požadován pro aplikace nemusí být na určitém systému k dispozici pro několik důvodů:

* Časové pásmo nikdy byla definována v registru místního systému.

* Data o časovém pásmu byl změněn nebo odstraněn z registru.

* Časové pásmo nemá přesné informace o úpravách časové pásmo pro určité historické období.

V těchto případech můžete volat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda definovat časové pásmo požadované aplikací. Přetížení této metody můžete vytvořit časové pásmo s nebo bez pravidel úpravy. Pokud se časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly buď pevné nebo plovoucí úpravy. (Pro definice těchto podmínkách, najdete v části "Časové pásmo terminologií" v [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nejsou přidány do registru. Místo toho jsou dostupné pouze prostřednictvím odkazu na objekt vrácený <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> volání metody.

Toto téma ukazuje, jak vytvořit časové pásmo s pravidly úpravy. Vytvoření časové pásmo, které nepodporuje pravidla úpravy letního času naleznete v tématu [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Chcete-li vytvořit časové pásmo s plovoucí úpravy pravidel

1. Pro každou úpravu (který je pro každý přechod směrem od a zpět do standardního času v konkrétním časovém intervalu) postupujte takto:

    1. Zadejte počáteční čas přechodu pro úpravu časového pásma.

       Je třeba volat <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metoda a předejte ji <xref:System.DateTime> hodnotu, která definuje čas přechodu, celočíselná hodnota, která definuje měsíc přechodu, celočíselná hodnota, která definuje v týdnu, kdy dojde k přechodu, a <xref:System.DayOfWeek> hodnota, která definuje den v týdnu, kdy dojde k přechodu. Toto volání metody vytváří <xref:System.TimeZoneInfo.TransitionTime> objektu.

    2. Zadejte čas dokončení přechodu pro úpravu časového pásma. To vyžaduje další volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metoda. Toto volání metody vytváří druhý <xref:System.TimeZoneInfo.TransitionTime> objektu.

    3. Volání <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> metoda a předejte ji efektivní počáteční a koncové datum úpravy, <xref:System.TimeSpan> objekt, který definuje množství času v přechodu a dvě <xref:System.TimeZoneInfo.TransitionTime> objekty, které definují při přechody do a z letní čas čas následovat. Toto volání metody vytváří <xref:System.TimeZoneInfo.AdjustmentRule> objektu.

    4. Přiřazení <xref:System.TimeZoneInfo.AdjustmentRule> objekt, který má pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty.

2. Definujte časové pásmo zobrazovaný název. Zobrazovaný název následuje poměrně standardní formát, ve kterém posun časového pásma z koordinovaný světový čas (UTC) uzavřený v závorkách a následuje řetězec, který identifikuje časové pásmo, jeden nebo více měst v časovém pásmu, nebo v jednom nebo více cou oložky nebo oblasti v časovém pásmu.

3. Definuje název časové pásmo (běžný čas). Obvykle se tento řetězec se používá jako identifikátor časového pásma.

4. Zadejte název časového pásma letní čas.

5. Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.

6. Vytváření instancí <xref:System.TimeSpan> objekt, který definuje posun časového pásma od času UTC. Časová pásma s časy, které jsou novější než čas UTC mít kladný posun. Časová pásma s časy, které jsou starší než čas UTC mít záporný posun.

7. Volání <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metoda pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

V následujícím příkladu definuje centrální standardní časové pásmo pro Spojené státy americké, zahrnující pravidla úprav pro celou řadu časové intervaly z 1918 tohoto.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Časové pásmo vytvořené v tomto příkladu má více pravidel úpravy. Musí být dbát na to, že efektivní počáteční a koncové datum jakéhokoli pravidla úpravy nepřekrývají s daty z jiné pravidlo úpravy. Pokud dojde překrytí <xref:System.InvalidTimeZoneException> je vyvolána výjimka.

Pro plovoucí úpravy pravidel, je předána hodnota 5 `week` parametr <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metoda k označení, že dojde k přechodu poslední týden v určitém měsíci.

Při vytváření pole <xref:System.TimeZoneInfo.AdjustmentRule> objekty, které chcete použít v <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> volání metody kód inicializovat pole velikosti požadované počtem úpravy, které mají být vytvořeny pro časové pásmo. Místo toho tento příklad kódu volá <xref:System.Collections.Generic.List%601.Add%2A> metodu pro přidání do obecný každé pravidlo úpravy <xref:System.Collections.Generic.List%601> kolekce <xref:System.TimeZoneInfo.AdjustmentRule> objekty. Kód pak zavolá <xref:System.Collections.Generic.List%601.CopyTo%2A> metoda kopírování členy této kolekce do pole.

V příkladu se používá také <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metoda definovat pevným datem. Toto je podobná volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metoda, s tím rozdílem, že IT oddělení vyžaduje pouze čas, měsíc a den parametrů přechodu.

V příkladu lze otestovat pomocí kódu, například následující:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Aby byly importované následujících oborů názvů:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
