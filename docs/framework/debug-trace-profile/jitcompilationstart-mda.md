---
title: jitCompilationStart – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 9cae942bc01e9263720dbfe9acfb21bbb70bc548
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216262"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart – pomocník spravovaného ladění (MDA)
V případě, že kompilátor JIT (just-in-time) začne kompilovat funkci, je aktivována funkce Pomocník pro spravované ladění (MDA) `jitCompilationStart`.  
  
## <a name="symptoms"></a>Příznaky  
 Velikost pracovní sady roste pro program, který je již v nativním formátu bitové kopie, protože do procesu je načtena knihovna Mscorjit. dll.  
  
## <a name="cause"></a>Příčina  
 Ne všechna sestavení, na kterých je program závislý, byla vygenerována v nativním formátu nebo ty, které nejsou správně registrovány.  
  
## <a name="resolution"></a>Řešení  
 Povolením tohoto MDA můžete určit, která funkce je kompilována JIT. Určete, zda sestavení, které obsahuje funkci, je vygenerováno do nativního formátu a správně zaregistrováno.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA zaznamená zprávu těsně před tím, než je metoda kompilována JIT, takže povolení tohoto MDA má významný dopad na výkon. Všimněte si, že pokud je metoda vložená, negeneruje tato MDA samostatnou zprávu.  
  
## <a name="output"></a>Výstup  
 Následující ukázka kódu ukazuje vzorový výstup. V tomto případě výstup ukazuje, že v sestavení test metoda "m" ve třídě "ns2.CO" byla kompilována JIT.  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Konfigurace  
 Následující konfigurační soubor znázorňuje různé filtry, které mohou být použity k vyfiltrování, které metody jsou hlášeny při prvním kompilování JIT. Můžete určit, že budou všechny metody hlášeny nastavením hodnoty atributu name na \*.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka kódu je určena pro použití s předchozím konfiguračním souborem.  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../interop/interop-marshaling.md)
