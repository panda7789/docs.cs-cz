---
title: 'Postupy: Skrytí zděděné proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: 6cf45b12bebc254a0d96516ab262d7aae3d70746
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691252"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="8e121-102">Postupy: Skrytí zděděné proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e121-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="8e121-103">Odvozené třídy dědí všechny definice své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8e121-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="8e121-104">Pokud chcete k definování proměnné pomocí stejného názvu jako prvek základní třídy, můžete skrýt, nebo *stínové*, základní třída prvku při definování proměnné v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="8e121-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="8e121-105">Pokud to uděláte, kód v odvozené třídě přistupuje ke vaše proměnná, pokud explicitně obchází mechanismu stínového provozu.</span><span class="sxs-lookup"><span data-stu-id="8e121-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="8e121-106">Dalším důvodem, že kdy je vhodné pro skrytí zděděné proměnné je ochrana proti revizi základních tříd.</span><span class="sxs-lookup"><span data-stu-id="8e121-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="8e121-107">Základní třídy, může být ke změně, která mění prvek, na který se dědí.</span><span class="sxs-lookup"><span data-stu-id="8e121-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="8e121-108">Pokud se to stane, `Shadows` modifikátor vynutí odkazy z odvozené třídy, které chcete přeložit na proměnnou, místo na prvek základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8e121-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="8e121-109">Chcete-li skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="8e121-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="8e121-110">Ujistěte se, že je deklarována, které chcete skrýt proměnné na úrovni třídy (mimo všechny procedury).</span><span class="sxs-lookup"><span data-stu-id="8e121-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="8e121-111">V opačném případě není potřeba skryli.</span><span class="sxs-lookup"><span data-stu-id="8e121-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="8e121-112">Uvnitř vaší odvozené třídě, zápisu [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarování proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e121-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="8e121-113">Použijte stejný název jako zděděné proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e121-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="8e121-114">Zahrnout [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="8e121-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="8e121-115">Když kód v odvozené třídě odkazuje na název proměnné, přeloží kompilátor odkaz na vaše proměnná.</span><span class="sxs-lookup"><span data-stu-id="8e121-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="8e121-116">Následující příklad ukazuje stínováním zděděné proměnné.</span><span class="sxs-lookup"><span data-stu-id="8e121-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
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
  
     <span data-ttu-id="8e121-117">Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a stíní v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="8e121-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="8e121-118">Postup `showStrings` v odvozené třídě Zobrazí verzi stínového provozu řetězce při název `shadowString` není kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="8e121-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="8e121-119">Potom zobrazí stínovaný verze při `shadowString` je kvalifikována `MyBase` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8e121-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8e121-120">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8e121-120">Robust Programming</span></span>  
 <span data-ttu-id="8e121-121">Stínový provoz přináší více než jedna verze proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="8e121-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="8e121-122">Když příkaz kódu odkazuje na název proměnné, verze, na který přeloží kompilátor odkaz na závisí na faktorech, jako je například umístění příkaz kódu a přítomnost oprávněným řetězec.</span><span class="sxs-lookup"><span data-stu-id="8e121-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="8e121-123">To může zvýšit riziko odkazující na stínové proměnné a nežádoucí verzi.</span><span class="sxs-lookup"><span data-stu-id="8e121-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="8e121-124">Plně kvalifikovaný všechny odkazy na stínové proměnné můžete snížit rizika.</span><span class="sxs-lookup"><span data-stu-id="8e121-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e121-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e121-125">See also</span></span>
- [<span data-ttu-id="8e121-126">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="8e121-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="8e121-127">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e121-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="8e121-128">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="8e121-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="8e121-129">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná</span><span class="sxs-lookup"><span data-stu-id="8e121-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="8e121-130">Postupy: Přístup k proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="8e121-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="8e121-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="8e121-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="8e121-132">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="8e121-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="8e121-133">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8e121-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
