---
title: marshalCleanupError – pomocník spravovaného ladění (MDA)
description: Projděte si pomocníka spravovaného ladění Marshalcleanuperror – (MDA), který je vyvolán, protože při čištění dočasných struktur došlo k neočekávané chybě.
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
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051607"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError – pomocník spravovaného ladění (MDA)
`marshalCleanupError`Pokud modul CLR (Common Language Runtime) zaznamená chybu při pokusu o vyčištění dočasných struktur a paměti, která se používá pro zařazování datových typů mezi nativním a spravovaným kódem, je aktivována pomocník spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Při provádění přechodů nativního a spravovaného kódu dojde k nevracení paměti, běhový stav, jako je například jazyková verze vlákna, není obnoven nebo dojde k chybám při <xref:System.Runtime.InteropServices.SafeHandle> čištění.  
  
## <a name="cause"></a>Příčina  
 Při čištění dočasných struktur došlo k neočekávané chybě.  
  
## <a name="resolution"></a>Řešení  
 Zkontrolujte všechny <xref:System.Runtime.InteropServices.SafeHandle> implementace destruktoru, finalizační metody a vlastního zařazovacího modulu pro chyby.  
  
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
