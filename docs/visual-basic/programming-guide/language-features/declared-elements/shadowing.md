---
title: Stínování
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 7d76e2e7398c2f954ff4274f77ffa350efbd3617
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410744"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="86537-102">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86537-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="86537-103">Pokud dva programovací prvky mají stejný název, jeden z nich může skrýt nebo *stín*, druhý.</span><span class="sxs-lookup"><span data-stu-id="86537-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="86537-104">V takové situaci není pro referenci k dispozici stínovaný element; místo toho, když kód používá název elementu, kompilátor Visual Basic ho přeloží na stínový element.</span><span class="sxs-lookup"><span data-stu-id="86537-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="86537-105">Účel</span><span class="sxs-lookup"><span data-stu-id="86537-105">Purpose</span></span>  
 <span data-ttu-id="86537-106">Hlavním účelem stínování je chránit definici členů vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="86537-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="86537-107">Základní třída se může podrobit změně, která vytvoří element se stejným názvem jako ten, který jste už definovali.</span><span class="sxs-lookup"><span data-stu-id="86537-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="86537-108">Pokud k tomu dojde, `Shadows` Modifikátor vynutí, aby byly odkazy prostřednictvím vaší třídy přeloženy na člen, který jste definovali, místo na nový prvek základní třídy.</span><span class="sxs-lookup"><span data-stu-id="86537-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="86537-109">Typy stínování</span><span class="sxs-lookup"><span data-stu-id="86537-109">Types of Shadowing</span></span>  
 <span data-ttu-id="86537-110">Element může stínovat jiný element dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="86537-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="86537-111">Stínový element lze deklarovat v dílčí oblasti oblasti obsahující stínový element. v takovém případě je vytváření stínů provedeno *prostřednictvím rozsahu*.</span><span class="sxs-lookup"><span data-stu-id="86537-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="86537-112">Nebo odvozená třída může předefinovat člen základní třídy, v takovém případě se stín provádí *prostřednictvím dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="86537-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="86537-113">Stínování přes rozsah</span><span class="sxs-lookup"><span data-stu-id="86537-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="86537-114">Je možné, že programovací prvky ve stejném modulu, třídě nebo struktuře mají stejný název, ale jiný obor.</span><span class="sxs-lookup"><span data-stu-id="86537-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="86537-115">Pokud jsou v tomto způsobu deklarovány dva prvky a kód odkazuje na název, který sdílí, element s úzkým rozsahem stínů ostatních prvků (rozsah bloku je nejužší).</span><span class="sxs-lookup"><span data-stu-id="86537-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="86537-116">Například modul může definovat `Public` proměnnou s názvem `temp` a procedura v rámci modulu může deklarovat také místní proměnnou pojmenovanou `temp` .</span><span class="sxs-lookup"><span data-stu-id="86537-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="86537-117">Odkazy na `temp` z v rámci procedury přistupují k místní proměnné, zatímco odkazy na `temp` z vně procedury přistupují k `Public` proměnné.</span><span class="sxs-lookup"><span data-stu-id="86537-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="86537-118">V tomto případě proměnná procedury `temp` nastínuje proměnnou modulu `temp` .</span><span class="sxs-lookup"><span data-stu-id="86537-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="86537-119">Následující ilustrace znázorňuje dvě proměnné s názvem `temp` .</span><span class="sxs-lookup"><span data-stu-id="86537-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="86537-120">Lokální proměnná `temp` nastínuje členskou proměnnou `temp` při použití z vlastní procedury `p` .</span><span class="sxs-lookup"><span data-stu-id="86537-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="86537-121">`MyClass`Klíčové slovo však obchází stín a přistupuje k členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="86537-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Obrázek, který zobrazuje stínování v rozsahu.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="86537-123">Příklad vytváření stínového rozsahu naleznete v tématu [How to: Hide a proměnná se stejným názvem jako má vaše proměnná](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="86537-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="86537-124">Stínování prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="86537-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="86537-125">Předefinuje-li odvozená třída programový prvek zděděný ze základní třídy, element redefine původní prvek nastínuje.</span><span class="sxs-lookup"><span data-stu-id="86537-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="86537-126">Můžete vytvořit stín libovolného typu deklarovaného prvku nebo sadu přetížených prvků s jakýmkoli jiným typem.</span><span class="sxs-lookup"><span data-stu-id="86537-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="86537-127">Například `Integer` Proměnná může vytvořit stínovou `Function` proceduru.</span><span class="sxs-lookup"><span data-stu-id="86537-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="86537-128">Pokud vytvoříte stínovou proceduru pomocí jiného postupu, můžete použít jiný seznam parametrů a jiný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="86537-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="86537-129">Následující ilustrace znázorňuje základní třídu `b` a odvozenou třídu `d` , která dědí z `b` .</span><span class="sxs-lookup"><span data-stu-id="86537-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="86537-130">Základní třída definuje proceduru s názvem `proc` a odvozenou třídu ji nastínuje jiným postupem stejného názvu.</span><span class="sxs-lookup"><span data-stu-id="86537-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="86537-131">První `Call` příkaz přistupuje k stínování `proc` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="86537-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="86537-132">`MyBase`Klíčové slovo však obchází stín a přistupuje k stínované proceduře v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="86537-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Grafický diagram stínování prostřednictvím dědičnosti](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="86537-134">Příklad stínování prostřednictvím dědičnosti naleznete v tématu [How to: Hide a proměnná se stejným názvem jako má vaše proměnná](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [Postupy: skrytí zděděné proměnné](how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="86537-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="86537-135">Stínová a přístupná úroveň</span><span class="sxs-lookup"><span data-stu-id="86537-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="86537-136">Element Shadow není vždy přístupný z kódu pomocí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="86537-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="86537-137">Může být například deklarována `Private` .</span><span class="sxs-lookup"><span data-stu-id="86537-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="86537-138">V takovém případě je stínový postup připraven a kompilátor překládá všechny odkazy na stejný prvek, který by měl být v případě, že se nevytvořila žádná Stínová kopie.</span><span class="sxs-lookup"><span data-stu-id="86537-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="86537-139">Tento prvek je přístupný prvek nejmenším odvozením kroků zpět od stínové třídy.</span><span class="sxs-lookup"><span data-stu-id="86537-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="86537-140">Pokud je stínovaný element procedurou, je rozlišením nejbližší dostupné verze se stejným názvem, seznamem parametrů a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="86537-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="86537-141">Následující příklad ukazuje hierarchii dědičnosti tří tříd.</span><span class="sxs-lookup"><span data-stu-id="86537-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="86537-142">Každá třída definuje `Sub` proceduru `display` a jednotlivé odvozené třídy stínují `display` proceduru v její základní třídě.</span><span class="sxs-lookup"><span data-stu-id="86537-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="86537-143">V předchozím příkladu se odvozené třídy `secondClass` stínují `display` pomocí `Private` procedury.</span><span class="sxs-lookup"><span data-stu-id="86537-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="86537-144">Při `callDisplay` volání modulu `display` v `secondClass` rozhraní je volající kód mimo `secondClass` a proto nemůže přistupovat k privátní `display` proceduře.</span><span class="sxs-lookup"><span data-stu-id="86537-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="86537-145">Nastínování je připraveno a kompilátor vyřeší odkaz na základní třídu `display` .</span><span class="sxs-lookup"><span data-stu-id="86537-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="86537-146">Další odvozená třída však `thirdClass` deklaruje `display` jako `Public` , takže kód v v `callDisplay` k němu má přístup.</span><span class="sxs-lookup"><span data-stu-id="86537-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="86537-147">Stínování a přepsání</span><span class="sxs-lookup"><span data-stu-id="86537-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="86537-148">Nezaměňujte stíny s přepsáním.</span><span class="sxs-lookup"><span data-stu-id="86537-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="86537-149">Obě jsou použity, když odvozená třída dědí ze základní třídy a obě předefinování jednoho deklarovaného elementu s jiným.</span><span class="sxs-lookup"><span data-stu-id="86537-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="86537-150">Existují však významné rozdíly mezi těmito dvěma.</span><span class="sxs-lookup"><span data-stu-id="86537-150">But there are significant differences between the two.</span></span> <span data-ttu-id="86537-151">Porovnání najdete v tématu [rozdíly mezi stínováním a přepsáním](differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="86537-151">For a comparison, see [Differences Between Shadowing and Overriding](differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="86537-152">Nastínování a přetížení</span><span class="sxs-lookup"><span data-stu-id="86537-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="86537-153">Pokud vytvoříte stín stejného prvku základní třídy s více než jedním prvkem v odvozené třídě, stínové prvky se stanou přetíženými verzemi tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="86537-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="86537-154">Další informace najdete v tématu [přetížení procedury](../procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="86537-154">For more information, see [Procedure Overloading](../procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="86537-155">Přístup k Stínovanému elementu</span><span class="sxs-lookup"><span data-stu-id="86537-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="86537-156">Při přístupu k elementu z odvozené třídy to obvykle provedete prostřednictvím aktuální instance této odvozené třídy – kvalifikováním názvu elementu pomocí `Me` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="86537-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="86537-157">Pokud je vaše odvozená třída stínem elementu v základní třídě, můžete přistupovat k elementu základní třídy tím, že ho zařadíte pomocí `MyBase` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="86537-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="86537-158">Příklad přístupu ke stínovým elementům naleznete v tématu [How to: Access a Hidden a Derived by odvozené třídy](how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="86537-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="86537-159">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="86537-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="86537-160">Způsob, jakým vytvoříte proměnnou objektu, může také ovlivnit, zda odvozená třída přistupuje ke stínovým elementům nebo k stínovanému elementu.</span><span class="sxs-lookup"><span data-stu-id="86537-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="86537-161">Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třída a druhý jako odvozená třída.</span><span class="sxs-lookup"><span data-stu-id="86537-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="86537-162">V předchozím příkladu `basObj` je proměnná deklarována jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="86537-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="86537-163">Přiřazení `dervCls` objektu k němu představuje rozšiřující převod, a proto je platný.</span><span class="sxs-lookup"><span data-stu-id="86537-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="86537-164">Základní třída však nemá přístup k stínové verzi proměnné `z` v odvozené třídě, takže kompilátor překládá `basObj.z` na původní hodnotu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="86537-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86537-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="86537-165">See also</span></span>

- [<span data-ttu-id="86537-166">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="86537-166">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="86537-167">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86537-167">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="86537-168">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="86537-168">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="86537-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="86537-169">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="86537-170">Přepsání</span><span class="sxs-lookup"><span data-stu-id="86537-170">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="86537-171">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="86537-171">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="86537-172">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="86537-172">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
