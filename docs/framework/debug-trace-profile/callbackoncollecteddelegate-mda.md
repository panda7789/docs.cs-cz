---
title: callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
dev_langs:
- cpp
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
ms.openlocfilehash: d4ca777fa5b41433eec227762fe315f22ab33cf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174222"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
Spravovaný `callbackOnCollectedDelegate` pomocník pro ladění (MDA) je aktivován, pokud je delegát zařazen ze spravovaného na nespravovaný kód jako ukazatel funkce a zpětné volání je umístěno na tento ukazatel funkce poté, co byl delegát uvolněn.  
  
## <a name="symptoms"></a>Příznaky  
 Při pokusu o volání spravovaného kódu prostřednictvím ukazatelů funkcí, které byly získány ze spravovaných delegátů, dochází k narušení přístupu. Tyto chyby, i když nejsou běžné chyby runtime jazyka (CLR), se může zdát, že tak, protože dojde k narušení přístupu v kódu CLR.  
  
 Selhání není konzistentní; někdy volání na ukazatel funkce úspěšné a někdy se nezdaří. K selhání může dojít pouze při velkém zatížení nebo při náhodném počtu pokusů.  
  
## <a name="cause"></a>Příčina  
 Delegát, ze kterého byl vytvořen ukazatel funkce a vystaven nespravovanému kódu, byl uvolněn. Když se nespravovaná komponenta pokusí volat ukazatel funkce, vygeneruje narušení přístupu.  
  
 Selhání se zobrazí náhodné, protože závisí na při uvolnění paměti. Pokud delegát je způsobilý pro sběr, uvolnění paměti může dojít po zpětné volání a volání úspěšné. Jindy dojde k uvolnění paměti před zpětné volání, zpětné volání generuje narušení přístupu a program se zastaví.  
  
 Pravděpodobnost selhání závisí na době mezi zařazování delegáta a zpětného volání na ukazatel funkce, jakož i četnost uvolnění paměti. Selhání je sporadické, pokud je krátká doba mezi zařazování delegáta a následné zpětné volání. To je obvykle případ, pokud nespravovaná metoda přijímající ukazatel funkce neuloží ukazatel funkce pro pozdější použití, ale místo toho zavolá zpět na ukazatel funkce okamžitě dokončit svou operaci před návratem. Podobně další uvolnění paměti dojít, když je systém pod velkým zatížením, což je pravděpodobnější, že dojde k uvolnění paměti před zpětné volání.  
  
## <a name="resolution"></a>Řešení  
 Jakmile delegát byl zařazen jako ukazatel nespravované funkce, systém uvolňování paměti nemůže sledovat jeho životnost. Místo toho musí váš kód uchovávat odkaz na delegáta po dobu životnosti ukazatele nespravované funkce. Ale předtím, než to můžete udělat, musíte nejprve určit, který delegát byl shromážděn. Při aktivaci MDA, poskytuje název typu delegáta. Tento název slouží k vyhledávání kódu pro vyvolání platformy nebo podpisy COM, které předávají tento delegát na nespravovaný kód. Problematický delegát je předán prostřednictvím jednoho z těchto volání weby. Můžete také povolit `gcUnmanagedToManaged` MDA vynutit uvolnění paměti před každé zpětné volání do runtime. Tím se odstraní nejistota zavedená uvolňování paměti tím, že zajistí, že uvolnění paměti vždy dojde před zpětné volání. Jakmile budete vědět, co delegát byl shromážděn, změňte kód zachovat odkaz na tohoto delegáta na spravované straně po dobu životnosti zařazeny ukazatele nespravované funkce.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Když delegáti jsou zařazeny jako ukazatele funkce, runtime přiděluje thunk, který provádí přechod z nespravované ho spravovaného. Tato funkce thunk je to, co nespravovaný kód skutečně volá před spravovaný delegát je nakonec vyvolána. Bez `callbackOnCollectedDelegate` mda povoleno nespravované zařazování kód je odstraněn při shromažďování delegáta. S `callbackOnCollectedDelegate` MDA povoleno, nespravované zařazování kód není okamžitě odstraněn při shromažďování delegáta. Místo toho posledních 1 000 instancí jsou udržovány naživu ve výchozím nastavení a změněn a aktivovat MDA při volání. Thunk je nakonec odstraněn po 1 001 více zařazované delegáty jsou shromažďovány.  
  
## <a name="output"></a>Výstup  
 MDA hlásí název typu delegáta, který byl shromážděn před pokusem o zpětné volání na ukazatel nespravované funkce.  
  
## <a name="configuration"></a>Konfigurace  
 Následující příklad ukazuje možnosti konfigurace aplikace. Nastavuje počet thunks MDA udržuje naživu na 1500. Výchozí `listSize` hodnota je 1 000, minimum je 50 a maximální hodnota je 2 000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje situaci, která může aktivovat tento MDA:  
  
```cpp
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
```

```csharp
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
