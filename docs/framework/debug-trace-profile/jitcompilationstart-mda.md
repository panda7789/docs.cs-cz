---
title: jitCompilationStart – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9643a2d2ea0967b8cf6d8e18ce2e9073ae583f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387033"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart – pomocník spravovaného ladění (MDA)
`jitCompilationStart` Pomocník spravovaného ladění (MDA) se při spuštění v běhu (JIT) kompilátor zkompilovat funkci aktivuje do sestavy.  
  
## <a name="symptoms"></a>Příznaky  
 Pracovní sada větší velikostí pro program, který je již ve formátu nativních bitových kopií, protože mscorjit.dll je načten do procesu.  
  
## <a name="cause"></a>příčina  
 Ne všechny sestavení, které program závisí na byly vygenerovány do nativní formát nebo ty, které mají nejsou správně zaregistrovány.  
  
## <a name="resolution"></a>Rozlišení  
 Povolení této MDA umožňuje určit, které funkce, která má být kompilována. Určete, jestli je sestavení obsahující funkce je generována do nativní formát a řádně zaregistrován.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Tato MDA zaznamená zprávu těsně před metodu je kompilována, takže povolení této MDA má významný dopad na výkon. Všimněte si, že pokud vložené je metoda, nevygeneruje tento MDA samostatnou zprávu.  
  
## <a name="output"></a>Výstup  
 Následující příklad kódu ukazuje ukázkový výstup. Výstup ukazuje, které se v sestavení Test metody "m" na třídu "ns2.CO" v tomto případě se kompilována.  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Konfigurace  
 Následujícího konfiguračního souboru ukazuje různé filtry, které mohou být použity pro odfiltrování které metody jsou hlášené, když jsou nejprve kompilována. Můžete určit, že všechny metody hlášené nastavením hodnoty atributu název tak, aby *.  
  
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
 Následující ukázka kódu je určena pro použití s předchozím konfigurační soubor.  
  
```  
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
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
