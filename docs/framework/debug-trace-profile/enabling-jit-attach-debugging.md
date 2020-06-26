---
title: 'Povolení JIT – ladění Attach '
description: Povolit JIT (just-in time) připojit ladění pro připojení ladicího programu k procesu, když dojde k chybám Může se aktivovat určitými metodami nebo funkcemi.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: d1190c51a9cc6b5322ec832e0d35bc01dc855b12
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416041"
---
# <a name="enabling-jit-attach-debugging"></a>Povolení JIT – ladění Attach 
Ladění JIT za běhu je fráze sloužící k popisu připojení ladicího programu k procesu, když dojde k chybám, nebo může být aktivována konkrétními metodami nebo funkcemi.  
  
 Ladění JIT JIT se používá v následujících podmínkách selhání:  
  
- Neošetřené výjimky (v nativním i spravovaném kódu).  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda nebo funkce [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (řada Windows 7).  
  
- Kritické chyby modulu runtime.  
  
 Ladění JIT JIT se spouští také voláními následujících metod a funkcí:  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.  
  
- Funkce [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).  
  
 Před .NET Framework 4 poskytovala .NET Framework samostatné klíče registru pro řízení chování nativních a spravovaných ladicích programů. Počínaje .NET Framework 4 je ovládací prvek konsolidován v jednom klíči registru: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které lze nastavit pro tento klíč, určují, zda je vyvolán ladicí program, a pokud ano, zda je vyvolána s dialogovým oknem, které vyžaduje zásah uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [Konfigurace automatického ladění](/windows/win32/debug/configuring-automatic-debugging).  
  
## <a name="see-also"></a>Viz také

- [Ladění, trasování a profilace](index.md)
- [Usnadnění ladění image](making-an-image-easier-to-debug.md)
