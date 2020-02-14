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
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216277"
---
# <a name="invalidvariant-mda"></a>invalidVariant – pomocník spravovaného ladění (MDA)
Pokud při volání z nativního nebo nespravovaného kódu do spravovaného kódu dojde k neplatnému `VARIANT` struktury, aktivuje se Pomocník s `invalidVariant`em spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané chování během přechodu mezi nativním a spravovaným kódem, který zahrnuje zařazování `VARIANT` do objektu.  
  
## <a name="cause"></a>Příčina  
 Nativní kód předá poškozenou strukturu `VARIANT` spravovanému kódu.  Modul runtime se pokusí o zařazení tohoto `VARIANT` objektu a aktivuje hodnotu MDA, pokud je `VARIANT` neplatná. Příklady neplatných `VARIANT`S zahrnují `VARIANT` s `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Řešení  
 Nativní nebo nespravovaný kód, který předává `VARIANT`, musí zajistit, aby byl `VARIANT` správně vytvořen a inicializován.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 MDA nemá žádný vliv na chování modulu runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva MDA označující, že modul runtime zjistil neplatnou `VARIANT` předal spravovanému kódu nespravovaný modul.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
