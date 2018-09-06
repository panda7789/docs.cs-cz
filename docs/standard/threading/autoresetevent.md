---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7602a61a4403b7ab85015876823aa41e250b23de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863306"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Třída představuje místní čekání popisovač událost, která se automaticky obnoví při signalizován po uvolnění jedno vlákno čekání. Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle>. Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce automatického resetu událostí.  
  
 <xref:System.Threading.AutoResetEvent> Objekt je automaticky obnovit do nesignálového systém po vydala jedno vlákno čekání. Pokud žádná vlákna čekající, zůstane signalizovaného stavu objektu události. <xref:System.Threading.AutoResetEvent> odpovídá Win32 `CreateEvent` volání, určení `false` pro `bManualReset` argument.  
  
 Příklad, který používá <xref:System.Threading.AutoResetEvent>, naleznete v tématu <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Dělení na vlákna](../../../docs/standard/threading/index.md)  
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Obslužné rutiny čekání](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
