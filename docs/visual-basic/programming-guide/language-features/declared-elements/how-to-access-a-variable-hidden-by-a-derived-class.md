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
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832174"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="498df-102">Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498df-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="498df-103">Když kód v odvozené třídě získá přístup k proměnné, obvykle přeloží kompilátor odkaz na nejbližší dostupné verzi, to znamená, že dostupné verze nejmíň derivational kroky zpětně ze třídy přístup.</span><span class="sxs-lookup"><span data-stu-id="498df-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="498df-104">Pokud je proměnná definovaná v odvozené třídě, kód obvykle přistupuje k tuto definici.</span><span class="sxs-lookup"><span data-stu-id="498df-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="498df-105">Pokud proměnná odvozené třídy zastiňuje proměnná v základní třídě, skryje verze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="498df-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="498df-106">Však může přistupovat k proměnné základní třídy s kvalifikaci `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="498df-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="498df-107">Pro přístup k základní třídě proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="498df-107">To access a base class variable hidden by a derived class</span></span>  
  
-   <span data-ttu-id="498df-108">Ve výrazu nebo příkazu přiřazení, zadejte před název proměnné `MyBase` – klíčové slovo a tečku (`.`).</span><span class="sxs-lookup"><span data-stu-id="498df-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="498df-109">Přeloží kompilátor odkaz na verzi základní třídy proměnné.</span><span class="sxs-lookup"><span data-stu-id="498df-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="498df-110">Následující příklad ukazuje stínový provoz prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="498df-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="498df-111">Umožňuje dva odkazy, ten, který přistupuje k stínového provozu proměnné a ten, který obchází stínováním.</span><span class="sxs-lookup"><span data-stu-id="498df-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="498df-112">Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a stíní v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="498df-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="498df-113">Postup `showStrings` v odvozené třídě Zobrazí verzi stínového provozu řetězce při název `shadowString` není kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="498df-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="498df-114">Potom zobrazí stínovaný verze při `shadowString` je kvalifikována `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="498df-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="498df-115">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="498df-115">Robust Programming</span></span>  
 <span data-ttu-id="498df-116">Chcete-li snížit riziko odkazující na stínové proměnné a nežádoucí verzi, plně kvalifikovat všechny odkazy na stínové proměnné.</span><span class="sxs-lookup"><span data-stu-id="498df-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="498df-117">Stínový provoz přináší více než jedna verze proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="498df-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="498df-118">Když příkaz kódu odkazuje na název proměnné, verze, na který přeloží kompilátor odkaz na závisí na faktorech, jako je například umístění příkaz kódu a přítomnost oprávněným řetězec.</span><span class="sxs-lookup"><span data-stu-id="498df-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="498df-119">To může zvýšit riziko odkazující na nesprávnou verzi proměnné.</span><span class="sxs-lookup"><span data-stu-id="498df-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498df-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="498df-120">See also</span></span>

- [<span data-ttu-id="498df-121">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="498df-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="498df-122">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="498df-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="498df-123">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="498df-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="498df-124">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná</span><span class="sxs-lookup"><span data-stu-id="498df-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="498df-125">Postupy: Skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="498df-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="498df-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="498df-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="498df-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="498df-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="498df-128">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="498df-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="498df-129">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="498df-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
