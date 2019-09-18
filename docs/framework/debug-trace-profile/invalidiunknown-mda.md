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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052597"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown – pomocník spravovaného ladění (MDA)
Pokud je do spravovaného kódu z nativního kódu předán neplatný `IUnknown` ukazatel, je aktivován pomocník spravovanéholadění(MDA).`invalidIUnknown` Při `IUnknown` dotazování `IUnknown` na rozhraní se nezdařila operace vrácení.  
  
## <a name="symptoms"></a>Příznaky  
 Při zařazování ukazatele rozhraní modelu COM během zařazování argumentů dojde k neočekávané chybě.  
  
## <a name="cause"></a>příčina  
 Nesprávná `QueryInterface` implementace rozhraní COM předaných modulu CLR.  
  
## <a name="resolution"></a>Řešení  
 Opravte `QueryInterface` implementaci.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Popis chyby  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
