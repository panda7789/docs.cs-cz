---
title: marshalCleanupError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 1a14c548ce960d53f47934595171189db28edfbb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216158"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError – pomocník spravovaného ladění (MDA)
Pokud se modul CLR (Common Language Runtime) vyskytne při pokusu o vyčištění dočasných struktur a paměti, která se používá pro zařazování datových typů mezi nativním a spravovaným kódem, se aktivuje Pomocník pro `marshalCleanupError` spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Při provádění přechodů nativních a spravovaných kódů dojde k nevracení paměti, běhový stav, jako je například jazyková verze vlákna, není obnoven nebo dojde k chybám při <xref:System.Runtime.InteropServices.SafeHandle> vyčištění.  
  
## <a name="cause"></a>Příčina  
 Při čištění dočasných struktur došlo k neočekávané chybě.  
  
## <a name="resolution"></a>Řešení  
 Zkontrolujte všechny implementace <xref:System.Runtime.InteropServices.SafeHandle> destruktoru, finalizační metody a vlastní zařazování pro chyby.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující operaci, která během čištění neproběhla úspěšně.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
