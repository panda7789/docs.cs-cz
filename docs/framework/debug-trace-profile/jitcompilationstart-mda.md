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
ms.openlocfilehash: cd4d1be3ec3c64c7c6669a2c85ba6bf68db6da68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536760"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart – pomocník spravovaného ladění (MDA)
`jitCompilationStart` Pomocníka spravovaného ladění (MDA) je aktivován do sestavy, když začne kompilátor just-in-time (JIT) kompilaci funkce.  
  
## <a name="symptoms"></a>Příznaky  
 Pracovní sada pro program, který je již ve formátu nativní bitové kopie, protože mscorjit.dll je načten do procesu se zvětší.  
  
## <a name="cause"></a>Příčina  
 Ne všechna sestavení, které program závisí na byly vytvořeny v nativním formátu, nebo ty, které mají nejsou správně registrovány.  
  
## <a name="resolution"></a>Rozlišení  
 Povolení toto MDA umožňuje určit, které funkce, která má být zkompilovaný pomocí kompilátoru JIT. Určete, zda je sestavení, které obsahuje funkce generované nativním formátu a správně registrována.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA zaznamená zprávu těsně před plánovaným metodu zkompilovaný pomocí kompilátoru JIT, takže umožňuje toto MDA má významný dopad na výkon. Všimněte si, že pokud je metoda vložené, nevygeneruje toto MDA samostatnou zprávu.  
  
## <a name="output"></a>Výstup  
 Následující příklad kódu ukazuje příklad výstupu. V tomto případě ukazuje výstup, které v sestavení testovací metoda "m" ve třídě "ns2.CO" byl zkompilován JIT Kompilátorem.  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Konfigurace  
 Následující konfigurační soubor ukazuje různé filtry, které mohou být použity pro filtrování, které metody jsou hlášeny, když jsou nejprve zkompilován JIT Kompilátorem. Můžete určit, že všechny metody oznámený tak, že nastavíte hodnotu atributu název \*.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
