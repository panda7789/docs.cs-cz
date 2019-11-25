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
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="0641f-102">Postupy: Skrytí zděděné proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0641f-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="0641f-103">A derived class inherits all the definitions of its base class.</span><span class="sxs-lookup"><span data-stu-id="0641f-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="0641f-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span><span class="sxs-lookup"><span data-stu-id="0641f-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="0641f-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span><span class="sxs-lookup"><span data-stu-id="0641f-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="0641f-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span><span class="sxs-lookup"><span data-stu-id="0641f-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="0641f-107">The base class might undergo a change that alters the element you are inheriting.</span><span class="sxs-lookup"><span data-stu-id="0641f-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="0641f-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span><span class="sxs-lookup"><span data-stu-id="0641f-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="0641f-109">To hide an inherited variable</span><span class="sxs-lookup"><span data-stu-id="0641f-109">To hide an inherited variable</span></span>

1. <span data-ttu-id="0641f-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span><span class="sxs-lookup"><span data-stu-id="0641f-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="0641f-111">Otherwise, you do not need to hide it.</span><span class="sxs-lookup"><span data-stu-id="0641f-111">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="0641f-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span><span class="sxs-lookup"><span data-stu-id="0641f-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="0641f-113">Use the same name as that of the inherited variable.</span><span class="sxs-lookup"><span data-stu-id="0641f-113">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="0641f-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span><span class="sxs-lookup"><span data-stu-id="0641f-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="0641f-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span><span class="sxs-lookup"><span data-stu-id="0641f-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="0641f-116">The following example illustrates shadowing of an inherited variable:</span><span class="sxs-lookup"><span data-stu-id="0641f-116">The following example illustrates shadowing of an inherited variable:</span></span>
  
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
  
     <span data-ttu-id="0641f-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span><span class="sxs-lookup"><span data-stu-id="0641f-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="0641f-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span><span class="sxs-lookup"><span data-stu-id="0641f-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="0641f-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span><span class="sxs-lookup"><span data-stu-id="0641f-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0641f-120">Robust programming</span><span class="sxs-lookup"><span data-stu-id="0641f-120">Robust programming</span></span>

<span data-ttu-id="0641f-121">Shadowing introduces more than one version of a variable with the same name.</span><span class="sxs-lookup"><span data-stu-id="0641f-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="0641f-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span><span class="sxs-lookup"><span data-stu-id="0641f-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="0641f-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="0641f-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="0641f-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="0641f-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="0641f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0641f-125">See also</span></span>

- [<span data-ttu-id="0641f-126">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="0641f-126">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="0641f-127">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0641f-127">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="0641f-128">Rozdíly mezi stínováním a přepsáním</span><span class="sxs-lookup"><span data-stu-id="0641f-128">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="0641f-129">Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná</span><span class="sxs-lookup"><span data-stu-id="0641f-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="0641f-130">Postupy: Přístup k proměnné skryté odvozenou třídou</span><span class="sxs-lookup"><span data-stu-id="0641f-130">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="0641f-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="0641f-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="0641f-132">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="0641f-132">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="0641f-133">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="0641f-133">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
