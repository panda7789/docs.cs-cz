---
title: Stínění v jazyce Visual Basic
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
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839389"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="82d4c-102">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82d4c-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="82d4c-103">Když dva programovací prvky sdílí se stejným názvem, jeden z nich můžete skrýt, nebo *stínové*, druhou.</span><span class="sxs-lookup"><span data-stu-id="82d4c-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="82d4c-104">V takové situaci stínovaný prvek není k dispozici pro referenci; Místo toho se při váš kód používá název elementu, kompilátor jazyka Visual Basic se přeloží na elementu stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="82d4c-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="82d4c-105">Účel</span><span class="sxs-lookup"><span data-stu-id="82d4c-105">Purpose</span></span>  
 <span data-ttu-id="82d4c-106">Stínový provoz hlavním účelem je chránit definice členů třídy.</span><span class="sxs-lookup"><span data-stu-id="82d4c-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="82d4c-107">Základní třídy může být změnu, která vytvoří element se stejným názvem jako ten, který je již definován.</span><span class="sxs-lookup"><span data-stu-id="82d4c-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="82d4c-108">Pokud k tomu dojde, `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy, které je potřeba vyřešit členovi definované, namísto nový prvek základní třídy.</span><span class="sxs-lookup"><span data-stu-id="82d4c-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="82d4c-109">Typy stínování</span><span class="sxs-lookup"><span data-stu-id="82d4c-109">Types of Shadowing</span></span>  
 <span data-ttu-id="82d4c-110">Element můžete stínové jiný element dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="82d4c-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="82d4c-111">Element stínového provozu mohou být deklarovány uvnitř podoblasti oblasti obsahující stínovaný element, ve kterém se provádí případ, stínováním *prostřednictvím oboru*.</span><span class="sxs-lookup"><span data-stu-id="82d4c-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="82d4c-112">Nebo odvozená třída může předefinovat člena základní třídy, ve kterém se provádí případ, stínováním *prostřednictvím dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="82d4c-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="82d4c-113">Stínový provoz prostřednictvím oboru</span><span class="sxs-lookup"><span data-stu-id="82d4c-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="82d4c-114">Je možné pro vaše programovací prvky ve stejném modulu, třídy nebo struktury mají stejný název, ale jiného oboru.</span><span class="sxs-lookup"><span data-stu-id="82d4c-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="82d4c-115">Když kód odkazuje na název sdílejí tímto způsobem jsou deklarovány dva prvky, element s oborem užší zastiňuje jiného elementu (rozsah bloku je nejbližší).</span><span class="sxs-lookup"><span data-stu-id="82d4c-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="82d4c-116">Například můžete definovat modulu `Public` proměnnou s názvem `temp`, a postup v rámci modulu lze deklarovat lokální proměnná i s názvem `temp`.</span><span class="sxs-lookup"><span data-stu-id="82d4c-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="82d4c-117">Odkazy na `temp` v rámci postupu přístup k místní proměnné při odkazy na `temp` z mimo řízení přístupu `Public` proměnné.</span><span class="sxs-lookup"><span data-stu-id="82d4c-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="82d4c-118">V takovém případě proměnnou postup `temp` zastiňuje proměnná modulu `temp`.</span><span class="sxs-lookup"><span data-stu-id="82d4c-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="82d4c-119">Následující obrázek znázorňuje dvě proměnné, oba s názvem `temp`.</span><span class="sxs-lookup"><span data-stu-id="82d4c-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="82d4c-120">Lokální proměnná `temp` zastiňuje členskou proměnnou `temp` při přístupu z v rámci své vlastní procedury `p`.</span><span class="sxs-lookup"><span data-stu-id="82d4c-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="82d4c-121">Ale `MyClass` – klíčové slovo stínový provoz obchází a přistupuje k členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="82d4c-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Obrázek znázorňující, stínování prostřednictvím oboru.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="82d4c-123">Příklad stínování prostřednictvím oboru, naleznete v tématu [jak: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="82d4c-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="82d4c-124">Stínový provoz prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="82d4c-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="82d4c-125">Pokud odvozené třídy předefinuje programovací element zděděné ze základní třídy, prvku redefining zastiňuje původní elementu.</span><span class="sxs-lookup"><span data-stu-id="82d4c-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="82d4c-126">Jakýkoli element deklarovaný typ nebo sadu přetížených elementů můžete stínové s žádným jiným typem.</span><span class="sxs-lookup"><span data-stu-id="82d4c-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="82d4c-127">Například `Integer` můžete stínové proměnné `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="82d4c-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="82d4c-128">Pokud jste stínové procedury s jinou proceduru, můžete použít seznam různých parametrů a jiným návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="82d4c-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="82d4c-129">Následující obrázek ukazuje základní třídu `b` a odvozená třída `d` , která dědí z `b`.</span><span class="sxs-lookup"><span data-stu-id="82d4c-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="82d4c-130">Základní třída definuje proceduru s názvem `proc`, a odvozená třída zastiňuje ho pomocí jiné proceduře se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="82d4c-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="82d4c-131">První `Call` příkaz přistupuje stínováním `proc` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="82d4c-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="82d4c-132">Ale `MyBase` – klíčové slovo stínový provoz obchází a budou k dispozici stínovaný postup v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="82d4c-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Grafický diagram stínový provoz prostřednictvím dědičnosti](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="82d4c-134">Příklad stínový provoz prostřednictvím dědičnosti, naleznete v tématu [jak: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [jak: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="82d4c-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="82d4c-135">Stínový provoz a úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="82d4c-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="82d4c-136">Element stínového provozu vždy není přístupné z kódu pomocí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="82d4c-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="82d4c-137">Například může být deklarován `Private`.</span><span class="sxs-lookup"><span data-stu-id="82d4c-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="82d4c-138">V takovém případě stínováním není zrušena a přeloží kompilátor všechny odkazy na stejný prvek by měl mít pokud byla žádné stínováním.</span><span class="sxs-lookup"><span data-stu-id="82d4c-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="82d4c-139">Tento prvek je přístupný prvek derivational nejmenším počtem kroků zpět ze třídy stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="82d4c-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="82d4c-140">Postup při stínovaný element řešení je nejbližší dostupné verze se stejným názvem, seznam parametrů a návratový typ.</span><span class="sxs-lookup"><span data-stu-id="82d4c-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="82d4c-141">Následující příklad ukazuje tři třídy hierarchie dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="82d4c-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="82d4c-142">Každá třída definuje `Sub` postup `display`, a každý odvozené třídy stínů `display` postup v její základní třídě.</span><span class="sxs-lookup"><span data-stu-id="82d4c-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```  
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
  
 <span data-ttu-id="82d4c-143">V předchozím příkladu, odvozené třídy `secondClass` stíny `display` s `Private` postup.</span><span class="sxs-lookup"><span data-stu-id="82d4c-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="82d4c-144">Pokud modul `callDisplay` volání `display` v `secondClass`, volající kód je mimo `secondClass` a proto nemůže přistupovat k privátní `display` postup.</span><span class="sxs-lookup"><span data-stu-id="82d4c-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="82d4c-145">Stínový provoz není zrušena a přeloží kompilátor odkaz na základní třídu `display` postup.</span><span class="sxs-lookup"><span data-stu-id="82d4c-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="82d4c-146">Však další odvozené třídy `thirdClass` deklaruje `display` jako `Public`, takže kód v `callDisplay` k němu máte přístup.</span><span class="sxs-lookup"><span data-stu-id="82d4c-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="82d4c-147">Stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="82d4c-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="82d4c-148">Nepleťte si stínový provoz pomocí přepsání.</span><span class="sxs-lookup"><span data-stu-id="82d4c-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="82d4c-149">Jak se používají při odvozená třída dědí ze základní třídy, a obě znovu definovat jeden element deklarovaný s jiným.</span><span class="sxs-lookup"><span data-stu-id="82d4c-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="82d4c-150">Ale existují významné rozdíly mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="82d4c-150">But there are significant differences between the two.</span></span> <span data-ttu-id="82d4c-151">Porovnání najdete v tématu [rozdíly mezi stínováním a přepíše](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="82d4c-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="82d4c-152">Stínový provoz a přetížení</span><span class="sxs-lookup"><span data-stu-id="82d4c-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="82d4c-153">Pokud stínové prvek základní třídy s více než jeden prvek v odvozené třídě, stanou se stínového provozu prvky přetížené verze daného prvku.</span><span class="sxs-lookup"><span data-stu-id="82d4c-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="82d4c-154">Další informace najdete v tématu [přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="82d4c-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="82d4c-155">Přístup k prvku stínovaný</span><span class="sxs-lookup"><span data-stu-id="82d4c-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="82d4c-156">Při přístupu k elementu z odvozené třídy, obvykle tak učiníte prostřednictvím aktuální instanci odvozené třídy, kvalifikaci pomocí názvu elementu `Me` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="82d4c-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="82d4c-157">Pokud odvozené třídy zastiňuje elementu v základní třídě, dostanete základní třída prvku kvalifikaci s `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="82d4c-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="82d4c-158">Příklad přístup k prvku stínovaný, naleznete v tématu [jak: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="82d4c-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="82d4c-159">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="82d4c-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="82d4c-160">Jak vytvořit objektové proměnné může ovlivnit také, zda stínového provozu element nebo element stínovaný přistupuje k odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="82d4c-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="82d4c-161">Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třídu a druhá jako odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="82d4c-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```  
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
  
 <span data-ttu-id="82d4c-162">V předchozím příkladu je proměnná `basObj` je deklarován jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="82d4c-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="82d4c-163">Přiřazení `dervCls` objektu představuje rozšiřující převod a proto je platná.</span><span class="sxs-lookup"><span data-stu-id="82d4c-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="82d4c-164">Však základní třídy nedaří stínového provozu verze proměnné `z` v odvozené třídě, takže přeloží kompilátor `basObj.z` na původní hodnotu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="82d4c-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d4c-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82d4c-165">See also</span></span>

- [<span data-ttu-id="82d4c-166">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="82d4c-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="82d4c-167">Obor v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82d4c-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="82d4c-168">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="82d4c-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="82d4c-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="82d4c-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="82d4c-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="82d4c-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="82d4c-171">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="82d4c-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="82d4c-172">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="82d4c-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
