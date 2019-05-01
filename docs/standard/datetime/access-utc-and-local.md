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
ms.openlocfilehash: c10c07c08a4e676cf3c84a5722814eaed85f74a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026602"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma

<xref:System.TimeZoneInfo> Třída poskytuje dvě vlastnosti <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, který kód přístup k předdefinované objekty časového pásma. Toto téma popisuje, jak získat přístup k <xref:System.TimeZoneInfo> objektů vrácených podle vlastností.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Pro přístup k objektu TimeZoneInfo koordinovaný univerzální čas (UTC)

1. Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti pro přístup k koordinovaný světový čas.

2. Místo toho <xref:System.TimeZoneInfo> objekt vráceného vlastností do proměnné objektu, dál přístup k koordinovaný světový čas prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnost.

### <a name="to-access-the-local-time-zone"></a>Pro přístup k místním časovém pásmu

1. Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti přístupu k časovému pásmu místního systému.

2. Místo toho <xref:System.TimeZoneInfo> objekt vráceného vlastností do proměnné objektu, dál přístup k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost.

## <a name="example"></a>Příklad

Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti pro převod z USA a Kanadské standardní východní časové pásmo času, jakož i zobrazovaný název časového pásma do konzoly.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

By měla vždycky přístup k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost spíše než přiřazením místního časového pásma na <xref:System.TimeZoneInfo> proměnné objektu. Podobně by měla vždycky přístup koordinovaný světový čas prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> spíše než přiřazením čas UTC pásma <xref:System.TimeZoneInfo> proměnné objektu. Díky tomu <xref:System.TimeZoneInfo> proměnné objektu před zrušením platnosti voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

* Aby byl odkaz na System.Core.dll přidán do projektu.

* Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
