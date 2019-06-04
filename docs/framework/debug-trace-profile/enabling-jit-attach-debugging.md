---
title: Povolení JIT – ladění Attach
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005395beabd956767b59e0cebd563fe883f6fe53
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489796"
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
  
 Rozhraní .NET Framework před rozhraní .NET Framework 4, poskytuje klíče samostatné registru, které řídí chování ladicí programy pro nativní a spravované. Od verze rozhraní .NET Framework 4, ovládací prvek je konsolidovány do jednoho registru klíč: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které můžete nastavit pro daný klíč určit, zda ladicí program je vyvolán, a pokud ano, zda je vyvolána s dialogové okno, které vyžaduje zásah uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [konfiguraci automatického ladění](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)
- [Usnadnění ladění obrázku](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
