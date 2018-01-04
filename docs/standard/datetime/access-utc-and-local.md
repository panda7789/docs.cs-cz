---
title: "Postupy: přístup k místním ČASEM a předdefinované objekty zóny"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Postupy: přístup k místním ČASEM a předdefinované objekty zóny

<xref:System.TimeZoneInfo> Třída poskytuje dvě vlastnosti <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, který kód přístup k předdefinovaným objektům časových pásem. Toto téma popisuje, jak získat přístup <xref:System.TimeZoneInfo> objektů vrácený tyto vlastnosti.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Pro přístup k objektu TimeZoneInfo koordinovaného světového času (UTC)

1. Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnost, která koordinovaného světového času.

2. Místo přiřazení <xref:System.TimeZoneInfo> objekt byl vrácen vlastností proměnné objektu, i nadále přistupovat k času UTC prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnost.

### <a name="to-access-the-local-time-zone"></a>Pro přístup k místním časovém pásmu

1. Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost, která má přístup k časovému pásmu místního systému.

2. Místo přiřazení <xref:System.TimeZoneInfo> objekt byl vrácen vlastností proměnné objektu, i nadále přistupovat k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost.

## <a name="example"></a>Příklad

Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti pro převod času z USA a Kanadští východní standardní časové pásmo, jakož i zobrazovaný název časového pásma ke konzole.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

By měla vždycky přístup k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost spíše než přiřazením místního časového pásma na <xref:System.TimeZoneInfo> proměnné objektu. Podobně, byste měli vždy přistupovat koordinovaný světový čas prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> spíše než přiřazením UTC zóny na <xref:System.TimeZoneInfo> proměnné objektu. Zabrání se tak <xref:System.TimeZoneInfo> objektová proměnná před zrušením platnosti voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

* Aby byl přidán odkaz na System.Core.dll do projektu.

* Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
