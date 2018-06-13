---
title: 'Postupy: uživatelům řešení víceznačných časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083871dd97a36529351aacbdcd39980bdde74a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572824"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Postupy: uživatelům řešení víceznačných časových údajů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC). K tomu dojde, při času hodin se upraví zpět v čase, například při přechodu z letního času časového pásma na jeho (běžný čas). Při zpracování nejednoznačný čas, můžete provést jednu z těchto možností:

* Pokud nejednoznačný čas položky data zadaná uživatelem, můžete je nechat uživateli, aby vyřešit nejednoznačnosti.

* Zkontrolujte předpoklady o tom, jak mapuje čas UTC. Například předpokládejte, že který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).

Toto téma ukazuje, jak může uživatel vyřešit nejednoznačný čas.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby mohl uživatel, vyřešte nejednoznačný čas

1. Získá datum a čas zadaný uživatelem.

2. Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metoda k určení, zda je čas nejednoznačný.

3. Pokud je čas nejednoznačný, zavolejte <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda k načtení pole <xref:System.TimeSpan> objekty. Každý prvek v poli obsahuje časový posun můžete namapovat nejednoznačný čas.

4. Umožní uživateli vybrat požadovaný posun.

5. Získáte odečtením posun vybraný uživatelem z místního času datum a čas UTC.

6. Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodu a nastavit UTC hodnota data a času na <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad zobrazí výzvu k zadání datum a čas a pokud je nejednoznačný, umožňuje uživateli vybrat čas UTC, která mapuje nejednoznačný čas.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Základní příklad kódu používá pole <xref:System.TimeSpan> objekty pro označení možných posunů nejednoznačný čas od času UTC. Tyto posuny jsou však pravděpodobně smysl pro uživatele. O vysvětlení význam posuny, kód také popisuje, zda posunutí představuje místní časové pásmo (běžný čas) nebo jeho letní čas. Určuje kód, který čas je standardní a který čas je letní porovnáním posunu s hodnotou <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost. Tato vlastnost určuje rozdíl mezi UTC a časové pásmo (běžný čas).

V tomto příkladu jsou provedeny všechny odkazy na místní časové pásmo prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas zóny nikdy přiřazená proměnná objektu. Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda by způsobila neplatnost objekty, které je přiřazeno místní časové pásmo.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postupy: řešení víceznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md)
