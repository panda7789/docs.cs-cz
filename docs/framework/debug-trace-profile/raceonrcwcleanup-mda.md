---
title: "raceOnRCWCleanup – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33d1c7d91c33c194353af43deed9329b9b4ec841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
`raceOnRCWCleanup` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) rozpozná, že [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) je v použijte, pokud je uskutečněn hovor pro uvolnění, například příkazem<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metoda.  
  
## <a name="symptoms"></a>Příznaky  
 Narušení přístupu nebo poškození paměti během nebo po uvolnění k RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.  
  
## <a name="cause"></a>příčina  
 RCW se používá na jiné vlákno nebo na uvolnění zásobníku přístup z více vláken.  Nelze uvolnit RCW, která je používána.  
  
## <a name="resolution"></a>Rozlišení  
 Není bez RCW, které by mohly být v aktuální nebo jiná vlákna.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva popisující chybu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
