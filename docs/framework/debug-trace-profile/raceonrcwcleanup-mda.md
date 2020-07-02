---
title: raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění raceOnRCWCleanup – (MDA), který se aktivuje, pokud se RCW používá v jiném vlákně nebo na uvolňování zásobníku vláken v rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803648"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
`raceOnRCWCleanup`Pomocník spravovaného ladění (MDA) je aktivován, když modul CLR (Common Language Runtime) zjistí, že se používá obálka s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW), když volání uvolní, je provedeno pomocí příkazu, jako je například <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> metoda.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
