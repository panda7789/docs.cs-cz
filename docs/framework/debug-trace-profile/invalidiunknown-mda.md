---
title: invalidIUnknown – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění invalidIUnknown – (MDA), který se aktivuje při předání neplatného ukazatele IUnknown do spravovaného kódu z nativního kódu.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051724"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown – pomocník spravovaného ladění (MDA)
`invalidIUnknown`Pokud `IUnknown` je do spravovaného kódu z nativního kódu předán neplatný ukazatel, je aktivován pomocník spravovaného ladění (MDA). `IUnknown`Při dotazování na rozhraní se nezdařila operace vrácení `IUnknown` .  
  
## <a name="symptoms"></a>Příznaky  
 Při zařazování ukazatele rozhraní modelu COM během zařazování argumentů dojde k neočekávané chybě.  
  
## <a name="cause"></a>Příčina  
 Nesprávná `QueryInterface` implementace rozhraní COM předaných modulu CLR.  
  
## <a name="resolution"></a>Řešení  
 Opravte `QueryInterface` implementaci.  
  
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
