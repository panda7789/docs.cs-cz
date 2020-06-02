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
ms.openlocfilehash: b7e938581dfde3f1566aa2506302292686c2fc5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278165"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Postupy: Vytváření časových pásem s pravidly úpravy

Přesné informace o časovém pásmu, které vyžaduje aplikace, nemusí být k dispozici v konkrétním systému z několika důvodů:

- Časové pásmo nebylo nikdy definováno v registru místního systému.

- Data o časovém pásmu byla upravena nebo odebrána z registru.

- Časové pásmo nemá správné informace o úpravách časového pásma pro konkrétní historické období.

V těchto případech můžete zavolat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodu pro definování časového pásma vyžadovaného vaší aplikací. Pomocí přetížení této metody můžete vytvořit časové pásmo s pravidly úprav nebo bez nich. Pokud časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly úpravy s pevnou nebo plovoucí. (Pro definice těchto podmínek si přečtěte část "Terminologie časových pásem" v tématu [Přehled časového pásma](time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nejsou přidána do registru. Místo toho mohou být k dispozici pouze prostřednictvím odkazu objektu vráceného <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> voláním metody.

V tomto tématu se dozvíte, jak vytvořit časové pásmo s pravidly úprav. Chcete-li vytvořit časové pásmo, které nepodporuje pravidla pro úpravu letního času, přečtěte si téma [Postup: vytváření časových pásem bez pravidel úprav](create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Vytvoření časového pásma s plovoucími pravidly úpravy

1. Pro každou úpravu (tj. pro každý přechod mimo určitý časový interval a zpět na běžný čas) udělejte toto:

    1. Definujte dobu zahájení přechodu pro úpravu časového pásma.

       Je nutné zavolat <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metodu a předat jí <xref:System.DateTime> hodnotu, která definuje čas přechodu, celočíselnou hodnotu, která definuje měsíc přechodu, celočíselnou hodnotu, která definuje týden, ke kterému dojde přechod, a <xref:System.DayOfWeek> hodnotu, která definuje den v týdnu, k němuž dojde přechod. Toto volání metody vytvoří instanci <xref:System.TimeZoneInfo.TransitionTime> objektu.

    2. Definujte čas ukončení přechodu pro úpravu časového pásma. To vyžaduje jiné volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody. Toto volání metody vytvoří instanci druhého <xref:System.TimeZoneInfo.TransitionTime> objektu.

    3. Zavolejte <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> metodu a předejte jí efektivní počáteční a koncové datum úpravy, <xref:System.TimeSpan> objekt, který definuje množství času v přechodu, a dva <xref:System.TimeZoneInfo.TransitionTime> objekty, které definují, kdy dojde k přechodu do a z letního času. Toto volání metody vytvoří instanci <xref:System.TimeZoneInfo.AdjustmentRule> objektu.

    4. Přiřaďte <xref:System.TimeZoneInfo.AdjustmentRule> objekt k poli <xref:System.TimeZoneInfo.AdjustmentRule> objektů.

2. Zadejte zobrazovaný název časového pásma. Zobrazovaný název se řídí poměrně standardním formátem, ve kterém je posun časového pásma od koordinovaného světového času (UTC) uzavřený v závorkách a následován řetězcem, který určuje časové pásmo, jednu nebo více měst v časovém pásmu nebo jednu nebo více zemí nebo oblastí v časovém pásmu.

3. Zadejte název standardního času časového pásma. Obvykle se tento řetězec používá také jako identifikátor časového pásma.

4. Zadejte název letního času časového pásma.

5. Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.

6. Vytvořte instanci <xref:System.TimeSpan> objektu, který definuje posun časového pásma od času UTC. Časová pásma s časy, které jsou pozdější než UTC, mají kladný posun. Časová pásma s časy, které jsou starší než UTC, mají záporný posun.

7. Zavolejte <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metodu pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

Následující příklad definuje centrální standardní časové pásmo pro USA, které obsahuje pravidla úprav pro celou řadu časových intervalů od 1918 do současného.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Časové pásmo vytvořené v tomto příkladu má více pravidel úprav. Je třeba dbát na to, aby se efektivní počáteční a koncové datum u libovolného pravidla úpravy nepřekrývaly s daty jiného pravidla úpravy. Pokud dojde k překrytí, <xref:System.InvalidTimeZoneException> je vyvolána výjimka.

U pravidel pro plovoucí úpravu je hodnota 5 předána `week` parametru <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody k označení toho, že přechod proběhne za poslední týden konkrétního měsíce.

Při vytváření pole <xref:System.TimeZoneInfo.AdjustmentRule> objektů, které chcete použít ve <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> volání metody, může kód inicializovat pole na velikost požadovanou počtem úprav, které mají být vytvořeny pro časové pásmo. Místo toho tento příklad kódu volá <xref:System.Collections.Generic.List%601.Add%2A> metodu pro přidání pravidla úprav do obecné <xref:System.Collections.Generic.List%601> kolekce <xref:System.TimeZoneInfo.AdjustmentRule> objektů. Kód pak zavolá <xref:System.Collections.Generic.List%601.CopyTo%2A> metodu pro zkopírování členů této kolekce do pole.

Příklad také používá <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metodu k definování úprav s pevným datem. To je podobné volání <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody s tím rozdílem, že vyžaduje pouze dobu, měsíc a den parametrů přechodu.

Příklad lze otestovat pomocí následujícího kódu:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Následující obory názvů se naimportují:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Přehled časových pásem](time-zone-overview.md)
- [Postupy: Vytváření časových pásem bez pravidel úpravy](create-time-zones-without-adjustment-rules.md)
