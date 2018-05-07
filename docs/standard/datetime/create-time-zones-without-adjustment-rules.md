---
title: 'Postupy: vytváření časových pásem bez pravidel úpravy'
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
ms.openlocfilehash: 214e3bca811f87f4b8367b459564449d16e7c289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Postupy: vytváření časových pásem bez pravidel úpravy

Informace o přesné časovém pásmu, který je požadován pro aplikace nemusí být na určitém systému k dispozici pro několik důvodů:

* Časové pásmo nikdy byla definována v registru místního systému.

* Data o časovém pásmu byl změněn nebo odstraněn z registru.

* Časové pásmo existuje, ale nemá přesné informace o úpravách časové pásmo pro určité historické období.

V těchto případech můžete volat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda definovat časové pásmo požadované aplikací. Přetížení této metody můžete vytvořit časové pásmo s nebo bez pravidel úpravy. Pokud se časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly buď pevné nebo plovoucí úpravy. (Pro definice těchto podmínkách, najdete v části "Časové pásmo terminologií" v [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nejsou přidány do registru. Místo toho jsou dostupné pouze prostřednictvím odkazu na objekt vrácený <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> volání metody.

Toto téma ukazuje, jak vytvořit časové pásmo bez pravidel úpravy. Vytvoření časové pásmo, které podporuje pravidla úpravy letního času naleznete v tématu [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Chcete-li vytvořit časové pásmo bez pravidel úpravy

1. Definujte časové pásmo zobrazovaný název.

   Zobrazovaný název následuje poměrně standardní formát, ve kterém posun časového pásma z koordinovaný světový čas (UTC) uzavřený v závorkách a následuje řetězec, který identifikuje časové pásmo, jeden nebo více měst v časovém pásmu, nebo v jednom nebo více cou oložky nebo oblasti v časovém pásmu.

2. Definuje název časové pásmo (běžný čas). Obvykle se tento řetězec se používá jako identifikátor časového pásma.

3. Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.

4. Vytváření instancí <xref:System.TimeSpan> objekt, který definuje posun časového pásma od času UTC. Časová pásma s časy, které jsou novější než čas UTC mít kladný posun. Časová pásma s časy, které jsou starší než čas UTC mít záporný posun.

5. Volání <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metoda pro vytvoření instance nového časového pásma.

## <a name="example"></a>Příklad

V následujícím příkladu definuje vlastní časové pásmo pro Mawson, Antarctica, který nemá žádná pravidla úprav.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Řetězec přiřazený k <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost následuje standardní formát, ve kterém je posun časového pásma od času UTC Následuje stručný popis časové pásmo.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Aby byly importované následujících oborů názvů:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
[postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
