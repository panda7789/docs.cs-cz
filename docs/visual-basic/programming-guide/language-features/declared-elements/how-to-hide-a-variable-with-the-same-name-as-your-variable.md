---
title: "Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af031f3ef134b2a509922e6ada28aa5b2b80d641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="c922e-102">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c922e-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="c922e-103">Můžete skrýt proměnné podle *stínový provoz* ho, který je ve předefinování s proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="c922e-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="c922e-104">Můžete stínové proměnnou, kterou chcete skrýt dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="c922e-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="c922e-105">**Stínový provoz prostřednictvím oboru.**</span><span class="sxs-lookup"><span data-stu-id="c922e-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="c922e-106">Můžete ho stínové prostřednictvím oboru podle redeclaring uvnitř podoblasti oblasti obsahující proměnnou, kterou chcete skrýt.</span><span class="sxs-lookup"><span data-stu-id="c922e-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="c922e-107">**Stínový provoz prostřednictvím dědičnosti.**</span><span class="sxs-lookup"><span data-stu-id="c922e-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="c922e-108">Pokud chcete skrýt proměnné definovanou na úrovni třídy, vám může stínové ji prostřednictvím dědičnosti podle její redeclaring [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="c922e-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="c922e-109">Dva způsoby, jak skrýt proměnné</span><span class="sxs-lookup"><span data-stu-id="c922e-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="c922e-110">Chcete-li skrýt proměnné tak, že stínování prostřednictvím rozsahu</span><span class="sxs-lookup"><span data-stu-id="c922e-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="c922e-111">Určit oblasti definování proměnné, které chcete skrýt a určit podoblasti, ve kterém znovu definovat s vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="c922e-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="c922e-112">Oblast proměnné</span><span class="sxs-lookup"><span data-stu-id="c922e-112">Variable's region</span></span>|<span data-ttu-id="c922e-113">Povolená podoblasti pro jeho opětovná definice</span><span class="sxs-lookup"><span data-stu-id="c922e-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="c922e-114">Modul</span><span class="sxs-lookup"><span data-stu-id="c922e-114">Module</span></span>|<span data-ttu-id="c922e-115">Třídu v rámci modulu</span><span class="sxs-lookup"><span data-stu-id="c922e-115">A class within the module</span></span>|  
    |<span data-ttu-id="c922e-116">Třída</span><span class="sxs-lookup"><span data-stu-id="c922e-116">Class</span></span>|<span data-ttu-id="c922e-117">Podtřídy v rámci třídy</span><span class="sxs-lookup"><span data-stu-id="c922e-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="c922e-118">Postup v rámci třídy</span><span class="sxs-lookup"><span data-stu-id="c922e-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="c922e-119">Nelze upravit postup proměnné v bloku v rámci tohoto postupu, například v `If`... `End If` konstrukce nebo `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="c922e-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="c922e-120">Pokud ještě neexistuje, vytvořte podoblasti.</span><span class="sxs-lookup"><span data-stu-id="c922e-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="c922e-121">V rámci podoblasti, zápisu [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarace proměnnou stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="c922e-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="c922e-122">Pokud kód podoblasti odkazuje na název proměnné, kompilátor vyřeší odkaz na proměnnou stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="c922e-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="c922e-123">Následující příklad ilustruje, stínový provoz prostřednictvím oboru, jakož i odkaz, který obchází stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="c922e-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     <span data-ttu-id="c922e-124">V předchozím příkladu deklaruje proměnnou `num` na úrovni modulu i na úrovni postupu (v postupu `show`).</span><span class="sxs-lookup"><span data-stu-id="c922e-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="c922e-125">Místní proměnná `num` shadows proměnnou úroveň modulu `num` v rámci `show`, takže místní proměnná je nastavená na 2.</span><span class="sxs-lookup"><span data-stu-id="c922e-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="c922e-126">Neexistuje však žádný místní proměnné na stínové `num` v `useModuleLevelNum` postupu.</span><span class="sxs-lookup"><span data-stu-id="c922e-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="c922e-127">Proto `useModuleLevelNum` nastaví hodnotu úroveň modulu proměnné na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="c922e-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="c922e-128">`MsgBox` Volání uvnitř `show` obchází stínového provozu mechanismus kvalifikováním `num` s názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="c922e-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="c922e-129">Proto se zobrazí proměnnou úroveň modulu místo místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="c922e-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="c922e-130">Chcete-li skrýt proměnné tak, že stínování prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="c922e-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="c922e-131">Ujistěte se, že proměnnou, kterou chcete skrýt je deklarovaná ve třídě a na úrovni třídy (mimo jakéhokoli postupu).</span><span class="sxs-lookup"><span data-stu-id="c922e-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="c922e-132">V opačném případě nemůže stínové prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="c922e-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="c922e-133">Definice třídy odvozené od třídy proměnné, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c922e-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="c922e-134">V odvozené třídě, zápisu `Dim` příkaz deklarace vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="c922e-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="c922e-135">Zahrnout [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c922e-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="c922e-136">Když kód v odvozené třídě odkazuje na název proměnné, kompilátor vyřeší odkaz na vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="c922e-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="c922e-137">Následující příklad ilustruje, stínový provoz prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="c922e-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="c922e-138">Umožňuje dva odkazy, ten, který přistupuje k proměnnou stínového provozu a ten, který obchází stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="c922e-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="c922e-139">V předchozím příkladu deklaruje proměnnou `shadowString` v základní třídě a stín v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="c922e-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="c922e-140">Postup `showStrings` v odvozené třídě zobrazí stínového provozu verzi řetězec při název `shadowString` není kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="c922e-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="c922e-141">Potom zobrazí stíněné verze při `shadowString` je kvalifikovaný s `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c922e-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c922e-142">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c922e-142">Robust Programming</span></span>  
 <span data-ttu-id="c922e-143">Stínový provoz zavádí více než jedna verze proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="c922e-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="c922e-144">Pokud příkaz kódu odkazuje na název proměnné, verze, do které kompilátor vyřeší odkaz závisí na faktorech, jako je například umístění příkaz kódu a přítomnost opravňující řetězec.</span><span class="sxs-lookup"><span data-stu-id="c922e-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="c922e-145">To může zvýšit riziko napadení odkazující na nezamýšleným verzi stíněné proměnné.</span><span class="sxs-lookup"><span data-stu-id="c922e-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="c922e-146">Plně kvalifikovaný všechny odkazy na proměnnou stíněné můžete snížit rizika.</span><span class="sxs-lookup"><span data-stu-id="c922e-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c922e-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="c922e-147">See Also</span></span>  
 [<span data-ttu-id="c922e-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="c922e-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="c922e-149">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c922e-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="c922e-150">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="c922e-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="c922e-151">Postupy: skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="c922e-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="c922e-152">Postupy: přístup k proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="c922e-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="c922e-153">Přepsání</span><span class="sxs-lookup"><span data-stu-id="c922e-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="c922e-154">ME, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="c922e-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="c922e-155">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="c922e-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
