---
title: 'Postupy: převod nejednoznačných časů uživatelů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122280"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Postupy: převod nejednoznačných časů uživatelů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC). K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času. Při zpracování dvojznačného času můžete provést jednu z následujících akcí:

- Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.

- Zajistěte, aby se čas namapoval na čas UTC. Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.

V tomto tématu se dozvíte, jak umožnit uživateli vyřešit nejednoznačný čas.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby uživatel mohl vyřešit nejednoznačný čas

1. Získá uživateli zadání data a času.

2. Voláním metody <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> určíte, zda je čas nejednoznačný.

3. Pokud je čas dvojznačný, zavolejte metodu <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pro načtení pole objektů <xref:System.TimeSpan>. Každý prvek v poli obsahuje časový posun UTC, na který může být mapován dvojznačný čas.

4. Umožní uživateli vybrat požadovaný posun.

5. Získá datum a čas UTC odečtením posunu vybraného uživatelem od místního času.

6. Voláním metody `static` (`Shared` in Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A>) nastavte vlastnost <xref:System.DateTime.Kind%2A> hodnoty data a času UTC na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad vyzve uživatele k zadání data a času a, pokud je dvojznačný, umožňuje uživateli vybrat čas UTC, ke kterému se nejednoznačná doba mapuje.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Jádro ukázkového kódu používá pole objektů <xref:System.TimeSpan> k označení možných posunů nejednoznačného času od času UTC. Tyto posuny ale pravděpodobně nebudou smysluplné pro uživatele. Pro objasnění významu posunu kód také Poznamenejte, zda posun představuje standardní čas místního časového pásma nebo jeho letní čas. Kód určuje, který čas je standardní a který čas je letní, porovnáním posunu s hodnotou vlastnosti <xref:System.TimeZoneInfo.BaseUtcOffset%2A>. Tato vlastnost označuje rozdíl mezi časem UTC a standardním časem časového pásma.

V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; místní časové pásmo není nikdy přiřazeno k objektové proměnné. Toto je doporučený postup, protože volání metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> zruší platnost všech objektů, ke kterým je místní časové pásmo přiřazeno.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Obor názvů <xref:System> lze importovat pomocí příkazu `using` (požadováno v C# kódu).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Řešení nejednoznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md)
