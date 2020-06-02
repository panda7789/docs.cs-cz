---
title: 'Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: ac723738d80a2f686a5fcaf279cec791b3c58619
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281580"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC). K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času. Při zpracování dvojznačného času můžete provést jednu z následujících akcí:

- Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.

- Zajistěte, aby se čas namapoval na čas UTC. Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.

V tomto tématu se dozvíte, jak umožnit uživateli vyřešit nejednoznačný čas.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby uživatel mohl vyřešit nejednoznačný čas

1. Získá uživateli zadání data a času.

2. Zavolejte <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodu pro zjištění, zda je čas nejednoznačný.

3. Pokud je čas dvojznačný, zavolejte <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodu pro načtení pole <xref:System.TimeSpan> objektů. Každý prvek v poli obsahuje časový posun UTC, na který může být mapován dvojznačný čas.

4. Umožní uživateli vybrat požadovaný posun.

5. Získá datum a čas UTC odečtením posunu vybraného uživatelem od místního času.

6. Zavolejte `static` metodu ( `Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> , chcete-li nastavit vlastnost hodnoty data a času UTC <xref:System.DateTime.Kind%2A> na hodnotu <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="example"></a>Příklad

Následující příklad vyzve uživatele k zadání data a času a, pokud je dvojznačný, umožňuje uživateli vybrat čas UTC, ke kterému se nejednoznačná doba mapuje.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Jádro ukázkového kódu používá pole <xref:System.TimeSpan> objektů k označení možných posunů nejednoznačného času od času UTC. Tyto posuny ale pravděpodobně nebudou smysluplné pro uživatele. Pro objasnění významu posunu kód také Poznamenejte, zda posun představuje standardní čas místního časového pásma nebo jeho letní čas. Kód určuje, který čas je standardní a který čas je letní, porovnáním posunu s hodnotou <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Vlastnosti. Tato vlastnost označuje rozdíl mezi časem UTC a standardním časem časového pásma.

V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Vlastnosti; místní časové pásmo není nikdy přiřazeno k objektové proměnné. Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody zruší platnost všech objektů, které jsou přiřazeny k místnímu časovému pásmu.

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Tento <xref:System> obor názvů se naimportuje pomocí `using` příkazu (vyžaduje se v kódu jazyka C#).

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Postupy: Řešení nejednoznačných časových údajů](resolve-ambiguous-times.md)
