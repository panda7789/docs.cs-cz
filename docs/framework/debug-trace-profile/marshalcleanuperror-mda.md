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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab3690cac28ef572b19cadb632662590d1ea04c7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052484"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError – pomocník spravovaného ladění (MDA)
Pokud modul CLR (Common Language Runtime) zaznamená chybu při pokusu o vyčištění dočasných struktur a paměti, která se používá pro zařazování datových typů mezi nativním a spravovaným kódem, je aktivována pomocník spravovanéholadění(MDA).`marshalCleanupError`  
  
## <a name="symptoms"></a>Příznaky  
 Při provádění přechodů nativního a spravovaného kódu dojde k nevracení paměti, běhový stav, jako je například jazyková verze vlákna <xref:System.Runtime.InteropServices.SafeHandle> , není obnoven nebo dojde k chybám při čištění.  
  
## <a name="cause"></a>příčina  
 Při čištění dočasných struktur došlo k neočekávané chybě.  
  
## <a name="resolution"></a>Řešení  
 Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> implementace destruktoru, finalizační metody a vlastního zařazovacího modulu pro chyby.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva oznamující operaci, která během čištění neproběhla úspěšně.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
