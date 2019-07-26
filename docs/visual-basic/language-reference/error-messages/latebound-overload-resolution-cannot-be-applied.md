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
ms.openlocfilehash: 1fe3c4a29b542302b3615459142a3c565aa8244f
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513028"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="c3990-102">Rozlišení přetěžování lateBound nejde použít pro proceduru instanceName >, protože přistupující instance je typ rozhraní.\<</span><span class="sxs-lookup"><span data-stu-id="c3990-102">Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>

<span data-ttu-id="c3990-103">Kompilátor se pokouší přeložit odkaz na přetíženou vlastnost nebo proceduru, ale odkaz se nezdaří, protože argument je typu `Object` a odkazující objekt má datový typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3990-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="c3990-104">`Object` Argument vynutí, aby kompilátor vyřešil odkaz jako pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="c3990-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>

<span data-ttu-id="c3990-105">Za těchto okolností kompilátor vyřeší přetížení prostřednictvím implementující třídy místo přes základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3990-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="c3990-106">Pokud třída přejmenuje jednu z přetížených verzí, kompilátor nepovažuje tuto verzi za přetížení, protože se její název liší.</span><span class="sxs-lookup"><span data-stu-id="c3990-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="c3990-107">Tím dojde k tomu, že kompilátor ignoruje přejmenovanou verzi, pokud by mohla být správná volba pro vyřešení odkazu.</span><span class="sxs-lookup"><span data-stu-id="c3990-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>

<span data-ttu-id="c3990-108">**ID chyby:** BC30933</span><span class="sxs-lookup"><span data-stu-id="c3990-108">**Error ID:** BC30933</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c3990-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c3990-109">To correct this error</span></span>

- <span data-ttu-id="c3990-110">Použijte `CType` k přetypování argumentu `Object` z na typ určený signaturou přetížení, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="c3990-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>

  <span data-ttu-id="c3990-111">Všimněte si, že neumožňuje přetypovat odkazující objekt na základní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3990-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="c3990-112">Chcete-li se této chybě vyhnout, je nutné přetypovat argument.</span><span class="sxs-lookup"><span data-stu-id="c3990-112">You must cast the argument to avoid this error.</span></span>

## <a name="example"></a><span data-ttu-id="c3990-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3990-113">Example</span></span>

<span data-ttu-id="c3990-114">Následující příklad ukazuje volání `Sub` přetížené procedury, která způsobuje tuto chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c3990-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>

```vb
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

<span data-ttu-id="c3990-115">V předchozím příkladu, pokud kompilátor povolil volání `s1` jako zapsáno, řešení by mělo probíhat prostřednictvím třídy `c1` namísto rozhraní `i1`.</span><span class="sxs-lookup"><span data-stu-id="c3990-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="c3990-116">To by znamenalo, že kompilátor nebere `s2` v `c1`úvahu, že se jedná o jiný název, i když je správná volba definovaná pomocí `i1`.</span><span class="sxs-lookup"><span data-stu-id="c3990-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>

<span data-ttu-id="c3990-117">Chybu můžete opravit tak, že změníte volání na některý z následujících řádků kódu:</span><span class="sxs-lookup"><span data-stu-id="c3990-117">You can correct the error by changing the call to either of the following lines of code:</span></span>

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

<span data-ttu-id="c3990-118">Každý z předchozích řádků kódu explicitně přetypování `Object` proměnnou `o1` na jeden z typů parametrů definovaných pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="c3990-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3990-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3990-119">See also</span></span>

- [<span data-ttu-id="c3990-120">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="c3990-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="c3990-121">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="c3990-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="c3990-122">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="c3990-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
