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
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681713"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Postupy: Vytváření časových pásem bez pravidel úpravy

Informace přesné časové pásmo, který vyžaduje aplikace nemusí být k dispozici na konkrétní systém z několika důvodů:

* Časové pásmo je nikdy definována v registru místního systému.

* Data o časovém pásmu, byla změněna nebo odebrána z registru.

* Časové pásmo existuje, ale nemá žádné přesné informace o úpravách časové pásmo pro konkrétní období historické.

V těchto případech můžete volat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda k definování časové pásmo požadovaná vaší aplikací. Přetížení této metody můžete použít k vytvoření časové pásmo s nebo bez pravidel úpravy. Podporuje-li časové pásmo letního času, můžete definovat úpravy pomocí pravidla buď pevnou nebo plovoucí úpravy. (Definice těchto pojmů najdete v části "Časové pásmo terminologie" v [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časové pásmo vytvořených voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nejsou přidány do registru. Místo toho jsou dostupné jenom prostřednictvím odkazu na objekt vrácený <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> volání metody.

Toto téma ukazuje, jak vytvořit časových pásem bez pravidel úpravy. Vytvoření časového pásma, které podporuje pravidla úpravy letního času, najdete v tématu [jak: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Chcete-li vytvořit časových pásem bez pravidel úpravy

1. Definujte časové pásmo zobrazovaný název.

   Zobrazovaný název následuje poměrně standardní formát, ve kterém časovém pásmu posun od koordinovaného světového času (UTC) není uzavřen v závorkách a následuje řetězec, který určí časové pásmo, jeden nebo více měst v časovém pásmu, nebo v jednom nebo více následujících cou oložky nebo oblasti v časovém pásmu.

2. Definujte název časového pásma (běžný čas). Obvykle tento řetězec se také používá jako identifikátor časového pásma.

3. Pokud chcete použít jiný identifikátor než název standardního časového pásma, definujte identifikátor časového pásma.

4. Vytvořit instanci <xref:System.TimeSpan> objekt, který definuje posun časového pásma UTC. Časových pásem s časem, které jsou novější než čas UTC mít kladný posun. Časových pásem s časem, které jsou starší než čas UTC, mají negativní posun.

5. Volání <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metoda pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

Následující příklad definuje vlastní časové pásmo pro Mawson, základna Antarktida, který nemá žádná pravidla úprav.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Řetězec přiřazený k <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost následuje standardní formát, ve kterém posun časového pásma od UTC Následuje stručný popis časového pásma.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Core.dll přidán do projektu.

* Aby byly importované následující obory názvů:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
