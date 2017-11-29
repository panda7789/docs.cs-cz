---
title: "CS3024 upozornění kompilátoru"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: CS3024
helpviewer_keywords: CS3024
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ffaf8a8b5c52e793e08ab467621c42ec47b1a29c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-warning-cs3024"></a><span data-ttu-id="27b17-102">CS3024 upozornění kompilátoru</span><span class="sxs-lookup"><span data-stu-id="27b17-102">Compiler Warning CS3024</span></span>
<span data-ttu-id="27b17-103">Omezení typu "typ" není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="27b17-103">Constraint type 'type' is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="27b17-104">Kompilátor vydává toto upozornění, protože použití jiných kompatibilní se specifikací CLS typu jako omezení obecného typu může způsobit, že znemožňuje, aby kód napsaný v některých jazycích využívat obecná třída.</span><span class="sxs-lookup"><span data-stu-id="27b17-104">The compiler issues this warning because the use of a non-CLS-compliant type as a generic type constraint could make it impossible for code written in some languages to consume your generic class.</span></span>  
  
### <a name="to-eliminate-this-warning"></a><span data-ttu-id="27b17-105">Chcete-li eliminovat toto upozornění</span><span class="sxs-lookup"><span data-stu-id="27b17-105">To eliminate this warning</span></span>  
  
1.  <span data-ttu-id="27b17-106">Kompatibilní se specifikací CLS typ použijte pro omezení typu.</span><span class="sxs-lookup"><span data-stu-id="27b17-106">Use a CLS-compliant type for the type constraint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27b17-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="27b17-107">Example</span></span>  
 <span data-ttu-id="27b17-108">Následující příklad vytvoří CS3024 v několika umístěních:</span><span class="sxs-lookup"><span data-stu-id="27b17-108">The following example generates CS3024 in several locations:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="27b17-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="27b17-109">See Also</span></span>  
 [<span data-ttu-id="27b17-110">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="27b17-110">Constraints on Type Parameters</span></span>](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
