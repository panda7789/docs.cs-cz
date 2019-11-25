---
title: 'Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná'
ms.date: 07/20/2015
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
ms.openlocfilehash: 0915adbbabb778b1bdd3b6b30e56725a7e74867c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345359"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="7eca4-102">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7eca4-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="7eca4-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span><span class="sxs-lookup"><span data-stu-id="7eca4-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="7eca4-104">You can shadow the variable you want to hide in two ways:</span><span class="sxs-lookup"><span data-stu-id="7eca4-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="7eca4-105">**Shadowing Through Scope.**</span><span class="sxs-lookup"><span data-stu-id="7eca4-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="7eca4-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span><span class="sxs-lookup"><span data-stu-id="7eca4-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="7eca4-107">**Shadowing Through Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="7eca4-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="7eca4-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span><span class="sxs-lookup"><span data-stu-id="7eca4-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="7eca4-109">Two Ways to Hide a Variable</span><span class="sxs-lookup"><span data-stu-id="7eca4-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="7eca4-110">To hide a variable by shadowing it through scope</span><span class="sxs-lookup"><span data-stu-id="7eca4-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="7eca4-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="7eca4-112">Variable's region</span><span class="sxs-lookup"><span data-stu-id="7eca4-112">Variable's region</span></span>|<span data-ttu-id="7eca4-113">Allowable subregion for redefining it</span><span class="sxs-lookup"><span data-stu-id="7eca4-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="7eca4-114">Modul</span><span class="sxs-lookup"><span data-stu-id="7eca4-114">Module</span></span>|<span data-ttu-id="7eca4-115">A class within the module</span><span class="sxs-lookup"><span data-stu-id="7eca4-115">A class within the module</span></span>|
    |<span data-ttu-id="7eca4-116">Třída</span><span class="sxs-lookup"><span data-stu-id="7eca4-116">Class</span></span>|<span data-ttu-id="7eca4-117">A subclass within the class</span><span class="sxs-lookup"><span data-stu-id="7eca4-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="7eca4-118">A procedure within the class</span><span class="sxs-lookup"><span data-stu-id="7eca4-118">A procedure within the class</span></span>|

    <span data-ttu-id="7eca4-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span><span class="sxs-lookup"><span data-stu-id="7eca4-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="7eca4-120">Create the subregion if it does not already exist.</span><span class="sxs-lookup"><span data-stu-id="7eca4-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="7eca4-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="7eca4-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="7eca4-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span><span class="sxs-lookup"><span data-stu-id="7eca4-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="7eca4-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span><span class="sxs-lookup"><span data-stu-id="7eca4-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="7eca4-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span><span class="sxs-lookup"><span data-stu-id="7eca4-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="7eca4-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span><span class="sxs-lookup"><span data-stu-id="7eca4-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="7eca4-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span><span class="sxs-lookup"><span data-stu-id="7eca4-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="7eca4-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span><span class="sxs-lookup"><span data-stu-id="7eca4-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="7eca4-129">Therefore, it displays the module-level variable instead of the local variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="7eca4-130">To hide a variable by shadowing it through inheritance</span><span class="sxs-lookup"><span data-stu-id="7eca4-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="7eca4-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span><span class="sxs-lookup"><span data-stu-id="7eca4-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="7eca4-132">Otherwise you cannot shadow it through inheritance.</span><span class="sxs-lookup"><span data-stu-id="7eca4-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="7eca4-133">Define a class derived from the variable's class if one does not already exist.</span><span class="sxs-lookup"><span data-stu-id="7eca4-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="7eca4-134">Inside the derived class, write a `Dim` statement declaring your variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="7eca4-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span><span class="sxs-lookup"><span data-stu-id="7eca4-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="7eca4-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="7eca4-137">The following example illustrates shadowing through inheritance.</span><span class="sxs-lookup"><span data-stu-id="7eca4-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="7eca4-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span><span class="sxs-lookup"><span data-stu-id="7eca4-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="7eca4-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span><span class="sxs-lookup"><span data-stu-id="7eca4-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="7eca4-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span><span class="sxs-lookup"><span data-stu-id="7eca4-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="7eca4-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span><span class="sxs-lookup"><span data-stu-id="7eca4-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="7eca4-142">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7eca4-142">Robust Programming</span></span>

<span data-ttu-id="7eca4-143">Shadowing introduces more than one version of a variable with the same name.</span><span class="sxs-lookup"><span data-stu-id="7eca4-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="7eca4-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span><span class="sxs-lookup"><span data-stu-id="7eca4-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="7eca4-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="7eca4-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="7eca4-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="7eca4-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eca4-147">See also</span></span>

- [<span data-ttu-id="7eca4-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="7eca4-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="7eca4-149">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7eca4-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="7eca4-150">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="7eca4-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="7eca4-151">Postupy: Skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="7eca4-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="7eca4-152">Postupy: Přístup k proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="7eca4-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="7eca4-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="7eca4-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="7eca4-154">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="7eca4-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="7eca4-155">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7eca4-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
