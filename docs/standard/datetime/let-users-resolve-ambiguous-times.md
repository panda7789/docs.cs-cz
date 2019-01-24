---
title: 'Postupy: Umožnit uživatelům řešení nejednoznačných časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae6d16bda7a2cd6f2367129b737ec79d8193ebf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502712"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Postupy: Umožnit uživatelům řešení nejednoznačných časových údajů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný univerzální čas (UTC). K tomu dochází, když čas dojde k přenastavení zpět v čase, například při přechodu z časové pásmo letního času na jeho (běžný čas). Při zpracování nejednoznačný čas, můžete provést jednu z následujících:

* Nejednoznačný čas je to položka data zadaná uživatelem,-li to můžete nechat pro uživatele, aby se vyřešit nejednoznačnost.

* Zkontrolujte předpoklady o způsobu, jakým času mapuje na čas UTC. Můžete například předpokládat, který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).

Toto téma ukazuje, jak může uživatel vyřešit nejednoznačný čas.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby mohl uživatel vyřešit nejednoznačný čas

1. Získáte datum a čas zadaný uživatelem.

2. Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodou ke zjištění, zda je nejednoznačný čas.

3. Pokud čas je nejednoznačný, zavolejte <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody k načtení pole <xref:System.TimeSpan> objekty. Každý prvek v poli obsahuje nejednoznačný čas můžete namapovat na časový posun.

4. Nechte uživatele, vyberte požadovanou posun.

5. Získáte tak, že se Posun vybrané uživatelem z místního času datum a čas UTC.

6. Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metody nastavte čas UTC data a času hodnoty <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

V následujícím příkladu se zobrazí výzva k zadání datum a čas a pokud je nejednoznačný a umožní uživateli vybrat, který mapuje nejednoznačný čas na čas UTC.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Základní příklad kódu používá pole <xref:System.TimeSpan> objektech k určení možných posunů nejednoznačný čas od času UTC. Tyto hodnoty posunu jsou však pravděpodobně srozumitelné pro uživatele. Pro objasnění významu posuny, kód rovněž uvedena, zda představuje posun místního časového pásma (běžný čas) nebo jeho letního času. Kód určuje, kdy je standardní a kdy je letního času porovnáním posun s hodnotou <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost. Tato vlastnost určuje rozdíl mezi časem UTC a časové pásmo (běžný čas).

V tomto příkladu jsou všechny odkazy na místní časové pásmo provedené prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas, zóna není nikdy přiřazeno do proměnné objektu. Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda zruší platnost objektů přiřazené k místním časovém pásmu.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Core.dll přidán do projektu.

* Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Řešení nejednoznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md)
