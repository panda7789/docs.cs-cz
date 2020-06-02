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
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278035"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Postupy: Vytváření časových pásem bez pravidel úpravy

Přesné informace o časovém pásmu, které vyžaduje aplikace, nemusí být k dispozici v konkrétním systému z několika důvodů:

- Časové pásmo nebylo nikdy definováno v registru místního systému.

- Data o časovém pásmu byla upravena nebo odebrána z registru.

- Časové pásmo existuje, ale nemá přesné informace o úpravách časového pásma pro konkrétní historické období.

V těchto případech můžete zavolat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodu pro definování časového pásma vyžadovaného vaší aplikací. Pomocí přetížení této metody můžete vytvořit časové pásmo s pravidly úprav nebo bez nich. Pokud časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly úpravy s pevnou nebo plovoucí. (Pro definice těchto podmínek si přečtěte část "Terminologie časových pásem" v tématu [Přehled časového pásma](time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nejsou přidána do registru. Místo toho mohou být k dispozici pouze prostřednictvím odkazu objektu vráceného <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> voláním metody.

V tomto tématu se dozvíte, jak vytvořit časové pásmo bez pravidel úprav. Chcete-li vytvořit časové pásmo, které podporuje pravidla úprav letního času, přečtěte si téma [Postup: vytváření časových pásem s pravidly úpravy](create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Vytvoření časového pásma bez pravidel úpravy

1. Zadejte zobrazovaný název časového pásma.

   Zobrazovaný název se řídí poměrně standardním formátem, ve kterém je posun časového pásma od koordinovaného světového času (UTC) uzavřený v závorkách a následován řetězcem, který určuje časové pásmo, jednu nebo více měst v časovém pásmu nebo jednu nebo více zemí nebo oblastí v časovém pásmu.

2. Zadejte název standardního času časového pásma. Obvykle se tento řetězec používá také jako identifikátor časového pásma.

3. Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.

4. Vytvořte instanci <xref:System.TimeSpan> objektu, který definuje posun časového pásma od času UTC. Časová pásma s časy, které jsou pozdější než UTC, mají kladný posun. Časová pásma s časy, které jsou starší než UTC, mají záporný posun.

5. Zavolejte <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metodu pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

Následující příklad definuje vlastní časové pásmo pro Mawson, Antarktida, které nemá žádná pravidla úprav.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Řetězec přiřazený k <xref:System.TimeZoneInfo.DisplayName%2A> vlastnosti následuje po standardním formátu, ve kterém je posun časového pásma od času UTC následován popisným popisem časového pásma.

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Následující obory názvů se naimportují:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Přehled časových pásem](time-zone-overview.md)
- [Postupy: Vytváření časových pásem s pravidly úpravy](create-time-zones-with-adjustment-rules.md)
