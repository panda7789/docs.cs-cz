---
title: "pInvokeStackImbalance – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b33a3edc5780ecf07e7809ca327a304d748110f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokestackimbalance-mda"></a>pInvokeStackImbalance – pomocník spravovaného ladění (MDA)
`pInvokeStackImbalance` Pomocník spravovaného ladění (MDA) se aktivuje, když modulu CLR zjistí, že hloubka zásobníku po volání nespravovaného neodpovídá očekávané zásobníku hloubka, danou konvence volání, které jsou zadané v <xref:System.Runtime.InteropServices.DllImportAttribute> atribut společně s prohlášení o parametrech v spravované podpis.  
  
> [!NOTE]
>  `pInvokeStackImbalance` MDA je implementována pouze pro 32-bit x86 platformy.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 3.5 `pInvokeStackImbalance` MDA ve výchozím nastavení vypnutá. Při použití rozhraní .NET Framework verze 3.5 s Visual Studio 2005 `pInvokeStackImbalance` MDA se objeví v **Pomocníci spravovaného ladění** seznamu v **výjimky** dialogové okno (což je zobrazí, když kliknutí na tlačítko **výjimky** na **ladění** nabídky). Ale zaškrtnete nebo zrušíte zaškrtnutí **vyvolaná** zaškrtnutí políčka pro `pInvokeStackImbalance` povolit nebo zakázat MDA; pouze řídí, zda Visual Studio vyvolá výjimku, pokud je aktivován (mda).  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace dojde narušení přístupu nebo paměti při vytváření nebo následující platformu poškození vyvolat volání.  
  
## <a name="cause"></a>příčina  
 Spravované podpis platformy vyvolat volání nespravovaného podpis metody volané se nemusí shodovat.  Tato neshoda může být způsobeno spravované podpis není deklarace správný počet parametrů nebo není zadáte odpovídající velikost pro parametry.  MDA můžete také aktivovat, protože konvence volání, které by mohly mít určeného <xref:System.Runtime.InteropServices.DllImportAttribute> atribut, neodpovídá nespravované konvence volání.  
  
## <a name="resolution"></a>Rozlišení  
 Zkontrolujte spravovaná platforma vyvolání podpis a konvence volání potvrďte, že odpovídá podpisu a konvence volání nativní cíle.  Zkuste explicitně zadat konvence volání na spravovaných a nespravovaných stranách. Je také možné, i když ne jako pravděpodobné, že nevyvážené nespravované funkce v zásobníku z jiného důvodu, jako je například chyby v nespravované kompilátoru.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Vynutí vyvolání všechny platformy volání cestou nonoptimized v modulu CLR.  
  
## <a name="output"></a>Výstup  
 Zpráva MDA poskytuje název platformy vyvolat volání metody, která je příčinou nevyváženosti zásobníku.  Volání metody vyvolání ukázkovou zprávu platformy `SampleMethod` je:  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
