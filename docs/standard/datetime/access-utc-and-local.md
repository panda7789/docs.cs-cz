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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106556"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma

Třída poskytuje dvě vlastnosti, <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, které přidávají přístup kódu k předdefinovaným objektům časového pásma. <xref:System.TimeZoneInfo> Toto téma popisuje, jak získat přístup <xref:System.TimeZoneInfo> k objektům vráceným těmito vlastnostmi.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Přístup k objektu TimeZoneInfo koordinovaného univerzálního času (UTC)

1. Pro přístup k`Shared` koordinovanému světovému času použijte vlastnost <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>(ve Visual Basic). `static`

2. Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je nadále přístup k koordinovanému univerzálnímu času <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> prostřednictvím vlastnosti.

### <a name="to-access-the-local-time-zone"></a>Přístup k místnímu časovému pásmu

1. Pro přístup k`Shared` časovému pásmu místního systému použijte vlastnost <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>(ve Visual Basic). `static`

2. Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je možné pokračovat v přístupu k místnímu časovému pásmu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> prostřednictvím vlastnosti.

## <a name="example"></a>Příklad

Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> k převodu času z USA a kanadského východního standardního časového pásma a také k zobrazení názvu časového pásma do konzoly.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Měli byste vždycky přistupovat k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti místo přiřazení místního časového pásma <xref:System.TimeZoneInfo> k objektové proměnné. Podobně byste měli vždycky přistupovat k koordinovanému univerzálnímu času <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> prostřednictvím vlastnosti namísto přiřazení zóny UTC <xref:System.TimeZoneInfo> k objektové proměnné. Tím zabráníte <xref:System.TimeZoneInfo> zrušení platnosti proměnné objektu voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Tento obor názvů se naimportuje `using` pomocí příkazu (vyžaduje C# se v kódu). <xref:System>

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
