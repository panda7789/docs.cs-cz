---
title: 'Postupy: řešení dvojznačných časů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122251"
---
# <a name="how-to-resolve-ambiguous-times"></a>Postupy: řešení dvojznačných časů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC). K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času. Při zpracování dvojznačného času můžete provést jednu z následujících akcí:

- Zajistěte, aby se čas namapoval na čas UTC. Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.

- Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.

V tomto tématu se dozvíte, jak vyřešit dvojznačný čas za předpokladu, že představuje standardní čas časového pásma.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Chcete-li namapovat nejednoznačný čas na běžný čas v časovém pásmu

1. Voláním metody <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> určíte, zda je čas nejednoznačný.

2. Pokud je čas dvojznačný, odečíst čas z objektu <xref:System.TimeSpan> vráceného vlastností <xref:System.TimeZoneInfo.BaseUtcOffset%2A> časového pásma.

3. Voláním metody `static` (`Shared` in Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A>) nastavte vlastnost <xref:System.DateTime.Kind%2A> hodnoty data a času UTC na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést dvojznačný čas na čas UTC za předpokladu, že představuje standardní čas místního časového pásma.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Příklad se skládá z metody s názvem `ResolveAmbiguousTime`, která určuje, zda <xref:System.DateTime> předaná hodnota je nejednoznačná. Pokud je hodnota dvojznačná, metoda vrátí <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC. Metoda zpracovává tento převod odečtením hodnoty vlastnosti <xref:System.TimeZoneInfo.BaseUtcOffset%2A> místního časového pásma z místního času.

Obvykle je nejednoznačná doba zpracována voláním metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pro načtení pole <xref:System.TimeSpan> objektů, které obsahují nejednoznačná časová posun UTC. Tento příklad ale provede libovolný předpoklad, že nejednoznačný čas by měl být vždy namapován na standardní čas časového pásma. Vlastnost <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vrací posun mezi časem UTC a standardním časem časového pásma.

V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; místní časové pásmo není nikdy přiřazeno k objektové proměnné. Toto je doporučený postup, protože volání metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> zruší platnost všech objektů, ke kterým je místní časové pásmo přiřazeno.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Obor názvů <xref:System> lze importovat pomocí příkazu `using` (požadováno v C# kódu).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Umožnění řešení nejednoznačných časových údajů pro uživatele](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
