---
title: Rozpoznání přetížené procedury s pozdní vazbou nelze použít pro '<procedurename>', protože přistupující instance je typu rozhraní.
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 7f2ae3bb0e7c09d966c53fb17b1cbe675dfce8b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814052"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="4fa12-102">Přetížení rozpoznání s pozdní vazbou nelze použít pro '\<název_procedury >' protože přistupující instance je typu rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fa12-102">Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>
<span data-ttu-id="4fa12-103">Kompilátor se pokouší rozpoznat odkaz na přetížená vlastnost nebo procedura, ale odkaz se nezdaří, protože argument je typu `Object` a odkazující objekt má datový typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4fa12-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="4fa12-104">`Object` Argument vynutí, aby kompilátor přeložit odkaz na jako s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="4fa12-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="4fa12-105">Za těchto okolností přeloží kompilátor přetížení prostřednictvím implementující třídu namísto prostřednictvím základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4fa12-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="4fa12-106">Pokud třída přejmenuje některou z přetížených verzí, kompilátor nebere v úvahu tuto verzi si přetížení, protože se její název liší.</span><span class="sxs-lookup"><span data-stu-id="4fa12-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="4fa12-107">To pak způsobí, že kompilátor bude ignorovat přejmenované verze, když ho mohla se přeložit odkaz na správnou volbu.</span><span class="sxs-lookup"><span data-stu-id="4fa12-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="4fa12-108">**ID chyby:** BC30933</span><span class="sxs-lookup"><span data-stu-id="4fa12-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4fa12-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4fa12-109">To correct this error</span></span>  
  
-   <span data-ttu-id="4fa12-110">Použití `CType` přetypovat argument od `Object` na typ určený signatura přetížení, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="4fa12-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="4fa12-111">Mějte na paměti, že to nepomůže objekt přetypujte na odkazující na základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4fa12-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="4fa12-112">Musíte přetypovat argument lze vyvarovat této chyby.</span><span class="sxs-lookup"><span data-stu-id="4fa12-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fa12-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fa12-113">Example</span></span>  
 <span data-ttu-id="4fa12-114">Následující příklad ukazuje volání přetížený `Sub` proceduru, která způsobí, že tuto chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="4fa12-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4fa12-115">V předchozím příkladu, pokud kompilátor může volání `s1` jak je uvedená, řešení by proběhnout prostřednictvím třídy `c1` namísto rozhraní `i1`.</span><span class="sxs-lookup"><span data-stu-id="4fa12-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="4fa12-116">To znamená, že by kompilátor zvažte `s2` vzhledem k tomu, že je její název liší `c1`, i když je správnou volbu podle definice `i1`.</span><span class="sxs-lookup"><span data-stu-id="4fa12-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="4fa12-117">Opravte chybu tak, že změníte volání na buď následující řádky kódu:</span><span class="sxs-lookup"><span data-stu-id="4fa12-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="4fa12-118">Jednotlivé řádky kódu, předchozí explicitní přetypování `Object` proměnnou `o1` na jeden z typů parametrů definovaných pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="4fa12-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa12-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fa12-119">See also</span></span>

- [<span data-ttu-id="4fa12-120">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="4fa12-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="4fa12-121">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="4fa12-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="4fa12-122">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="4fa12-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
