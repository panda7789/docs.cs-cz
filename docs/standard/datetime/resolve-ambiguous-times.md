---
title: 'Postupy: Řešení nejednoznačných časových údajů'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106787"
---
# <a name="how-to-resolve-ambiguous-times"></a>Postupy: Řešení nejednoznačných časových údajů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný světový čas (UTC). K tomu dochází, když se změní čas v čase, například během přechodu z letního času v časovém pásmu do standardního času. Při zpracování dvojznačného času můžete provést jednu z následujících akcí:

- Zajistěte, aby se čas namapoval na čas UTC. Můžete například předpokládat, že nejednoznačná doba je vždy vyjádřena v časovém pásmu standardního času.

- Pokud je nejednoznačným časem položka dat zadaná uživatelem, můžete ji ponechat uživateli, aby vyřešila nejednoznačnost.

V tomto tématu se dozvíte, jak vyřešit dvojznačný čas za předpokladu, že představuje standardní čas časového pásma.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Chcete-li namapovat nejednoznačný čas na běžný čas v časovém pásmu

1. <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> Zavolejte metodu pro zjištění, zda je čas nejednoznačný.

2. Pokud je čas dvojznačný, odečíst čas od <xref:System.TimeSpan> objektu vráceného <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastností časového pásma.

3. <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.DateTime.Kind%2A> Zavolejte metodu`Shared` (in Visual Basic .NET), chcete-li nastavit vlastnost hodnoty data a času UTC na hodnotu. `static`

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést dvojznačný čas na čas UTC za předpokladu, že představuje standardní čas místního časového pásma.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Příklad se skládá z metody s názvem `ResolveAmbiguousTime` , která určuje, <xref:System.DateTime> zda je předaná hodnota nejednoznačná. Pokud je hodnota dvojznačná, metoda vrátí <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC. Metoda zpracovává tento převod odečtením hodnoty <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnosti místního časového pásma z místního času.

Obvykle je nejednoznačná doba zpracována voláním <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody pro načtení <xref:System.TimeSpan> pole objektů, které obsahují nejednoznačná časová posun UTC. Tento příklad ale provede libovolný předpoklad, že nejednoznačný čas by měl být vždy namapován na standardní čas časového pásma. <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Vlastnost vrací posun mezi časem UTC a standardním časem časového pásma.

V tomto příkladu jsou všechny odkazy na místní časové pásmo provedeny prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti; místní časové pásmo není nikdy přiřazeno k objektové proměnné. Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody zruší platnost všech objektů, které jsou přiřazeny k místnímu časovému pásmu.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Tento obor názvů se naimportuje `using` pomocí příkazu (vyžaduje C# se v kódu). <xref:System>

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Umožnit uživatelům řešení nejednoznačných časů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
