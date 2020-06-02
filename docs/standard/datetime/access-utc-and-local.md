---
title: 'Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma'
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
ms.openlocfilehash: ebb07800b2a35f4faf312dc55b8c5679079b4b68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291406"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma

<xref:System.TimeZoneInfo>Třída poskytuje dvě vlastnosti, <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A> , které přidávají přístup kódu k předdefinovaným objektům časového pásma. Toto téma popisuje, jak získat přístup k <xref:System.TimeZoneInfo> objektům vráceným těmito vlastnostmi.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Přístup k objektu TimeZoneInfo koordinovaného univerzálního času (UTC)

1. `static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Pro přístup k koordinovanému světovému času použijte vlastnost (ve Visual Basic).

2. Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je nadále přístup k koordinovanému univerzálnímu času prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Vlastnosti.

### <a name="to-access-the-local-time-zone"></a>Přístup k místnímu časovému pásmu

1. `static` `Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Pro přístup k časovému pásmu místního systému použijte vlastnost (ve Visual Basic).

2. Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je možné pokračovat v přístupu k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Vlastnosti.

## <a name="example"></a>Příklad

Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti a k převodu času z USA a kanadského východního standardního časového pásma a také k zobrazení názvu časového pásma do konzoly.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Měli byste vždycky přistupovat k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti místo přiřazení místního časového pásma k <xref:System.TimeZoneInfo> objektové proměnné. Podobně byste měli vždycky přistupovat k koordinovanému univerzálnímu času prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti namísto přiřazení zóny UTC k <xref:System.TimeZoneInfo> objektové proměnné. Tím zabráníte <xref:System.TimeZoneInfo> zrušení platnosti proměnné objektu voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Tento <xref:System> obor názvů se naimportuje pomocí `using` příkazu (vyžaduje se v kódu jazyka C#).

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Hledání časových pásem definovaných v lokálním systému](finding-the-time-zones-on-local-system.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](instantiate-time-zone-info.md)
