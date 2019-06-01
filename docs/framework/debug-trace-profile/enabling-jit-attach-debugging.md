---
title: Povolení JIT – ladění Attach
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 088ca6dd8973a626b1f028c638e60bf995af1e65
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457315"
---
# <a name="enabling-jit-attach-debugging"></a>Povolení JIT – ladění Attach
JIT – ladění attach je frázi používají k popisu připojení ladicího programu k procesu, pokud narazíte na chyby, nebo se dá spouštět podle konkrétní metody nebo funkce.  
  
 JIT – ladění attach slouží za následujících podmínek selhání:  
  
- Neošetřené výjimky (v nativní a spravovaný kód).  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Metoda nebo [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) – funkce (řady Windows 7).  
  
- Závažné chyby za běhu.  
  
 JIT – ladění attach také aktivuje volání těchto metod a funkce:  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> Metoda.  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> Metoda.  
  
- [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) – funkce (Win32).  
  
 Před [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework poskytuje klíče samostatné registru, které řídí chování ladicí programy pro nativní a spravované. Od verze rozhraní .NET Framework 4, ovládací prvek je konsolidovány do jednoho registru klíč: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které můžete nastavit pro daný klíč určit, zda ladicí program je vyvolán, a pokud ano, zda je vyvolána s dialogové okno, které vyžaduje zásah uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [konfiguraci automatického ladění](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)
- [Usnadnění ladění obrázku](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
