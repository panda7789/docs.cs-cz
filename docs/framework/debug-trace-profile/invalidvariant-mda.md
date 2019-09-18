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
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052564"
---
# <a name="invalidvariant-mda"></a>invalidVariant – pomocník spravovaného ladění (MDA)
Pokud při volání z nativního nebo nespravovaného kódu do `VARIANT` spravovaného kódu dojde k neplatné struktuře, aktivuje se pomocník spravovanéholadění(MDA).`invalidVariant`  
  
## <a name="symptoms"></a>Příznaky  
 Neočekávané chování během přechodu mezi nativním a spravovaným kódem, který zahrnuje zařazování `VARIANT` do objektu.  
  
## <a name="cause"></a>příčina  
 Nativní kód předá poškozenou `VARIANT` strukturu spravovanému kódu.  Modul runtime se pokusí ho zařadit `VARIANT` do objektu a aktivovat objekt MDA, `VARIANT` Pokud není platný. `VARIANT`Příklady neplatných s zahrnují `VARIANT` `VARTYPE` a VT_EMPTY &#124; VT_BYREF nebo `VARIANT` s `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Řešení  
 Nativní nebo nespravovaný kód, `VARIANT` `VARIANT` který projde, musí zajistit, aby byl správně vytvořen a inicializován.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 MDA nemá žádný vliv na chování modulu runtime.  
  
## <a name="output"></a>Výstup  
 Zpráva MDA označující, že modul runtime zjistil neplatnou `VARIANT` chybu předanou spravovanému modulu spravovanému kódu.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
