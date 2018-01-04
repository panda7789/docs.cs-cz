---
title: "callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5459efbb07aa235bd7c1d34ffd6b56195fe0bf1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
`callbackOnCollectedDelegate` Pomocník spravovaného ladění (MDA) se aktivuje, pokud je delegáta zařazen ze spravovaného na nespravovaný kód jako ukazatel na funkci a zpětné volání je umístěn na tento ukazatel na funkci po uvolnění z paměti delegát.  
  
## <a name="symptoms"></a>Příznaky  
 Při pokusu o volání do spravovaného kódu pomocí ukazatele na funkce, které byly získány ze spravovaných delegáti dojít k porušení přístupu. Tyto chyby při není common language runtime (CLR) chyb, může se zdát, vzhledem k tomu, že dojde k porušení přístupu v kódu CLR.  
  
 Selhání není konzistentní; Někdy je úspěšné volání na ukazatel funkce a v některých případech se nezdaří. Selhání může dojít pouze v případě velkého zatížení nebo na náhodných počet pokusů.  
  
## <a name="cause"></a>příčina  
 Delegát, ze kterého byl vytvořen a vystavené na nespravovaný kód ukazatel na funkci se uvolnění z paměti. Když komponentu nespravované se pokusí zavolat na ukazatel na funkci, vygeneruje porušení přístupu.  
  
 Selhání se zobrazí náhodné, protože závisí na při uvolňování paměti. Pokud delegát je vhodné pro kolekce, kolekce paměti může vzniknout po zpětného volání a volání bude úspěšné. V jinou dobu dojde k uvolnění paměti před zpětné volání, zpětné volání vygeneruje porušení přístupu a program se zastaví.  
  
 Pravděpodobnost selhání závisí na čas mezi zařazování delegáta a zpětného volání na ukazatel na funkci, jakož i četnost kolekce. Selhání je výskyt občasný, pokud je krátká doba mezi zařazování delegáta a následná zpětného volání. Je tomu tak obvykle Pokud nespravované metoda přijetí ukazatel na funkci neukládá ukazatel funkce pro pozdější použití, ale místo toho volání zpět na ukazatel funkce okamžitě na dokončení jeho operace před vrácením. Podobně další probíhalo uvolňování paměti při systému je přetížen, takže je pravděpodobnější, že dojde k uvolnění paměti před zpětné volání.  
  
## <a name="resolution"></a>Rozlišení  
 Jakmile delegáta byl zařazen se jako ukazatel Nespravované funkce, nemůže sledovat garbage collector v celé jeho životnosti. Místo toho kódu musí je udržovat v odkazu na delegáta po dobu jeho existence ukazatel Nespravované funkce. Ale předtím, než můžete to udělat, je nejprve nutné určit delegáta, který byl shromážděn. Po aktivaci MDA poskytuje název typu delegáta. Použijte tento název pro vyhledávání kódu pro platformu vyvolání nebo COM podpisy, které předat přidělíte nespravovaný kód. Problematické delegáta je předána jednu z těchto volání lokalit. Můžete také povolit `gcUnmanagedToManaged` MDA vynutit uvolňování před každou zpětného volání do modulu runtime. Tato akce odebere nejistoty zaváděné uvolňování zajištěním, které kolekce paměti vždy předchází zpětné volání. Jakmile již víte, jaké delegáta byl shromážděn a měnit kód zachovat odkaz na tohoto delegáta na straně pro spravované po dobu jeho existence zařazené nespravované funkce ukazatele.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Když Delegáti jsou zařazené jako ukazatelů na funkce, modul runtime přiděluje převodu, která provádí přechod z nespravovaných do spravovaných. Tato převodu je co nespravovaného kódu ve skutečnosti volá před spravovaný nakonec vyvolání delegáta. Bez `callbackOnCollectedDelegate` MDA povolené, nespravovaného kódu zařazování se odstraní, jakmile se shromažďují delegát. Pomocí `callbackOnCollectedDelegate` MDA povolené, nespravovaného kódu zařazování se neodstraní okamžitě po shromážděných delegát. Posledních 1000 instance místo toho se ukládají zachování připojení ve výchozím nastavení a změnit tak, aby aktivovat MDA při volání. Odstraní jinou bitovou šířku se nakonec po 1,001 více zařazené delegáti se shromažďují.  
  
## <a name="output"></a>Výstup  
 MDA hlásí název typu delegáta, který byl shromážděn před zpětné volání došlo k pokusu o jeho ukazatel Nespravované funkce.  
  
## <a name="configuration"></a>Konfigurace  
 Následující příklad ukazuje možnosti konfigurace aplikace. Nastaví počet převody, které MDA zachová aktivní na 1 500. Výchozí hodnota `listSize` hodnota je 1 000, minimální hodnota je 50 a maximální hodnota je 2000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje situaci, které můžou aktivovat tuto (mda):  
  
```  
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}  
// ---------------------------------------------------  
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
