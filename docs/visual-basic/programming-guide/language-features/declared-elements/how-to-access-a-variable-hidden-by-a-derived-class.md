---
title: 'Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 8dd59dff5b8123331237db905432bbb4e94d62ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648044"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="fa86f-102">Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa86f-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="fa86f-103">Když kód v odvozené třídě získá přístup k proměnné, kompilátor normálně přeloží odkaz na nejbližší dostupné verze, který je přístupný verze nejmenšího derivational kroky zpětné z přístupu k třídě.</span><span class="sxs-lookup"><span data-stu-id="fa86f-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="fa86f-104">Pokud je proměnná definovaná v odvozené třídě, kód normálně přistupuje k této definici.</span><span class="sxs-lookup"><span data-stu-id="fa86f-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="fa86f-105">Pokud proměnná odvozené třídy shadows proměnné v základní třídě, skryje verze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fa86f-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="fa86f-106">Ale mají přístup k proměnné základní třída kvalifikováním její `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fa86f-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="fa86f-107">Pro přístup k základní třída proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="fa86f-107">To access a base class variable hidden by a derived class</span></span>  
  
-   <span data-ttu-id="fa86f-108">Ve výrazu nebo příkazu přiřazení, zadejte před název proměnné `MyBase` – klíčové slovo a období (`.`).</span><span class="sxs-lookup"><span data-stu-id="fa86f-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="fa86f-109">Kompilátor vyřeší odkaz na základní třída verzi proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fa86f-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="fa86f-110">Následující příklad ilustruje, stínový provoz prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="fa86f-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="fa86f-111">Umožňuje dva odkazy, ten, který přistupuje k proměnnou stínového provozu a ten, který obchází stínový provoz.</span><span class="sxs-lookup"><span data-stu-id="fa86f-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="fa86f-112">V předchozím příkladu deklaruje proměnnou `shadowString` v základní třídě a stín v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fa86f-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="fa86f-113">Postup `showStrings` v odvozené třídě zobrazí stínového provozu verzi řetězec při název `shadowString` není kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="fa86f-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="fa86f-114">Potom zobrazí stíněné verze při `shadowString` je kvalifikovaný s `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="fa86f-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fa86f-115">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="fa86f-115">Robust Programming</span></span>  
 <span data-ttu-id="fa86f-116">Chcete-li snížit riziko odkazující na nezamýšleným verzi stíněné proměnné, můžete plnému určení všechny odkazy na proměnnou stíněné.</span><span class="sxs-lookup"><span data-stu-id="fa86f-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="fa86f-117">Stínový provoz zavádí více než jedna verze proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="fa86f-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="fa86f-118">Pokud příkaz kódu odkazuje na název proměnné, verze, do které kompilátor vyřeší odkaz závisí na faktorech, jako je například umístění příkaz kódu a přítomnost opravňující řetězec.</span><span class="sxs-lookup"><span data-stu-id="fa86f-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="fa86f-119">To může zvýšit riziko napadení odkazuje na nesprávné verze proměnné.</span><span class="sxs-lookup"><span data-stu-id="fa86f-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa86f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa86f-120">See Also</span></span>  
 [<span data-ttu-id="fa86f-121">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="fa86f-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="fa86f-122">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa86f-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="fa86f-123">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="fa86f-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="fa86f-124">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná</span><span class="sxs-lookup"><span data-stu-id="fa86f-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="fa86f-125">Postupy: Skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="fa86f-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="fa86f-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="fa86f-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="fa86f-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="fa86f-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="fa86f-128">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="fa86f-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="fa86f-129">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="fa86f-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
