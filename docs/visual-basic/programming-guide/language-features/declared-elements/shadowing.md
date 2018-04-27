---
title: Stínění v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 489e1786b08085f229f66b2dbc434b96b06d86df
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="943d3-102">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="943d3-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="943d3-103">Když dva programovací elementy sdílet stejný název, jednu z nich můžete skrýt, nebo *stínové*, jiný.</span><span class="sxs-lookup"><span data-stu-id="943d3-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="943d3-104">V takové situaci stíněné element není k dispozici pro referenci; Místo toho že pokud váš kód používá název elementu, Visual Basic – kompilátor ho přeloží na stínového provozu elementu.</span><span class="sxs-lookup"><span data-stu-id="943d3-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="943d3-105">Účel</span><span class="sxs-lookup"><span data-stu-id="943d3-105">Purpose</span></span>  
 <span data-ttu-id="943d3-106">Hlavním účelem stínový provoz je k ochraně definici členy vaší třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="943d3-107">Základní třída může podstoupit změnu, která vytvoří element se stejným názvem jako jeden, který je již definován.</span><span class="sxs-lookup"><span data-stu-id="943d3-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="943d3-108">V takovém případě `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy přeloží na člen definované, místo do nového elementu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="943d3-109">Typy stínováním</span><span class="sxs-lookup"><span data-stu-id="943d3-109">Types of Shadowing</span></span>  
 <span data-ttu-id="943d3-110">Element můžete stínové jiný element dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="943d3-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="943d3-111">Element stínového provozu může být deklarována uvnitř podoblasti oblasti obsahující stíněné elementu, ve kterém se provádí stínový provoz – případ *prostřednictvím oboru*.</span><span class="sxs-lookup"><span data-stu-id="943d3-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="943d3-112">Nebo odvozující třídě lze znovu definovat členem základní třídu, ve kterém se provádí stínový provoz – případ *prostřednictvím dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="943d3-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="943d3-113">Stínový provoz prostřednictvím oboru</span><span class="sxs-lookup"><span data-stu-id="943d3-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="943d3-114">Je možné pro programování elementů ve stejném modulu, třídu nebo strukturu, do mají stejný název, ale jiný rozsah.</span><span class="sxs-lookup"><span data-stu-id="943d3-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="943d3-115">Pokud jsou dva elementy deklarované tímto způsobem a kód odkazuje na název sdílejí, element s oboru užší shadows jiného elementu (je nejbližší rozsah bloku).</span><span class="sxs-lookup"><span data-stu-id="943d3-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="943d3-116">Například můžete definovat modul `Public` proměnné s názvem `temp`, a postupu v modulu můžou deklarovat místní proměnné také s názvem `temp`.</span><span class="sxs-lookup"><span data-stu-id="943d3-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="943d3-117">Odkazuje na `temp` uvnitř postup přístup k místní proměnné, při odkazy na `temp` z mimo přístup procedur `Public` proměnné.</span><span class="sxs-lookup"><span data-stu-id="943d3-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="943d3-118">V tomto případě proměnnou postup `temp` shadows proměnnou modulu `temp`.</span><span class="sxs-lookup"><span data-stu-id="943d3-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="943d3-119">Následující obrázek znázorňuje dvě proměnné, jak s názvem `temp`.</span><span class="sxs-lookup"><span data-stu-id="943d3-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="943d3-120">Místní proměnná `temp` shadows členské proměnné `temp` přistupováno z v rámci vlastní procedury `p`.</span><span class="sxs-lookup"><span data-stu-id="943d3-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="943d3-121">Ale `MyClass` – klíčové slovo stínový provoz obchází a přistupuje k členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="943d3-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 <span data-ttu-id="943d3-122">![Grafický diagram stínování prostřednictvím oboru](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span><span class="sxs-lookup"><span data-stu-id="943d3-122">![Graphic diagram of shadowing through scope](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")</span></span>  
<span data-ttu-id="943d3-123">Stínový provoz prostřednictvím oboru</span><span class="sxs-lookup"><span data-stu-id="943d3-123">Shadowing through scope</span></span>  
  
 <span data-ttu-id="943d3-124">Příklad stínování prostřednictvím rozsahu, naleznete v části [postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="943d3-124">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="943d3-125">Stínový provoz prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="943d3-125">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="943d3-126">Pokud odvozené třídy znovu definuje programovací element zděděn ze základní třídy, stín redefining element původní elementu.</span><span class="sxs-lookup"><span data-stu-id="943d3-126">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="943d3-127">Žádný druh deklarovaný element nebo sadu přetížené elementů můžete stínové s žádným jiným typem.</span><span class="sxs-lookup"><span data-stu-id="943d3-127">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="943d3-128">Například `Integer` můžete stínové proměnné `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="943d3-128">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="943d3-129">Pokud jste stínové procedury s jinou proceduru, můžete seznam různých parametrů a jiné návratový typ.</span><span class="sxs-lookup"><span data-stu-id="943d3-129">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="943d3-130">Následující obrázek ukazuje základní třídu `b` a odvozená třída `d` který dědí z `b`.</span><span class="sxs-lookup"><span data-stu-id="943d3-130">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="943d3-131">Definuje základní třídu s názvem procedury `proc`, a odvozené třídy jej shadows s jinou proceduru se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="943d3-131">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="943d3-132">První `Call` příkaz přistupuje stínováním `proc` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="943d3-132">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="943d3-133">Ale `MyBase` – klíčové slovo stínový provoz obchází a přistupuje k procesu stíněné v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="943d3-133">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 <span data-ttu-id="943d3-134">![Grafický diagram stínování prostřednictvím dědičnosti](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span><span class="sxs-lookup"><span data-stu-id="943d3-134">![Graphic diagram of shadowing through inheritance](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")</span></span>  
<span data-ttu-id="943d3-135">Stínový provoz prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="943d3-135">Shadowing through inheritance</span></span>  
  
 <span data-ttu-id="943d3-136">Příklad stínování prostřednictvím dědičnosti, naleznete v části [postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [postupy: skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="943d3-136">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="943d3-137">Stínový provoz a úroveň přístupu</span><span class="sxs-lookup"><span data-stu-id="943d3-137">Shadowing and Access Level</span></span>  
 <span data-ttu-id="943d3-138">Element stínového provozu není vždy přístupné z kódu pomocí odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-138">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="943d3-139">Například může deklarovat `Private`.</span><span class="sxs-lookup"><span data-stu-id="943d3-139">For example, it might be declared `Private`.</span></span> <span data-ttu-id="943d3-140">V takovém případě stínový provoz je nepotlačí a kompilátor vyřeší všechny odkazy na stejný element by měla mít pokud by došlo bez stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="943d3-140">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="943d3-141">Tento element je přístupný element nejmenším počtem derivational kroky zpátky ze třídy stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="943d3-141">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="943d3-142">Pokud element stíněné procedury, řešení je na nejbližší dostupný verzi se stejným názvem, seznam parametrů a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="943d3-142">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="943d3-143">Následující příklad ukazuje hierarchie dědičnosti tří tříd.</span><span class="sxs-lookup"><span data-stu-id="943d3-143">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="943d3-144">Každá třída definuje `Sub` postup `display`, a všechny odvozené třídy stínů `display` postup v její základní třída.</span><span class="sxs-lookup"><span data-stu-id="943d3-144">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
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
  
 <span data-ttu-id="943d3-145">V předchozím příkladu, odvozené třídy `secondClass` stínů `display` s `Private` postupu.</span><span class="sxs-lookup"><span data-stu-id="943d3-145">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="943d3-146">Pokud modul `callDisplay` volání `display` v `secondClass`, volající kód je mimo `secondClass` a proto nemá přístup k privátní `display` postupu.</span><span class="sxs-lookup"><span data-stu-id="943d3-146">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="943d3-147">Stínový provoz je nepotlačí a kompilátor přeloží odkaz na základní třídu `display` postupu.</span><span class="sxs-lookup"><span data-stu-id="943d3-147">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="943d3-148">Další však odvozené třídy `thirdClass` deklaruje `display` jako `Public`, takže kód v `callDisplay` k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="943d3-148">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="943d3-149">Stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="943d3-149">Shadowing and Overriding</span></span>  
 <span data-ttu-id="943d3-150">Nezaměňujte stínový provoz s přepsání.</span><span class="sxs-lookup"><span data-stu-id="943d3-150">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="943d3-151">Jak se používají při odvozené třídy dědí vlastnosti ze základní třídy a obě znovu definovat jeden deklarovaný element s jinou.</span><span class="sxs-lookup"><span data-stu-id="943d3-151">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="943d3-152">Ale existují významné rozdíly mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="943d3-152">But there are significant differences between the two.</span></span> <span data-ttu-id="943d3-153">Porovnání najdete v tématu [rozdíly mezi stínováním a přepíše](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="943d3-153">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="943d3-154">Stínový provoz a přetížení</span><span class="sxs-lookup"><span data-stu-id="943d3-154">Shadowing and Overloading</span></span>  
 <span data-ttu-id="943d3-155">Pokud jste v odvozené třídě stínové stejnou základní třídu element s více než jeden element, stanou se stínového provozu elementy přetížené verzích tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="943d3-155">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="943d3-156">Další informace najdete v tématu [přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="943d3-156">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="943d3-157">Přístup k stíněné Element</span><span class="sxs-lookup"><span data-stu-id="943d3-157">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="943d3-158">Při přístupu k elementu z odvozené třídy, je obvykle k tomu prostřednictvím aktuální instancí třídy odvozené třídy, kvalifikující název elementu s `Me` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="943d3-158">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="943d3-159">Pokud odvozené třídy shadows element v základní třídě, dostanete prvku základní třídy kvalifikováním její `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="943d3-159">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="943d3-160">Příklad přístup k prvku stíněné, naleznete v části [postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="943d3-160">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="943d3-161">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="943d3-161">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="943d3-162">Jak vytvořit proměnné objektu může ovlivnit také zda stínového provozu element nebo element stíněné přistupuje k odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-162">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="943d3-163">Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třídy a další jako odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-163">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
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
  
 <span data-ttu-id="943d3-164">V předchozím příkladu, proměnná `basObj` je deklarován jako základní třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-164">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="943d3-165">Přiřazení `dervCls` objektu k němu rozšiřující převod se považuje za a je proto platný.</span><span class="sxs-lookup"><span data-stu-id="943d3-165">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="943d3-166">Základní třída však nelze přístup stínového provozu verzi proměnnou `z` v odvozené třídě, takže kompilátor přeloží `basObj.z` na původní hodnotu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="943d3-166">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943d3-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="943d3-167">See Also</span></span>  
 [<span data-ttu-id="943d3-168">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="943d3-168">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="943d3-169">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="943d3-169">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="943d3-170">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="943d3-170">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="943d3-171">Shadows</span><span class="sxs-lookup"><span data-stu-id="943d3-171">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="943d3-172">Overrides</span><span class="sxs-lookup"><span data-stu-id="943d3-172">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="943d3-173">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="943d3-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="943d3-174">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="943d3-174">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
