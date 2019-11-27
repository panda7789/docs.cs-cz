---
title: 'Postupy: Skrytí zděděné proměnné'
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
ms.openlocfilehash: c20c36b26c90c82da4e8836799f499498ccc40e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345352"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="bcb34-102">Postupy: Skrytí zděděné proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcb34-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="bcb34-103">Odvozená třída dědí všechny definice své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bcb34-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="bcb34-104">Pokud chcete definovat proměnnou pomocí stejného názvu jako element základní třídy, můžete skrýt nebo vytvořit *stín*, který prvek základní třídy při definování proměnné v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="bcb34-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="bcb34-105">Pokud to uděláte, kód v odvozené třídě přistupuje k proměnné, pokud explicitně neobejde mechanismus stínování.</span><span class="sxs-lookup"><span data-stu-id="bcb34-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="bcb34-106">Dalším důvodem, proč je vhodné skrýt zděděnou proměnnou, je chránit před revizí základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bcb34-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="bcb34-107">Základní třída může podléhat změně, která mění prvek, který je děděn.</span><span class="sxs-lookup"><span data-stu-id="bcb34-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="bcb34-108">Pokud k tomu dojde, modifikátor `Shadows` vynutí, aby byly odkazy z odvozené třídy přeloženy na vaši proměnnou namísto elementu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bcb34-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="bcb34-109">Skrytí zděděné proměnné</span><span class="sxs-lookup"><span data-stu-id="bcb34-109">To hide an inherited variable</span></span>

1. <span data-ttu-id="bcb34-110">Ujistěte se, že proměnná, kterou chcete skrýt, je deklarována na úrovni třídy (mimo jakoukoliv proceduru).</span><span class="sxs-lookup"><span data-stu-id="bcb34-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="bcb34-111">V opačném případě ji nemusíte skrývat.</span><span class="sxs-lookup"><span data-stu-id="bcb34-111">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="bcb34-112">V rámci odvozené třídy napište [příkaz Dim](../../../language-reference/statements/dim-statement.md) , který deklaruje vaši proměnnou.</span><span class="sxs-lookup"><span data-stu-id="bcb34-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="bcb34-113">Použijte stejný název jako u zděděné proměnné.</span><span class="sxs-lookup"><span data-stu-id="bcb34-113">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="bcb34-114">Do deklarace zahrňte klíčové slovo [Shadows](../../../language-reference/modifiers/shadows.md) .</span><span class="sxs-lookup"><span data-stu-id="bcb34-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="bcb34-115">Pokud kód v odvozené třídě odkazuje na název proměnné, kompilátor vyřeší odkaz na vaši proměnnou.</span><span class="sxs-lookup"><span data-stu-id="bcb34-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="bcb34-116">Následující příklad znázorňuje stíny zděděné proměnné:</span><span class="sxs-lookup"><span data-stu-id="bcb34-116">The following example illustrates shadowing of an inherited variable:</span></span>
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="bcb34-117">Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a nastínuje ji v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="bcb34-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="bcb34-118">Procedura `ShowStrings` v odvozené třídě zobrazuje stínovou verzi řetězce, když název `shadowString` není kvalifikován.</span><span class="sxs-lookup"><span data-stu-id="bcb34-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="bcb34-119">Když je `shadowString` kvalifikován pomocí klíčového slova `MyBase`, zobrazí se stínovaná verze.</span><span class="sxs-lookup"><span data-stu-id="bcb34-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bcb34-120">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="bcb34-120">Robust programming</span></span>

<span data-ttu-id="bcb34-121">Stíning zavádí více než jednu verzi proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="bcb34-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="bcb34-122">Pokud příkaz kódu odkazuje na název proměnné, verze, na kterou kompilátor vyřeší odkaz, závisí na faktorech, jako je například umístění příkazu kódu a přítomnost opravňujícího řetězce.</span><span class="sxs-lookup"><span data-stu-id="bcb34-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="bcb34-123">To může zvýšit riziko odkazování na neúmyslnou verzi stínové proměnné.</span><span class="sxs-lookup"><span data-stu-id="bcb34-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="bcb34-124">Toto riziko můžete snížit tím, že plně zadáte všechny odkazy na stínovou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="bcb34-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcb34-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcb34-125">See also</span></span>

- [<span data-ttu-id="bcb34-126">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="bcb34-126">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="bcb34-127">Stínování v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bcb34-127">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="bcb34-128">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="bcb34-128">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="bcb34-129">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná</span><span class="sxs-lookup"><span data-stu-id="bcb34-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="bcb34-130">Postupy: Přístup k proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="bcb34-130">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="bcb34-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="bcb34-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="bcb34-132">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="bcb34-132">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="bcb34-133">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="bcb34-133">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
