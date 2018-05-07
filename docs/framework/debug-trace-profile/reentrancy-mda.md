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
ms.openlocfilehash: 5aea903a7b16491a84998d8290270044e167b79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="reentrancy-mda"></a>vícenásobný přístup MDA
`reentrancy` Pomocník spravovaného ladění (MDA) se aktivuje, když je proveden pokus o přechod z nativní do spravovaného kódu v případech, kdy nebyla provedena předchozí přepínač ze spravovaného na nativní kódu prostřednictvím uspořádání přechodu.  
  
## <a name="symptoms"></a>Příznaky  
 Je poškozena halda objekt nebo jiné závažné chyby dochází při přechodu z nativní do spravovaného kódu.  
  
 Vláken, která přepínat mezi nativního a spravovaného kódu v obou směrech musíte provést uspořádání přechodu. Však určité body rozšiřitelnosti nízké úrovně v operačním systému, jako je například obslužná rutina výjimky vectored, povolit přepínače ze spravovaných do nativního kódu bez uspořádání přechodu.  Tyto přepínače jsou pod kontrolou operačního systému, a nikoli podle běžného ovládacího prvku language runtime (CLR).  Nativní kód, který provede uvnitř tyto body rozšiřitelnosti musí Vyhněte se volání zpět do spravovaného kódu.  
  
## <a name="cause"></a>příčina  
 Bod rozšiřitelnost nízké úrovně operačního systému, jako je například obslužná rutina výjimky vectored, aktivoval při provádění spravovaného kódu.  Aplikační kód, který lze vyvolat pomocí tohoto bodu rozšíření se pokouší o zpětného volání do spravovaného kódu.  
  
 Tento problém je způsoben vždy kódu aplikace.  
  
## <a name="resolution"></a>Rozlišení  
 Zkontrolujte trasování zásobníku pro vlákno, které tento MDA aktivoval.  Vlákno se pokouší o nelegálního volání do spravovaného kódu.  Trasování zásobníku byste měli odhalit kódu aplikace pomocí tohoto bodu rozšiřitelnost, kód operačního systému, který poskytuje tento bod rozšiřitelnost a spravovaný kód, který byl přerušen bodem rozšíření.  
  
 Například uvidíte MDA za pokus o volání spravovaného kódu z uvnitř obslužné rutiny výjimek vectored aktivuje.  V zásobníku uvidíte zpracování kód a některé spravovaného kódu, která aktivuje výjimku, jako výjimek operačního systému <xref:System.DivideByZeroException> nebo <xref:System.AccessViolationException>.  
  
 V tomto příkladu je na správné řešení implementace obslužná rutina výjimky vectored zcela v nespravovaném kódu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA nemá žádný vliv na modulu CLR.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že probíhá pokus o neplatné opětovné zadání.  Zkontrolujte zásobníku podprocesu určit, proč k této situaci a jak problém vyřešit. Následuje příklad výstupu.  
  
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
 Následující kód například příčiny <xref:System.AccessViolationException> vyvolání.  Ve verzích systému Windows, které podporují vectored výjimek způsobí obslužná rutina výjimky spravované vectored k volání.  Pokud `reentrancy` MDA je povoleno, MDA aktivují během pokusu o volání `MyHandler` z operačního systému vectored výjimky podporu kód pro zpracování.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
