---
title: 'Postupy: vytváření časových pásem s pravidly úpravy'
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
ms.openlocfilehash: 4ef3d93746c5688dc15fc7e45d9be054dcfba4c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132557"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Postupy: vytváření časových pásem s pravidly úpravy

Přesné informace o časovém pásmu, které vyžaduje aplikace, nemusí být k dispozici v konkrétním systému z několika důvodů:

- Časové pásmo nebylo nikdy definováno v registru místního systému.

- Data o časovém pásmu byla upravena nebo odebrána z registru.

- Časové pásmo nemá správné informace o úpravách časového pásma pro konkrétní historické období.

V těchto případech můžete zavolat metodu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> pro definování časového pásma vyžadovaného vaší aplikací. Pomocí přetížení této metody můžete vytvořit časové pásmo s pravidly úprav nebo bez nich. Pokud časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly úpravy s pevnou nebo plovoucí. (Pro definice těchto podmínek si přečtěte část "Terminologie časových pásem" v tématu [Přehled časového pásma](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časová pásma vytvořená voláním metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> nejsou přidána do registru. Místo toho mohou být k dispozici pouze prostřednictvím odkazu objektu vráceného voláním metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.

V tomto tématu se dozvíte, jak vytvořit časové pásmo s pravidly úprav. Chcete-li vytvořit časové pásmo, které nepodporuje pravidla pro úpravu letního času, přečtěte si téma [Postup: vytváření časových pásem bez pravidel úprav](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Vytvoření časového pásma s plovoucími pravidly úpravy

1. Pro každou úpravu (tj. pro každý přechod mimo určitý časový interval a zpět na běžný čas) udělejte toto:

    1. Definujte dobu zahájení přechodu pro úpravu časového pásma.

       Musíte zavolat metodu <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> a předat jí hodnotu <xref:System.DateTime>, která definuje čas přechodu, celočíselnou hodnotu, která definuje měsíc přechodu, celočíselnou hodnotu, která definuje týden, ke kterému dojde přechod, a hodnotu <xref:System.DayOfWeek>, která definuje den v týdnu, kdy dojde k přechodu. Toto volání metody vytvoří instanci objektu <xref:System.TimeZoneInfo.TransitionTime>.

    2. Definujte čas ukončení přechodu pro úpravu časového pásma. To vyžaduje jiné volání metody <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>. Tato metoda volá instanci druhého objektu <xref:System.TimeZoneInfo.TransitionTime>.

    3. Zavolejte metodu <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> a předejte jí efektivní počáteční a koncové datum úpravy, objekt <xref:System.TimeSpan>, který definuje množství času v přechodu, a dva objekty <xref:System.TimeZoneInfo.TransitionTime>, které definují, kdy dojde k přechodu do a z letního času. Toto volání metody vytvoří instanci objektu <xref:System.TimeZoneInfo.AdjustmentRule>.

    4. Přiřaďte objekt <xref:System.TimeZoneInfo.AdjustmentRule> k poli objektů <xref:System.TimeZoneInfo.AdjustmentRule>.

2. Zadejte zobrazovaný název časového pásma. Zobrazovaný název se řídí poměrně standardním formátem, ve kterém je posun časového pásma od koordinovaného světového času (UTC) uzavřený v závorkách a následován řetězcem, který určuje časové pásmo, jednu nebo více měst v časovém pásmu nebo jeden nebo více COU. ntries nebo oblasti v časovém pásmu.

3. Zadejte název standardního času časového pásma. Obvykle se tento řetězec používá také jako identifikátor časového pásma.

4. Zadejte název letního času časového pásma.

5. Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.

6. Vytvořte instanci objektu <xref:System.TimeSpan> definující posun časového pásma od času UTC. Časová pásma s časy, které jsou pozdější než UTC, mají kladný posun. Časová pásma s časy, které jsou starší než UTC, mají záporný posun.

7. Pro vytvoření instance nového časového pásma volejte metodu <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad definuje centrální standardní časové pásmo pro USA, které obsahuje pravidla úprav pro celou řadu časových intervalů od 1918 do současného.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Časové pásmo vytvořené v tomto příkladu má více pravidel úprav. Je třeba dbát na to, aby se efektivní počáteční a koncové datum u libovolného pravidla úpravy nepřekrývaly s daty jiného pravidla úpravy. Pokud dojde k překrytí, je vyvolána <xref:System.InvalidTimeZoneException>.

Pro pravidla plovoucího nastavení je hodnota 5 předána parametru `week` metody <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>, aby označovala, že přechod proběhne za poslední týden konkrétního měsíce.

Při vytváření pole objektů <xref:System.TimeZoneInfo.AdjustmentRule> pro použití ve volání metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> může kód inicializovat pole na velikost požadovanou počtem úprav, které mají být vytvořeny pro časové pásmo. Místo toho tento příklad kódu volá metodu <xref:System.Collections.Generic.List%601.Add%2A> pro přidání pravidla úprav do obecné <xref:System.Collections.Generic.List%601> kolekce <xref:System.TimeZoneInfo.AdjustmentRule> objektů. Kód pak zavolá metodu <xref:System.Collections.Generic.List%601.CopyTo%2A> ke zkopírování členů této kolekce do pole.

Tento příklad také používá metodu <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> k definování úprav s pevným datem. To je podobné volání metody <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>, s tím rozdílem, že vyžaduje pouze dobu, měsíc a den parametrů přechodu.

Příklad lze otestovat pomocí následujícího kódu:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Následující obory názvů se naimportují:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
