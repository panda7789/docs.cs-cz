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
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="204cc-102">CS3024 upozornění kompilátoru</span><span class="sxs-lookup"><span data-stu-id="204cc-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="204cc-103">Typ omezení 'type' není kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="204cc-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="204cc-104">Kompilátor toto upozornění vydá, protože použití typu bez-kompatibilní se Specifikací CLS jako omezení obecného typu může znemožnit pro kód napsaný v některých jazycích využívat obecná třída.</span><span class="sxs-lookup"><span data-stu-id="204cc-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="204cc-105">Chcete-li odstranit toto upozornění</span><span class="sxs-lookup"><span data-stu-id="204cc-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="204cc-106">Kompatibilní se Specifikací CLS typ použijte pro omezení typu.</span><span class="sxs-lookup"><span data-stu-id="204cc-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="204cc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="204cc-107">Example</span></span>  
 <span data-ttu-id="204cc-108">Následující příklad generuje CS3024 v několika umístěních:</span><span class="sxs-lookup"><span data-stu-id="204cc-108">The following example generates CS3024 in several locations:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="204cc-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="204cc-109">See Also</span></span>

- [<span data-ttu-id="204cc-110">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="204cc-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
