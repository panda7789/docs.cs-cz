---
title: invalidVariant – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 64f5a4425d70974bae8c4f7bec28041e687fe95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228481"
---
# <a name="invalidvariant-mda"></a>invalidVariant – pomocník spravovaného ladění (MDA)
`invalidVariant` Pomocníka spravovaného ladění (MDA) se aktivuje, když neplatný `VARIANT` struktura dochází při volání z nativní nebo nespravovaného kódu pro spravovaný kód.  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané chování během přechodu mezi nativním a spravovaným kódem zahrnující zařazování z `VARIANT` na objekt.  
  
## <a name="cause"></a>Příčina  
 Nativní kód předává poškozené `VARIANT` struktura se spravovaným kódem.  Modul runtime pokusí zařazování to `VARIANT` na objekt a aktivuje MDA, pokud `VARIANT` není platný. Příklady neplatných `VARIANT`S zahrnout `VARIANT` s `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Řešení  
 Nativní nebo nespravovaný kód předá `VARIANT` musíte zajistit, aby `VARIANT` je správně vytvořen a inicializován.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 MDA nemá žádný vliv na chování modulu runtime.  
  
## <a name="output"></a>Výstup  
 MDA zpráva oznamující, že modul runtime zjistil neplatný `VARIANT` předávány modul nespravovaného do spravovaného kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
