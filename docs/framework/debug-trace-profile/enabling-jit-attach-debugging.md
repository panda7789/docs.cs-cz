---
title: 'Povolení JIT – ladění Attach '
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1696f9054d44a5f80a1f67cc38e315a8627d295
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078781"
---
# <a name="enabling-jit-attach-debugging"></a>Povolení JIT – ladění Attach 
JIT – ladění attach je frázi používají k popisu připojení ladicího programu k procesu, pokud narazíte na chyby, nebo se dá spouštět podle konkrétní metody nebo funkce.  
  
 JIT – ladění attach slouží za následujících podmínek selhání:  
  
-   Neošetřené výjimky (v nativní a spravovaný kód).  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Metoda nebo [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) – funkce (řady Windows 7).  
  
-   Závažné chyby za běhu.  
  
 JIT – ladění attach také aktivuje volání těchto metod a funkce:  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> Metoda.  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> Metoda.  
  
-   [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) – funkce (Win32).  
  
 Před [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework poskytuje klíče samostatné registru, které řídí chování ladicí programy pro nativní a spravované. Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ovládací prvek je konsolidovány do jednoho registru klíč: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které můžete nastavit pro daný klíč určit, zda ladicí program je vyvolán, a pokud ano, zda je vyvolána s dialogové okno, které vyžaduje zásah uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [konfiguraci automatického ladění](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)
- [Usnadnění ladění obrázku](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
