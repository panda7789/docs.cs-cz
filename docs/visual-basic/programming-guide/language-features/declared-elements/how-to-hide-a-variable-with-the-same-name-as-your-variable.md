---
title: 'Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)'
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
ms.openlocfilehash: a8a7eda2a636d7f89131d140c82ad4f3c4743211
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826675"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="05dc4-102">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05dc4-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="05dc4-103">Můžete skrýt proměnné tak *stínováním* ho tedy předefinováním proměnnou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="05dc4-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="05dc4-104">Můžete stínové proměnné, které chcete skrýt dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="05dc4-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="05dc4-105">**Stínový provoz prostřednictvím oboru.**</span><span class="sxs-lookup"><span data-stu-id="05dc4-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="05dc4-106">Můžete ho stínové prostřednictvím oboru ve změně deklarace je uvnitř podoblasti oblasti, který obsahuje proměnné, které chcete skrýt.</span><span class="sxs-lookup"><span data-stu-id="05dc4-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="05dc4-107">**Stínový provoz prostřednictvím dědičnosti.**</span><span class="sxs-lookup"><span data-stu-id="05dc4-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="05dc4-108">Pokud chcete skrýt proměnné je definován na úrovni třídy, je můžete stínové ji prostřednictvím dědičnosti ve změně deklarace s [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="05dc4-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="05dc4-109">Dva způsoby, jak skrýt proměnné</span><span class="sxs-lookup"><span data-stu-id="05dc4-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="05dc4-110">Chcete-li skrýt proměnné tak, že stínování prostřednictvím oboru</span><span class="sxs-lookup"><span data-stu-id="05dc4-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="05dc4-111">Určit oblast definující proměnné, které chcete skrýt a určete podoblasti, ve kterém k předefinování se vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="05dc4-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="05dc4-112">Proměnné oblasti</span><span class="sxs-lookup"><span data-stu-id="05dc4-112">Variable's region</span></span>|<span data-ttu-id="05dc4-113">Pro předefinování ho povolený podoblast</span><span class="sxs-lookup"><span data-stu-id="05dc4-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="05dc4-114">Modul</span><span class="sxs-lookup"><span data-stu-id="05dc4-114">Module</span></span>|<span data-ttu-id="05dc4-115">Třídy v rámci modulu</span><span class="sxs-lookup"><span data-stu-id="05dc4-115">A class within the module</span></span>|  
    |<span data-ttu-id="05dc4-116">Třída</span><span class="sxs-lookup"><span data-stu-id="05dc4-116">Class</span></span>|<span data-ttu-id="05dc4-117">Podtřída v rámci třídy</span><span class="sxs-lookup"><span data-stu-id="05dc4-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="05dc4-118">Postup v rámci třídy</span><span class="sxs-lookup"><span data-stu-id="05dc4-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="05dc4-119">Nelze předefinovat postupu proměnnou v bloku, v rámci tohoto postupu, například v `If`... `End If` konstrukce nebo `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="05dc4-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="05dc4-120">Pokud ještě neexistuje, vytvořte podoblasti.</span><span class="sxs-lookup"><span data-stu-id="05dc4-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="05dc4-121">V rámci podoblasti, zápisu [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarování proměnné stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="05dc4-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="05dc4-122">Když kód uvnitř podoblasti odkazuje na název proměnné, přeloží kompilátor odkaz na proměnnou stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="05dc4-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="05dc4-123">Následující příklad ukazuje stínování prostřednictvím oboru, stejně jako odkaz, který obchází stínováním.</span><span class="sxs-lookup"><span data-stu-id="05dc4-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="05dc4-124">Předchozí příklad deklaruje proměnnou `num` na úrovni modulu i na úrovni postup (v postupu `show`).</span><span class="sxs-lookup"><span data-stu-id="05dc4-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="05dc4-125">Lokální proměnná `num` zastiňuje proměnnou úrovni modulu `num` v rámci `show`, takže místní proměnná je nastavená na 2.</span><span class="sxs-lookup"><span data-stu-id="05dc4-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="05dc4-126">Neexistuje však žádný místní proměnnou stínové `num` v `useModuleLevelNum` postup.</span><span class="sxs-lookup"><span data-stu-id="05dc4-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="05dc4-127">Proto `useModuleLevelNum` nastaví hodnotu proměnné úrovni modulu na 1.</span><span class="sxs-lookup"><span data-stu-id="05dc4-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="05dc4-128">`MsgBox` Volat v `show` obchází stínového provozu mechanismus kvalifikaci `num` s názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="05dc4-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="05dc4-129">Proto se zobrazí úrovni modulu proměnnou místo do místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="05dc4-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="05dc4-130">Chcete-li skrýt proměnné tak, že stínování prostřednictvím dědičnosti</span><span class="sxs-lookup"><span data-stu-id="05dc4-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="05dc4-131">Ujistěte se, že proměnné, které chcete skrýt je deklarovaná ve třídě a na úrovni třídy (mimo všechny procedury).</span><span class="sxs-lookup"><span data-stu-id="05dc4-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="05dc4-132">V opačném případě nemůže zastiňovat prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="05dc4-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="05dc4-133">Definujte třídu odvozenou z třídy proměnné, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="05dc4-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="05dc4-134">V odvozených třídách, zápisu `Dim` deklarace proměnné příkazu.</span><span class="sxs-lookup"><span data-stu-id="05dc4-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="05dc4-135">Zahrnout [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="05dc4-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="05dc4-136">Když kód v odvozené třídě odkazuje na název proměnné, přeloží kompilátor odkaz na vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="05dc4-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="05dc4-137">Následující příklad ukazuje stínový provoz prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="05dc4-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="05dc4-138">Umožňuje dva odkazy, ten, který přistupuje k stínového provozu proměnné a ten, který obchází stínováním.</span><span class="sxs-lookup"><span data-stu-id="05dc4-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="05dc4-139">Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a stíní v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="05dc4-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="05dc4-140">Postup `showStrings` v odvozené třídě Zobrazí verzi stínového provozu řetězce při název `shadowString` není kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="05dc4-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="05dc4-141">Potom zobrazí stínovaný verze při `shadowString` je kvalifikována `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="05dc4-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="05dc4-142">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="05dc4-142">Robust Programming</span></span>  
 <span data-ttu-id="05dc4-143">Stínový provoz přináší více než jedna verze proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="05dc4-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="05dc4-144">Když příkaz kódu odkazuje na název proměnné, verze, na který přeloží kompilátor odkaz na závisí na faktorech, jako je například umístění příkaz kódu a přítomnost oprávněným řetězec.</span><span class="sxs-lookup"><span data-stu-id="05dc4-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="05dc4-145">To může zvýšit riziko odkazující na stínové proměnné a nežádoucí verzi.</span><span class="sxs-lookup"><span data-stu-id="05dc4-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="05dc4-146">Plně kvalifikovaný všechny odkazy na stínové proměnné můžete snížit rizika.</span><span class="sxs-lookup"><span data-stu-id="05dc4-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05dc4-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05dc4-147">See also</span></span>

- [<span data-ttu-id="05dc4-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="05dc4-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="05dc4-149">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05dc4-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="05dc4-150">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="05dc4-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="05dc4-151">Postupy: Skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="05dc4-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="05dc4-152">Postupy: Přístup k proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="05dc4-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="05dc4-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="05dc4-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="05dc4-154">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="05dc4-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="05dc4-155">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="05dc4-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
