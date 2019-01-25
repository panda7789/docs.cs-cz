---
title: vícenásobný přístup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18189ace97238bede9ed18d1dcbae2490956fad8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498593"
---
# <a name="reentrancy-mda"></a>vícenásobný přístup MDA
`reentrancy` Pomocníka spravovaného ladění (MDA) se aktivuje, když je proveden pokus o přechod z nativní do spravovaného kódu v případech, kdy se neprovedla předchozí přepínač ze spravovaného do nativního kódu prostřednictvím uspořádání přechodu.  
  
## <a name="symptoms"></a>Příznaky  
 Objekt haldy je poškozený nebo jiné závažné chyby dochází při přesunu z nativní do spravovaného kódu.  
  
 Vlákna, která přepínat mezi nativním a spravovaným kódem v obou směrech musíte provést uspořádání přechodu. Určitých bodů rozšiřitelnosti nízké úrovně v operačním systému, jako je například vektorové obslužné rutiny výjimek, ale umožní přepínače ze spravované do nativního kódu bez uspořádání přechodu.  Tyto přepínače jsou v rámci ovládacího prvku operačního systému, nikoli ovládány language runtime (CLR).  Nativní kód, který se spustí v těmto rozšiřujícím bodům musí Vyhněte se volání zpět do spravovaného kódu.  
  
## <a name="cause"></a>Příčina  
 Bodu rozšiřitelnosti nízké úrovně operačního systému, jako je například vektorové obslužné rutiny výjimek, je aktivován při provádění spravovaného kódu.  Kód aplikace, která je volána pomocí tohoto bodu rozšiřitelnosti se pokouší volat zpět do spravovaného kódu.  
  
 Tento problém je způsoben vždy kódem aplikace.  
  
## <a name="resolution"></a>Rozlišení  
 Prozkoumejte trasování zásobníku pro vlákno, které se má toto MDA aktivováno.  Vlákno se pokouší o neoprávněně volat do spravovaného kódu.  Trasování zásobníku by měl odhalit kódu aplikace pomocí tohoto bodu rozšiřitelnost, kód operačního systému, který poskytuje tento bod rozšiřitelnost a spravovaný kód, který bylo přerušeno bodu rozšiřitelnosti.  
  
 Uvidíte MDA aktivováno při pokusu o volání spravovaného kódu z uvnitř vektorové obslužné rutiny výjimek.  V zásobníku uvidíte zpracování kódu a spravovaného kódu aktivuje výjimku, jako výjimek operačního systému <xref:System.DivideByZeroException> nebo <xref:System.AccessViolationException>.  
  
 V tomto příkladu je na správné řešení úplně implementace vektorové obslužné rutiny výjimek v nespravovaném kódu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že probíhá pokus o neplatné opětovné zadání.  Prozkoumejte zásobníku vlákna, chcete-li zjistit, proč dochází k tomu a pokyny k vyřešení problému. Tady je ukázkový výstup.  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad způsobí, že kód <xref:System.AccessViolationException> vyvolání.  Ve verzích Windows, která podporuje zpracování výjimek vektorové to způsobí, že spravované vektorové obslužné rutiny výjimek má být volána.  Pokud `reentrancy` MDA je povoleno, MDA se aktivují během pokusu o volání `MyHandler` z operačního systému vektorové výjimky podporu kód pro zpracování.  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
