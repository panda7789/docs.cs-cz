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
ms.openlocfilehash: d14ba8724659172711da44e7bb249e9d20768dbc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052339"
---
# <a name="reentrancy-mda"></a>vícenásobný přístup MDA
Při pokusu o přechod z nativního kódu do spravovaného kódu se aktivuje pomocník spravovanéholadění(MDA),protožepředchozípřepínačzespravovanéhodonativníhokódunebylprovedenprostřednictvímpřechodupodlepořadí.`reentrancy`  
  
## <a name="symptoms"></a>Příznaky  
 Halda objektu je poškozena nebo dojde k jiným závažným chybám při přechodu z nativního kódu do spravovaného kódu.  
  
 Vlákna, která přepínají mezi nativním a spravovaným kódem v obou směrech, musí provádět přechod na objednávku. Nicméně některé body rozšiřitelnosti na nízké úrovni v operačním systému, jako je vektorová obslužná rutina výjimky, umožňují přepínání ze spravovaného do nativního kódu bez nutnosti přechodu do konkrétního pořadí.  Tyto přepínače jsou v rámci řízení operačního systému, nikoli v rámci řízení modulu CLR (Common Language Runtime).  Jakýkoliv nativní kód, který se spouští uvnitř těchto bodů rozšiřitelnosti, se musí vyhnout volání zpět do spravovaného kódu.  
  
## <a name="cause"></a>příčina  
 Bod rozšiřitelnosti operačního systému nižší úrovně, jako je například vektorová obslužná rutina výjimky, byl aktivován při spuštění spravovaného kódu.  Kód aplikace, který je vyvolán prostřednictvím tohoto bodu rozšiřitelnosti, se pokouší o zpětné volání zpět do spravovaného kódu.  
  
 Tento problém je vždy způsoben kódem aplikace.  
  
## <a name="resolution"></a>Řešení  
 Prověřte trasování zásobníku pro vlákno, které aktivovalo Tento MDA.  Vlákno se pokouší o neoprávněné volání spravovaného kódu.  Trasování zásobníku by mělo odhalit kód aplikace pomocí tohoto bodu rozšiřitelnosti, kódu operačního systému, který poskytuje tento bod rozšiřitelnosti, a spravovaného kódu, který byl přerušen bodem rozšiřitelnosti.  
  
 Například se zobrazí informace MDA aktivované při pokusu o volání spravovaného kódu zevnitř vektorové obslužné rutiny výjimky.  V zásobníku se zobrazí kód pro zpracování výjimek operačního systému a určitý spravovaný kód, který aktivuje výjimku, jako je <xref:System.DivideByZeroException> například <xref:System.AccessViolationException>nebo.  
  
 V tomto příkladu je správné řešení implementovat vektorovou obslužnou rutinu výjimky zcela v nespravovaném kódu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 Dojde k pokusu o vyřízení sestav s neplatným Vícenásobný přístup.  Zkontrolujte zásobník vlákna, abyste zjistili, proč k tomu dochází, a jak problém vyřešit. Následuje ukázkový výstup.  
  
```output
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu způsobí, že <xref:System.AccessViolationException> bude vyvolána výjimka.  Ve verzích Windows, které podporují zpracování vektorových výjimek, to způsobí, že bude volána spravovaná vektorová obslužná rutina výjimky.  Pokud je povolený `MyHandler` MDA,běhempokusuovolánízkódupodporyzpracovánívektorovévýjimkyvoperačnímsystému`reentrancy` se aktivuje.  
  
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

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
