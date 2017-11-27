---
title: "Postupy: řešení víceznačných časových údajů"
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
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a>Postupy: řešení víceznačných časových údajů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC). K tomu dojde, při času hodin se upraví zpět v čase, například při přechodu z letního času časového pásma na jeho (běžný čas). Při zpracování nejednoznačný čas, můžete provést jednu z těchto možností:

* Zkontrolujte předpoklady o tom, jak mapuje čas UTC. Například předpokládejte, že který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).

* Pokud nejednoznačný čas položky data zadaná uživatelem, můžete je nechat uživateli, aby vyřešit nejednoznačnosti.

Toto téma ukazuje, jak vyřešit nejednoznačný čas za předpokladu, že představuje časové pásmo (běžný čas).

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Pro mapování nejednoznačný čas na časové pásmo (běžný čas)

1. Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metoda k určení, zda je čas nejednoznačný.

2. Pokud je čas nejednoznačný, odečtena čas z <xref:System.TimeSpan> objekt vrácený časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost.

3. Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodu a nastavit UTC hodnota data a času na <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést nejednoznačný čas UTC podle předpokladu, že představuje místní časové pásmo (běžný čas).

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

V příkladu se skládá z metodu s názvem `ResolveAmbiguousTime` který určuje, zda <xref:System.DateTime> hodnotu do ní předán je nejednoznačný. Pokud hodnota je nejednoznačné, vrátí metoda <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC. Tato metoda obsluhuje tento převod odečtením hodnoty místní časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost z místního času.

Obvykle je nejednoznačný čas zpracováván voláním <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda k načtení pole <xref:System.TimeSpan> objekty, které obsahují nejednoznačný čas UTC možné posun. V tomto příkladu však umožňuje libovolné předpoklad, že nejednoznačný čas musí být vždy mapována na časové pásmo (běžný čas). <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Vlastnost vrací posun mezi ČASEM a časové pásmo (běžný čas).

V tomto příkladu jsou provedeny všechny odkazy na místní časové pásmo prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas zóny nikdy přiřazená proměnná objektu. Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda by způsobila neplatnost objekty, které je přiřazeno místní časové pásmo.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postup: uživatelům řešení víceznačných časových údajů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
