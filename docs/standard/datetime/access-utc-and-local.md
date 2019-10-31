---
title: 'Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132609"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu

Třída <xref:System.TimeZoneInfo> poskytuje dvě vlastnosti, <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, které poskytují přístup kódu k předdefinovaným objektům časového pásma. Toto téma popisuje, jak získat přístup k objektům <xref:System.TimeZoneInfo> vráceným těmito vlastnostmi.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Přístup k objektu TimeZoneInfo koordinovaného univerzálního času (UTC)

1. Pro přístup k koordinovanému univerzálnímu času použijte vlastnost <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> `static` (`Shared` in Visual Basic).

2. Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je nadále přístup k koordinovanému univerzálnímu času prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.

### <a name="to-access-the-local-time-zone"></a>Přístup k místnímu časovému pásmu

1. Pro přístup k časovému pásmu místního systému použijte vlastnost `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.

2. Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností do proměnné objektu pokračuje v přístupu k místnímu časovému pásmu prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.

## <a name="example"></a>Příklad

Následující kód používá vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> k převodu času z USA a kanadského východního standardního časového pásma a také k zobrazení názvu časového pásma pro konzolu.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Měli byste vždycky přistupovat k místnímu časovému pásmu prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> místo přiřazení místního časového pásma k proměnné objektu <xref:System.TimeZoneInfo>. Podobně byste měli vždycky přistupovat k koordinovanému univerzálnímu času prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> místo přiřazení zóny UTC k proměnné objektu <xref:System.TimeZoneInfo>. Tím zabráníte zrušení platnosti proměnné objektu <xref:System.TimeZoneInfo> voláním metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Obor názvů <xref:System> lze importovat pomocí příkazu `using` (požadováno v C# kódu).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
