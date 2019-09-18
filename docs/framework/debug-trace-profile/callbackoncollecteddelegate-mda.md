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
ms.openlocfilehash: f7f5a6ef2d4e8d4a987ed74a6a04e31f87cc46f3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052935"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate – pomocník spravovaného ladění (MDA)
Pokud je delegát zařazen ze spravovaného do nespravovaného kódu jako ukazatel na funkci a na tento ukazatel funkce je umístěno zpětné volání, poté, co byl delegát uvolněn z paměti, je aktivován pomocník spravovanéholadění(MDA).`callbackOnCollectedDelegate`  
  
## <a name="symptoms"></a>Příznaky  
 K narušení přístupu dojde při pokusu o volání spravovaného kódu prostřednictvím ukazatelů na funkce, které byly získány ze spravovaných delegátů. Tyto chyby, zatímco nejsou chyby modulu CLR (Common Language Runtime), mohou vypadat tak, že v kódu CLR dojde k narušení přístupu.  
  
 Selhání není konzistentní; v některých případech se volání na ukazatel na funkci zdaří a někdy selže. K selhání může dojít pouze při velkém zatížení nebo při náhodném počtu pokusů.  
  
## <a name="cause"></a>příčina  
 Delegát, ze kterého byl ukazatel na funkci vytvořen a zpřístupněn nespravovanému kódu, byl shromážděn z paměti. Když se nespravovanou součást pokusí zavolat na ukazatel na funkci, vygeneruje porušení přístupu.  
  
 Selhání se jeví jako náhodné, protože závisí na tom, kdy dojde k uvolnění paměti. Pokud má delegát nárok na kolekci, může dojít k uvolnění paměti po zpětném volání a volání je úspěšné. V jinou dobu dojde k uvolnění paměti před zpětným voláním, zpětné volání vygeneruje porušení přístupu a program se zastaví.  
  
 Pravděpodobnost selhání závisí na době mezi zařazováním delegáta a zpětným voláním na ukazatel funkce a také frekvence uvolňování paměti. Selhání je občas v případě, že čas mezi zařazováním delegáta a následným zpětným voláním je krátký. To je obvykle případ, pokud nespravované metody, které obdrží ukazatel funkce, neuloží ukazatel na funkci pro pozdější použití, ale místo toho se před vrácením vrátí zpět na ukazatel funkce hned. Podobně další uvolňování paměti dochází v případě vysoké zátěže systému, což je pravděpodobnější, že k uvolňování paměti dojde před zpětným voláním.  
  
## <a name="resolution"></a>Řešení  
 Po zařazování delegáta jako nespravovaného ukazatele na funkci nemůže systém uvolňování paměti sledovat svoji dobu života. Místo toho musí váš kód uchovávat odkaz na delegáta po dobu života nespravovaného ukazatele na funkci. Než to ale uděláte, musíte nejdřív určit, který delegát byl shromážděn. Když je aktivováno MDA, poskytuje název typu delegáta. Použijte tento název k vyhledání kódu pro vyvolání nebo signatury modelu COM, které předají tento delegát do nespravovaného kódu. Poškozený delegát se předává přes jednu z těchto webů volání. Můžete také povolit `gcUnmanagedToManaged` službě MDA vynutit uvolňování paměti před každým zpětným voláním do modulu runtime. Tím dojde k odebrání nejistoty zavedené uvolňováním paměti tím, že zajistíte, aby se uvolňování paměti vždy před zpětným voláním. Jakmile víte, který delegát byl shromážděn, změňte kód tak, aby zůstal na spravované straně odkaz na spravovanou stranu za dobu života zařazovacího ukazatele nespravované funkce.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Když jsou delegáti zařazeni jako ukazatelé na funkce, modul runtime přidělí převod, který provede přechod z nespravovaného do spravovaného kódu. Tato rutina nespravovaného kódu ve skutečnosti volá před tím, než se spravované delegáty nakonec vyvolají. Bez povoleného `callbackOnCollectedDelegate` MDA se nespravovaný kód pro zařazování odstraní při shromáždění delegáta. Když je povolený MDA, nespravovaný kód pro zařazování se hned po shromáždění delegáta neodstraní. `callbackOnCollectedDelegate` Místo toho se ve výchozím nastavení chovají poslední instance 1 000 a při volání metody MDA se změní na aktivovat. V případě, že jsou shromažďována více zařazování delegátů, je nakonec 1 001 odstraněn převod.  
  
## <a name="output"></a>Výstup  
 MDA oznamuje název typu delegáta, který byl shromážděn před provedením zpětného volání na jeho nespravovaném ukazateli funkce.  
  
## <a name="configuration"></a>Konfiguraci  
 Následující příklad ukazuje možnosti konfigurace aplikace. Nastaví počet převodní rutiny, který se zachová, takže zůstane aktivní až 1 500. Výchozí `listSize` hodnota je 1 000, minimum je 50 a maximum je 2 000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje situaci, která může aktivovat Tento MDA:  
  
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
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
