---
title: raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216199"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
Pokud modul CLR (Common Language Runtime) zjistí, že se používá [obálka](../../standard/native-interop/runtime-callable-wrapper.md) RCW (Runtime), je-li volání k vydání vyvoláno pomocí příkazu, jako je například metoda <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>, je aktivována pomocná aplikace `raceOnRCWCleanup` Managed Debugging Assistant (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Porušení přístupu nebo poškození paměti během nebo po uvolnění RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.  
  
## <a name="cause"></a>Příčina  
 RCW se používá v jiném vlákně nebo v uvolňování zásobníku vláken.  RCW, který se používá, nelze uvolnit.  
  
## <a name="resolution"></a>Řešení  
 Neuvolňujte RCW, které by bylo možné použít v aktuálním nebo jiném vlákně.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva popisující chybu  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
