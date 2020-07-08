---
title: invalidVariant – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Invalidvariant –, který se vyvolá v případě, že při volání z nativního/nespravovaného kódu došlo k neplatnému typu VARIANT.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: ab1233d9faa86ef1508fa8fe2b5af46cb37bd523
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051633"
---
# <a name="invalidvariant-mda"></a>invalidVariant – pomocník spravovaného ladění (MDA)
`invalidVariant`Pokud `VARIANT` při volání z nativního nebo nespravovaného kódu do spravovaného kódu dojde k neplatné struktuře, aktivuje se pomocník spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané chování během přechodu mezi nativním a spravovaným kódem, který zahrnuje zařazování `VARIANT` do objektu.  
  
## <a name="cause"></a>Příčina  
 Nativní kód předá poškozenou `VARIANT` strukturu spravovanému kódu.  Modul runtime se pokusí ho zařadit `VARIANT` do objektu a aktivovat objekt MDA, pokud `VARIANT` není platný. Příklady neplatných `VARIANT` s zahrnují `VARIANT` `VARTYPE` VT_EMPTY &#124; VT_BYREF nebo `VARIANT` `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Řešení  
 Nativní nebo nespravovaný kód, který projde, `VARIANT` musí zajistit, aby `VARIANT` byl správně vytvořen a inicializován.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 MDA nemá žádný vliv na chování modulu runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva MDA označující, že modul runtime zjistil neplatnou chybu `VARIANT` předanou spravovanému modulu spravovanému kódu.  
  
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
