---
title: CS3024 upozornění kompilátoru
ms.date: 07/20/2015
f1_keywords:
- CS3024
helpviewer_keywords:
- CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
ms.openlocfilehash: 5d8781117b80dbebe6a01488b8bd66feb12d3e3c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510200"
---
# <a name="compiler-warning-cs3024"></a>CS3024 upozornění kompilátoru
Typ omezení 'type' není kompatibilní se Specifikací CLS.  
  
 Kompilátor toto upozornění vydá, protože použití typu bez-kompatibilní se Specifikací CLS jako omezení obecného typu může znemožnit pro kód napsaný v některých jazycích využívat obecná třída.  
  
### <a name="to-eliminate-this-warning"></a>Chcete-li odstranit toto upozornění  
  
1.  Kompatibilní se Specifikací CLS typ použijte pro omezení typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje CS3024 v několika umístěních:  
  
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

- [Omezení parametrů typů](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
