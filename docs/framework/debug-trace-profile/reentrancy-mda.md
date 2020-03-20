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
ms.openlocfilehash: 5cbe8e843ad72785010240f3db30b1d344c80650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181769"
---
# <a name="reentrancy-mda"></a>vícenásobný přístup MDA
Spravovaný `reentrancy` ladicí asistent (MDA) je aktivován při pokusu o přechod z nativního na spravovaný kód v případech, kdy předchozí přechod ze spravovaného na nativního kódu nebyl proveden prostřednictvím řádného přechodu.  
  
## <a name="symptoms"></a>Příznaky  
 Halda objektu je poškozennebo jiné závažné chyby dochází při přechodu z nativní do spravovaného kódu.  
  
 Vlákna, která přepínají mezi nativním a spravovaným kódem v obou směrech, musí provést řádný přechod. Některé nízkoúrovňové body rozšiřitelnosti v operačním systému, jako je například obslužná rutina vektorové výjimky, však umožňují přepínače ze spravovaného na nativního kódu bez provedení spořádaného přechodu.  Tyto přepínače jsou pod kontrolou operačního systému, nikoli pod kontrolou CLR (COMMON Language runtime).  Jakýkoli nativní kód, který se spustí uvnitř těchto bodů rozšiřitelnosti, se musí vyhnout volání zpět do spravovaného kódu.  
  
## <a name="cause"></a>Příčina  
 Při provádění spravovaného kódu byl aktivován bod rozšiřitelnosti operačního systému nižší úrovně, například obslužná rutina vektorové výjimky.  Kód aplikace, který je vyvolán prostřednictvím tohoto bodu rozšiřitelnosti se pokouší volat zpět do spravovaného kódu.  
  
 Tento problém je vždy způsoben kódem aplikace.  
  
## <a name="resolution"></a>Řešení  
 Zkontrolujte trasování zásobníku pro vlákno, které aktivovalo tento MDA.  Podproces se pokouší nelegálně volat do spravovaného kódu.  Trasování zásobníku by mělo odhalit kód aplikace pomocí tohoto bodu rozšiřitelnosti, kód operačního systému, který poskytuje tento bod rozšiřitelnosti, a spravovaný kód, který byl přerušen bodem rozšiřitelnosti.  
  
 Například uvidíte MDA aktivován ve snaze volat spravovaný kód zevnitř vektorované výjimky obslužné rutiny.  V zásobníku uvidíte kód zpracování výjimek operačního systému <xref:System.DivideByZeroException> <xref:System.AccessViolationException>a některé spravované kódy, které aktivují výjimku, jako je například nebo .  
  
 V tomto příkladu je správné rozlišení implementovat vektorovou obslužnou rutinu výjimky zcela v nespravovaném kódu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na běhový čas  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA hlásí, že se pokouší o nelegální reentrancy.  Zkontrolujte zásobníku vlákna k určení, proč se to děje a jak opravit problém. Následuje ukázkový výstup.  
  
```output
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
 Následující příklad kódu <xref:System.AccessViolationException> způsobí, že vyvolá.  Ve verzích systému Windows, které podporují zpracování vektorových výjimek, to způsobí, že bude volána spravovaná obslužná rutina výjimky.  Pokud `reentrancy` je povoleno MDA, MDA aktivuje během pokusu o `MyHandler` volání z operačního systému vektorované výjimky zpracování podpůrného kódu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
