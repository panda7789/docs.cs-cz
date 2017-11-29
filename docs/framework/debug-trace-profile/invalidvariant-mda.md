---
title: "invalidVariant – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ee537dcb03dc76968b829f827c73542c07922a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="invalidvariant-mda"></a>invalidVariant – pomocník spravovaného ladění (MDA)
`invalidVariant` Pomocník spravovaného ladění (MDA) se aktivuje, když neplatný `VARIANT` struktura je došlo během volání z nativní nebo nespravovaného kódu do spravovaného kódu.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané chování během přechodu mezi nativní a spravované kódové zahrnující zařazování z `VARIANT` k objektu.  
  
## <a name="cause"></a>příčina  
 Nativní kód je předávání chybná `VARIANT` struktura do spravovaného kódu.  Modul runtime pokusí zařazování to `VARIANT` na objekt a aktivuje MDA, pokud `VARIANT` není platný. Příkladem neplatné `VARIANT`S zahrnout `VARIANT` s `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Rozlišení  
 Kód nativní nebo nespravované předávání `VARIANT` musíte zajistit, aby `VARIANT` správně vytvořen a inicializován.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 MDA nemá žádný vliv na modul runtime chování.  
  
## <a name="output"></a>Výstup  
 MDA zpráva označující, že modul runtime zjistil neplatný `VARIANT` předal modul nespravovaného do spravovaného kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
