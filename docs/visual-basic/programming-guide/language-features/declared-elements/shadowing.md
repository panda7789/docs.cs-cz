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
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266882"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="6c516-102">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c516-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="6c516-103">Pokud dva programovací prvky sdílejí stejný název, jeden z nich může skrýt nebo *stín*, druhý.</span><span class="sxs-lookup"><span data-stu-id="6c516-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="6c516-104">V takové situaci stínovaný prvek není k dispozici pro referenci; místo toho při kódu používá název prvku, kompilátor jazyka jej přeloží na prvek stínování.</span><span class="sxs-lookup"><span data-stu-id="6c516-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="6c516-105">Účel</span><span class="sxs-lookup"><span data-stu-id="6c516-105">Purpose</span></span>  
 <span data-ttu-id="6c516-106">Hlavním účelem stínových stínových stínů je chránit definici členů třídy.</span><span class="sxs-lookup"><span data-stu-id="6c516-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="6c516-107">Základní třída může podstoupit změnu, která vytvoří prvek se stejným názvem jako ten, který jste již definovali.</span><span class="sxs-lookup"><span data-stu-id="6c516-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="6c516-108">Pokud k tomu `Shadows` dojde, modifikátor vynutí odkazy prostřednictvím třídy, které mají být vyřešeny na člen, který jste definovali, namísto nového elementu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6c516-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="6c516-109">Typy stínových stínových objektů</span><span class="sxs-lookup"><span data-stu-id="6c516-109">Types of Shadowing</span></span>  
 <span data-ttu-id="6c516-110">Prvek může stínovat jiný prvek dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="6c516-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="6c516-111">Prvek stínování lze deklarovat uvnitř podoblasti oblasti obsahující stínový prvek, v takovém případě je stínování provedeno *prostřednictvím oboru*.</span><span class="sxs-lookup"><span data-stu-id="6c516-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="6c516-112">Nebo odvozené třídy můžete předefinovat člen základní třídy, v takovém případě stínový provoz provádí *prostřednictvím dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="6c516-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="6c516-113">Stínový provoz prostřednictvím oboru</span><span class="sxs-lookup"><span data-stu-id="6c516-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="6c516-114">Je možné, že programovací prvky ve stejném modulu, třídy nebo struktury mají stejný název, ale jiný obor.</span><span class="sxs-lookup"><span data-stu-id="6c516-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="6c516-115">Když dva prvky jsou deklarovány tímto způsobem a kód odkazuje na název, který sdílejí, prvek s užší mašle stíny další prvek (blok obor je nejužší).</span><span class="sxs-lookup"><span data-stu-id="6c516-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="6c516-116">Modul může například definovat `Public` proměnnou s názvem `temp`a postup v rámci `temp`modulu může deklarovat místní proměnnou také pojmenovanou .</span><span class="sxs-lookup"><span data-stu-id="6c516-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="6c516-117">Odkazy na `temp` z v rámci postupu přístup k `temp` místní proměnné, zatímco `Public` odkazy na mimo postup přístup proměnné.</span><span class="sxs-lookup"><span data-stu-id="6c516-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="6c516-118">V tomto případě proměnná `temp` procedura `temp`stíny proměnné modulu .</span><span class="sxs-lookup"><span data-stu-id="6c516-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="6c516-119">Následující obrázek znázorňuje dvě `temp`proměnné, obě s názvem .</span><span class="sxs-lookup"><span data-stu-id="6c516-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="6c516-120">Místní proměnná `temp` stíny `temp` členské proměnné při přístupu `p`z vlastní postup .</span><span class="sxs-lookup"><span data-stu-id="6c516-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="6c516-121">`MyClass` Klíčové slovo však obchází stínování a přistupuje k členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="6c516-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Grafika, která zobrazuje stínování v oboru.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="6c516-123">Příklad stínování v oboru najdete v [tématu Jak: Skrýt proměnnou se stejným názvem jako proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="6c516-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="6c516-124">Stínování prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="6c516-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="6c516-125">Pokud odvozená třída předefinuje programovací prvek zděděný ze základní třídy, předefinování element stíny původní prvek.</span><span class="sxs-lookup"><span data-stu-id="6c516-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="6c516-126">Můžete stín ovat libovolný typ deklarovaného prvku nebo sadu přetížených prvků s jiným typem.</span><span class="sxs-lookup"><span data-stu-id="6c516-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="6c516-127">Proměnná `Integer` může například `Function` stínovat proceduru.</span><span class="sxs-lookup"><span data-stu-id="6c516-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="6c516-128">Pokud stín postup s jiným postupem, můžete použít jiný seznam parametrů a jiný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="6c516-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="6c516-129">Následující obrázek znázorňuje základní třídu `b` a odvozenou třídu, `d` která dědí z `b`.</span><span class="sxs-lookup"><span data-stu-id="6c516-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="6c516-130">Základní třída definuje proceduru `proc`s názvem a odvozená třída ji stíní jiným postupem se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="6c516-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="6c516-131">První `Call` příkaz přistupuje k stínování `proc` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="6c516-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="6c516-132">`MyBase` Klíčové slovo však obchází stínování a přistupuje k stínované procedury v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="6c516-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Grafický diagram stínování prostřednictvím dědičnosti](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="6c516-134">Příklad stínování prostřednictvím dědičnosti najdete v [tématu Jak: Skrýt proměnnou se stejným názvem jako proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [Jak skrýt zděděnou proměnnou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="6c516-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="6c516-135">Stínování a úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="6c516-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="6c516-136">Prvek stínování není vždy přístupný z kódu pomocí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="6c516-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="6c516-137">Může být například `Private`deklarována .</span><span class="sxs-lookup"><span data-stu-id="6c516-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="6c516-138">V takovém případě je stínování poraženo a kompilátor vyřeší jakýkoli odkaz na stejný prvek, který by měl, kdyby nedošlo k žádnému stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="6c516-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="6c516-139">Tento prvek je přístupný prvek nejmenší odvozenické kroky zpět od třídy stínování.</span><span class="sxs-lookup"><span data-stu-id="6c516-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="6c516-140">Pokud stínovaný prvek je procedura, rozlišení je nejbližší přístupné verze se stejným názvem, seznam parametrů a návratový typ.</span><span class="sxs-lookup"><span data-stu-id="6c516-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="6c516-141">Následující příklad ukazuje hierarchii dědičnosti tří tříd.</span><span class="sxs-lookup"><span data-stu-id="6c516-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="6c516-142">Každá třída definuje `Sub` `display`proceduru a každá odvozená `display` třída stíny postup v jeho základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6c516-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="6c516-143">V předchozím příkladu jsou odvozené `display` třídy `Private` `secondClass` stíny s procedurou.</span><span class="sxs-lookup"><span data-stu-id="6c516-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="6c516-144">Při `callDisplay` volání `display` `secondClass`modulu je volající `secondClass` kód mimo a `display` proto nemůže získat přístup k privátní procedurě.</span><span class="sxs-lookup"><span data-stu-id="6c516-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="6c516-145">Stínový provoz je poražen a kompilátor řeší odkaz `display` na proceduru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6c516-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="6c516-146">Další odvozené třídy `thirdClass` však deklaruje `display` jako `Public`, takže kód v aplikaci `callDisplay` přístup.</span><span class="sxs-lookup"><span data-stu-id="6c516-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="6c516-147">Stínování a přepsání</span><span class="sxs-lookup"><span data-stu-id="6c516-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="6c516-148">Nezaměňujte stínování s přepsáním.</span><span class="sxs-lookup"><span data-stu-id="6c516-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="6c516-149">Oba se používají, když odvozené třídy dědí ze základní třídy a oba předefinovat jeden deklarovaný prvek s jiným.</span><span class="sxs-lookup"><span data-stu-id="6c516-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="6c516-150">Ale existují významné rozdíly mezi těmito dvěma.</span><span class="sxs-lookup"><span data-stu-id="6c516-150">But there are significant differences between the two.</span></span> <span data-ttu-id="6c516-151">Porovnání naleznete v tématu [Rozdíly mezi stínovým a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="6c516-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="6c516-152">Stínování a přetížení</span><span class="sxs-lookup"><span data-stu-id="6c516-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="6c516-153">Pokud stín stejný element základní třídy s více než jeden prvek v odvozené třídy, stínování prvky stanou přetížené verze tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="6c516-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="6c516-154">Další informace naleznete [v tématu Přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="6c516-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="6c516-155">Přístup k prvku stínového stínu</span><span class="sxs-lookup"><span data-stu-id="6c516-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="6c516-156">Při přístupu k prvku z odvozené třídy, obvykle tak provedete prostřednictvím aktuální instance této `Me` odvozené třídy tím, že kvalifikuje název prvku s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="6c516-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="6c516-157">Pokud vaše odvozené třídy stíny prvek v základní třídě, můžete získat přístup `MyBase` k elementu základní třídy kvalifikující se s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="6c516-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="6c516-158">Příklad přístupu k stínovému prvku naleznete v tématu [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="6c516-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="6c516-159">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="6c516-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="6c516-160">Způsob vytvoření proměnné objektu může také ovlivnit, zda odvozená třída přistupuje k prvku stínování nebo stínovému prvku.</span><span class="sxs-lookup"><span data-stu-id="6c516-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="6c516-161">Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třída a druhý jako odvozená třída.</span><span class="sxs-lookup"><span data-stu-id="6c516-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="6c516-162">V předchozím příkladu je `basObj` proměnná deklarována jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="6c516-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="6c516-163">Přiřazení objektu `dervCls` k němu představuje rozšiřující převod a je proto platný.</span><span class="sxs-lookup"><span data-stu-id="6c516-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="6c516-164">Základní třída však nemůže získat přístup k `z` verzi stínového vysílání proměnné v `basObj.z` odvozené třídě, takže kompilátor se překládá na původní hodnotu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6c516-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c516-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c516-165">See also</span></span>

- [<span data-ttu-id="6c516-166">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="6c516-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="6c516-167">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c516-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="6c516-168">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="6c516-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="6c516-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="6c516-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6c516-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="6c516-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="6c516-171">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="6c516-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="6c516-172">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="6c516-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
