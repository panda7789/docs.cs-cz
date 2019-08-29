---
title: 'Postupy: Vytváření časových pásem bez pravidel úpravy'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 510112c8b19ec002d1dcf918eb983b55dee68fd0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106659"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Postupy: Vytváření časových pásem bez pravidel úpravy

Přesné informace o časovém pásmu, které vyžaduje aplikace, nemusí být k dispozici v konkrétním systému z několika důvodů:

- Časové pásmo nebylo nikdy definováno v registru místního systému.

- Data o časovém pásmu byla upravena nebo odebrána z registru.

- Časové pásmo existuje, ale nemá přesné informace o úpravách časového pásma pro konkrétní historické období.

V těchto případech můžete zavolat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodu pro definování časového pásma vyžadovaného vaší aplikací. Pomocí přetížení této metody můžete vytvořit časové pásmo s pravidly úprav nebo bez nich. Pokud časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly úpravy s pevnou nebo plovoucí. (Pro definice těchto podmínek si přečtěte část "Terminologie časových pásem" v tématu [Přehled časového pásma](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nejsou přidána do registru. Místo toho mohou být k dispozici pouze prostřednictvím odkazu objektu vráceného <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> voláním metody.

V tomto tématu se dozvíte, jak vytvořit časové pásmo bez pravidel úprav. Pokud chcete vytvořit časové pásmo, které podporuje pravidla úprav letního času, [Přečtěte si téma How to: Vytváření časových pásem s pravidly](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)úpravy

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Vytvoření časového pásma bez pravidel úpravy

1. Zadejte zobrazovaný název časového pásma.

   Zobrazovaný název se řídí poměrně standardním formátem, ve kterém je posun časového pásma od koordinovaného světového času (UTC) uzavřený v závorkách a následován řetězcem, který určuje časové pásmo, jednu nebo více měst v časovém pásmu nebo jeden nebo více COU. ntries nebo oblasti v časovém pásmu.

2. Zadejte název standardního času časového pásma. Obvykle se tento řetězec používá také jako identifikátor časového pásma.

3. Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.

4. Vytvořte instanci objektu, který definuje posun časového pásma od času UTC. <xref:System.TimeSpan> Časová pásma s časy, které jsou pozdější než UTC, mají kladný posun. Časová pásma s časy, které jsou starší než UTC, mají záporný posun.

5. <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> Zavolejte metodu pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

Následující příklad definuje vlastní časové pásmo pro Mawson, Antarktida, které nemá žádná pravidla úprav.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Řetězec přiřazený k <xref:System.TimeZoneInfo.DisplayName%2A> vlastnosti následuje po standardním formátu, ve kterém je posun časového pásma od času UTC následován popisným popisem časového pásma.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Následující obory názvů se naimportují:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
