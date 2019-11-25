---
title: Povolení JIT – ladění Attach
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be619f8e84b176872361fdd43faa9c704832c8e0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975587"
---
# <a name="enabling-jit-attach-debugging"></a>Povolení JIT – ladění Attach
Ladění JIT za běhu je fráze sloužící k popisu připojení ladicího programu k procesu, když dojde k chybám, nebo může být aktivována konkrétními metodami nebo funkcemi.  
  
 Ladění JIT JIT se používá v následujících podmínkách selhání:  
  
- Neošetřené výjimky (v nativním i spravovaném kódu).  
  
- Metoda <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> nebo funkce [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) (řada Windows 7)  
  
- Kritické chyby modulu runtime.  
  
 Ladění JIT JIT se spouští také voláními následujících metod a funkcí:  
  
- Metoda <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.  
  
- Metoda <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.  
  
- Funkce [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) (Win32).  
  
 Před .NET Framework 4 poskytovala .NET Framework samostatné klíče registru pro řízení chování nativních a spravovaných ladicích programů. Počínaje .NET Framework 4 je ovládací prvek konsolidován v jednom klíči registru: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Hodnoty, které lze nastavit pro tento klíč, určují, zda je vyvolán ladicí program, a pokud ano, zda je vyvolána s dialogovým oknem, které vyžaduje zásah uživatele. Informace o nastavení tohoto klíče registru najdete v tématu [Konfigurace automatického ladění](/windows/win32/debug/configuring-automatic-debugging).  
  
## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](index.md)
- [Usnadnění ladění obrázku](making-an-image-easier-to-debug.md)
