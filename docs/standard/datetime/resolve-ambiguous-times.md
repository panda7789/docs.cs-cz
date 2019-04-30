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
ms.openlocfilehash: aae3e5145d2fa85cd55fc5b1288ef4aaa0fef48f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796406"
---
# <a name="how-to-resolve-ambiguous-times"></a>Postupy: Řešení nejednoznačných časových údajů

Nejednoznačný čas je čas, který se mapuje na více než jeden koordinovaný univerzální čas (UTC). K tomu dochází, když čas dojde k přenastavení zpět v čase, například při přechodu z časové pásmo letního času na jeho (běžný čas). Při zpracování nejednoznačný čas, můžete provést jednu z následujících:

* Zkontrolujte předpoklady o způsobu, jakým času mapuje na čas UTC. Můžete například předpokládat, který nejednoznačný čas je vždy vyjádřené v časovém pásmu (běžný čas).

* Nejednoznačný čas je to položka data zadaná uživatelem,-li to můžete nechat pro uživatele, aby se vyřešit nejednoznačnost.

Toto téma ukazuje, jak vyřešit nejednoznačný čas za předpokladu, že představuje časové pásmo (běžný čas).

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>K namapování nejednoznačný čas na časové pásmo (běžný čas)

1. Volání <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodou ke zjištění, zda je nejednoznačný čas.

2. Pokud čas je nejednoznačný, odečíst čas <xref:System.TimeSpan> vrácený časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost.

3. Volání `static` (`Shared` v jazyce Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metody nastavte čas UTC data a času hodnoty <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést nejednoznačný čas na čas UTC podle předpokladu, že představuje místní časové pásmo (běžný čas).

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

V příkladu se skládá z metodu s názvem `ResolveAmbiguousTime` , který určuje, zda <xref:System.DateTime> předaná hodnota je nejednoznačný. Pokud hodnota je nejednoznačný, metoda vrátí <xref:System.DateTime> hodnotu, která představuje odpovídající čas UTC. Tato metoda obsluhuje tento převod tak, že se hodnota místní časové pásmo <xref:System.TimeZoneInfo.BaseUtcOffset%2A> vlastnost z místního času.

Obvykle je zpracována nejednoznačný čas voláním <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody k načtení pole <xref:System.TimeSpan> posuny objektů, které obsahují možná nejednoznačný čas UTC. V tomto příkladu je však libovolného předpokladu, že by vždy nejednoznačný čas musí být mapováno na časové pásmo (běžný čas). <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Vlastnost vrací posun mezi UTC a časové pásmo (běžný čas).

V tomto příkladu jsou všechny odkazy na místní časové pásmo provedené prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost; místní čas, zóna není nikdy přiřazeno do proměnné objektu. Toto je doporučený postup, protože volání <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda zruší platnost objektů přiřazené k místním časovém pásmu.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Core.dll přidán do projektu.

* Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Umožnit uživatelům řešení nejednoznačných časových údajů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
