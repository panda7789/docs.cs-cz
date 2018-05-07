---
title: CS3024 upozornění kompilátoru
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: c4c2f915d6172e3c30fc32c5c57fe9921c3f915d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-cs3024"></a>CS3024 upozornění kompilátoru
Omezení typu "typ" není kompatibilní se specifikací CLS.  
  
 Kompilátor vydává toto upozornění, protože použití jiných kompatibilní se specifikací CLS typu jako omezení obecného typu může způsobit, že znemožňuje, aby kód napsaný v některých jazycích využívat obecná třída.  
  
### <a name="to-eliminate-this-warning"></a>Chcete-li eliminovat toto upozornění  
  
1.  Kompatibilní se specifikací CLS typ použijte pro omezení typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří CS3024 v několika umístěních:  
  
```csharp  
// cs3024.cs  
// Compile with: /target:library  
 [assembly: System.CLSCompliant(true)]  
  
[type: System.CLSCompliant(false)]  
public class TestClass // CS3024  
{  
    public ushort us;  
}  
[type: System.CLSCompliant(false)]  
public interface ITest // CS3024  
{}  
public interface I<T> where T : TestClass  
{}  
public class TestClass_2<T> where T : ITest  
{}  
public class TestClass_3<T> : I<T> where T : TestClass  
{}  
public class TestClass_4<T> : TestClass_2<T> where T : ITest  
{}  
public class Test  
{  
    public static int Main()  
    {  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Omezení parametrů typů](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
