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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 459465064fe9db9f2f0aebb4153a3caea173af4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875066"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
`callbackOnCollectedDelegate` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud delegát je zařazen ze spravovaného do nespravovaného kódu jako ukazatel na funkci a zpětné volání je umístěn na tento ukazatel na funkci delegáta byla uvolněna z paměti.  
  
## <a name="symptoms"></a>Příznaky  
 Při pokusu o volání spravovaného kódu prostřednictvím ukazatele na funkce, které jste získali z spravovaných delegáty, dojde k narušení přístupu. Tyto chyby při není common language runtime (CLR) chyb, které může zobrazit, protože dojde k porušení přístupu v kódu CLR.  
  
 Selhání není konzistentní; v některých případech bude úspěšné volání na ukazatel funkce a někdy nezdaří. Pouze v případě velkého zatížení nebo na náhodné číslo pokusů o přihlášení, může dojít k selhání.  
  
## <a name="cause"></a>Příčina  
 Delegát, ze kterého byla vytvořena a vystavit na nespravovaný kód ukazatel na funkci byla uvolněna z paměti. Když se nespravované součásti se pokusí zavolat na ukazatel funkce, generuje narušení přístupu.  
  
 Selhání se zobrazí náhodné, protože závisí na, když dojde k uvolnění paměti. Pokud delegát má nárok na kolekce, kolekce uvolnění paměti může vzniknout po zpětném volání a bude volání úspěšné. V jinou dobu před zpětné volání dojde k uvolnění paměti, zpětné volání vygeneruje narušení přístupu a program se zastaví.  
  
 Pravděpodobnost selhání závisí na čas mezi zařazování delegáta a zpětné volání na ukazatel funkce, jakož i frekvence uvolnění paměti. Selhání je sporadické, pokud je krátký čas mezi zařazování delegáta a následné zpětného volání. To je obvykle tento případ, pokud nespravované metoda přijímá ukazatel na funkci nelze uložit ukazatel na funkci pro pozdější použití, ale místo toho zavolá zpět na ukazatel funkce okamžitě na dokončení jeho operace před vrácením. Podobně další kolekce dojít, když je systém v případě velkého zatížení, což zvyšuje pravděpodobnost, že uvolňování paměti dojde před zpětného volání.  
  
## <a name="resolution"></a>Řešení  
 Jakmile si byl zařazen delegáta jako ukazatel nespravovanou funkci, systému uvolňování paměti nelze sledovat svého životního cyklu. Místo toho kód uchovává odkaz na delegáta po dobu životnosti ukazatel nespravované funkci. Ale předtím, než budete moct provést, nejprve musíte určit, které delegát byl shromážděn. Když MDA aktivováno, obsahuje název typu delegáta. Použijte tento název hledání kódu pro platformu vyvolání nebo COM podpisy, které předat tento delegát navýšení kapacity na nespravovaný kód. Problematické delegáta se předává jednu z těchto místa volání. Můžete také povolit `gcUnmanagedToManaged` MDA vynutit uvolnění před každé zpětné volání do modulu runtime. Tato akce odebere nejistoty zavedené kolekce paměti zajištěním uvolnění vždy předchází zpětnému volání. Jakmile budete vědět, jaké delegáta byl shromážděn, změňte kód pro odkaz na tohoto delegáta na straně spravované pro dobu života ukazatele zařazené nespravované funkci.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Když jsou delegáti zařadit jako ukazatele funkcí, modul runtime přiděluje převodní rutina, která provádí přechod z nespravovaných do spravovaných. Tento převod je co nespravovaný kód volá vlastně před spravovanou nakonec je vyvolán delegát. Bez `callbackOnCollectedDelegate` MDA povolena, nespravované zařazování kód se odstraní při delegáta se shromažďují. S `callbackOnCollectedDelegate` MDA povolena, nespravované zařazování kódu se neodstraní okamžitě po shromážděných delegáta. Místo toho jsou poslední 1 000 instancí udržována nehledě ve výchozím nastavení a změnit aktivovat MDA při volání. Po 1,001 více zařazené Delegáti jsou shromážděná se nakonec odstraní převodní rutině.  
  
## <a name="output"></a>Výstup  
 MDA sestavy název typu delegáta, který byl shromážděn předtím, než došlo k pokusu o zpětné volání v jeho ukazatel nespravované funkci.  
  
## <a name="configuration"></a>Konfigurace  
 Následující příklad ukazuje možnosti konfigurace aplikace. Nastaví počet převodní rutiny, které MDA zachová aktivní na 1 500. Výchozí hodnota `listSize` hodnota je 1 000, minimální hodnota je 50 a maximální hodnota je 2000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje situaci, která může aktivovat toto MDA:  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
