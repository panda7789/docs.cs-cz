---
title: Povolení JIT – ladění Attach
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052827"
---
# <a name="enabling-jit-attach-debugging"></a>Povolení JIT – ladění Attach
Ladění JIT za běhu je fráze sloužící k popisu připojení ladicího programu k procesu, když dojde k chybám, nebo může být aktivována konkrétními metodami nebo funkcemi.  
  
 Ladění JIT JIT se používá v následujících podmínkách selhání:  
  
- Neošetřené výjimky (v nativním i spravovaném kódu).  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda nebo funkce [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (řada Windows 7).  
  
- Kritické chyby modulu runtime.  
  
 Ladění JIT JIT se spouští také voláními následujících metod a funkcí:  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.  
  
- Funkce [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32).  
  
 Před .NET Framework 4 poskytovala .NET Framework samostatné klíče registru pro řízení chování nativních a spravovaných ladicích programů. Počínaje .NET Framework 4 je ovládací prvek konsolidován v rámci jednoho klíče registru: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které lze nastavit pro tento klíč, určují, zda je vyvolán ladicí program, a pokud ano, zda je vyvolána s dialogovým oknem, které vyžaduje zásah uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [Konfigurace automatického ladění](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](index.md)
- [Usnadnění ladění obrázku](making-an-image-easier-to-debug.md)
