---
title: Rozpoznání přetížené nelze použít pro &#39; &lt;procedurename&gt; &#39; protože přistupující instance je typ rozhraní
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: e41cbf30f06547ef39553e31542e4e8b6df49a3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589877"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="04578-102">Rozpoznání přetížené nelze použít pro &#39; &lt;procedurename&gt; &#39; protože přistupující instance je typ rozhraní</span><span class="sxs-lookup"><span data-stu-id="04578-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="04578-103">Kompilátor se pokouší vyřešit odkaz na vlastnost přetížené nebo postup, ale odkaz nezdaří, protože argument je typu `Object` a odkazující objekt má datový typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="04578-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="04578-104">`Object` Způsobí, že kompilátoru vyřešit jako pozdní vazbou odkaz.</span><span class="sxs-lookup"><span data-stu-id="04578-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="04578-105">Za těchto okolností přeloží kompilátor přetížení prostřednictvím implementující třídu místo prostřednictvím základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="04578-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="04578-106">Pokud třída přejmenuje jednu z verzí přetížené, kompilátor nebere v úvahu této verze být přetížení, protože se její název liší.</span><span class="sxs-lookup"><span data-stu-id="04578-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="04578-107">To způsobí, že kompilátoru ignorovat přejmenovat verze při by mohlo být nejvhodnější odkaz na řešení.</span><span class="sxs-lookup"><span data-stu-id="04578-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="04578-108">**ID chyby:** BC30933</span><span class="sxs-lookup"><span data-stu-id="04578-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04578-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="04578-109">To correct this error</span></span>  
  
-   <span data-ttu-id="04578-110">Použití `CType` přetypovat argument z `Object` na typ určený podpis přetížení, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="04578-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="04578-111">Všimněte si, že nepomůže přetypovat odkazující objekt, který má základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="04578-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="04578-112">Argumentem této chybě zabráníte tak musíte vysílat.</span><span class="sxs-lookup"><span data-stu-id="04578-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04578-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="04578-113">Example</span></span>  
 <span data-ttu-id="04578-114">Následující příklad ukazuje volání přetížené `Sub` procedury, která způsobí, že tato chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="04578-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
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
  
 <span data-ttu-id="04578-115">V předchozím příkladu, pokud je povoleno volání do kompilátoru `s1` jako zapsána, řešení by proběhnout prostřednictvím třídy `c1` místo rozhraní `i1`.</span><span class="sxs-lookup"><span data-stu-id="04578-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="04578-116">To znamená, když nebude zvážit kompilátor `s2` protože se její název liší v `c1`, i když je nejvhodnější podle definice `i1`.</span><span class="sxs-lookup"><span data-stu-id="04578-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="04578-117">Chybu můžete vyřešit změnou volání na jednu z následujících řádků kódu:</span><span class="sxs-lookup"><span data-stu-id="04578-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="04578-118">Každý předchozí řádek kódu explicitně vrhá `Object` proměnná `o1` na jeden z typů parametrů definovaný pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="04578-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04578-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="04578-119">See Also</span></span>  
 [<span data-ttu-id="04578-120">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="04578-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="04578-121">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="04578-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [<span data-ttu-id="04578-122">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="04578-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
