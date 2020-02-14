---
title: invalidIUnknown – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217369"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown – pomocník spravovaného ladění (MDA)
V případě, že je do spravovaného kódu z nativního kódu předán neplatný ukazatel `IUnknown`, je aktivován Pomocník s `invalidIUnknown` Managed Debugging Assistant (MDA). `IUnknown` se při dotazování na rozhraní `IUnknown` nepodařilo vrátit úspěch.  
  
## <a name="symptoms"></a>Příznaky  
 Při zařazování ukazatele rozhraní modelu COM během zařazování argumentů dojde k neočekávané chybě.  
  
## <a name="cause"></a>Příčina  
 Nesprávná implementace `QueryInterface` v rozhraní COM předanému modulu CLR.  
  
## <a name="resolution"></a>Řešení  
 Opravte implementaci `QueryInterface`.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Popis chyby.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
