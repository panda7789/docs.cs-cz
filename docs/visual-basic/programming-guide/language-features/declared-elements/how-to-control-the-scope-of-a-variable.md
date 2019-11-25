---
title: 'Postupy: Řízení rozsahu proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345380"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="2914e-102">Postupy: Řízení rozsahu proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2914e-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="2914e-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span><span class="sxs-lookup"><span data-stu-id="2914e-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="2914e-104">In some cases, the variable's *access level* can influence its scope.</span><span class="sxs-lookup"><span data-stu-id="2914e-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="2914e-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="2914e-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="2914e-106">Scope at Block or Procedure Level</span><span class="sxs-lookup"><span data-stu-id="2914e-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="2914e-107">To make a variable visible only within a block</span><span class="sxs-lookup"><span data-stu-id="2914e-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="2914e-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span><span class="sxs-lookup"><span data-stu-id="2914e-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="2914e-109">You can refer to the variable only from within the block.</span><span class="sxs-lookup"><span data-stu-id="2914e-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="2914e-110">To make a variable visible only within a procedure</span><span class="sxs-lookup"><span data-stu-id="2914e-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="2914e-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span><span class="sxs-lookup"><span data-stu-id="2914e-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="2914e-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span><span class="sxs-lookup"><span data-stu-id="2914e-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="2914e-113">Scope at Module or Namespace Level</span><span class="sxs-lookup"><span data-stu-id="2914e-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="2914e-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span><span class="sxs-lookup"><span data-stu-id="2914e-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="2914e-115">The access level of a module level variable determines its scope.</span><span class="sxs-lookup"><span data-stu-id="2914e-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="2914e-116">The namespace that contains the module, class, or structure also influences the scope.</span><span class="sxs-lookup"><span data-stu-id="2914e-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="2914e-117">To make a variable visible throughout a module, class, or structure</span><span class="sxs-lookup"><span data-stu-id="2914e-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="2914e-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span><span class="sxs-lookup"><span data-stu-id="2914e-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="2914e-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="2914e-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="2914e-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span><span class="sxs-lookup"><span data-stu-id="2914e-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="2914e-121">To make a variable visible throughout a namespace</span><span class="sxs-lookup"><span data-stu-id="2914e-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="2914e-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span><span class="sxs-lookup"><span data-stu-id="2914e-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="2914e-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="2914e-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="2914e-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="2914e-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2914e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2914e-125">Example</span></span>  
 <span data-ttu-id="2914e-126">The following example declares a variable at module level and limits its visibility to code within the module.</span><span class="sxs-lookup"><span data-stu-id="2914e-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2914e-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="2914e-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="2914e-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span><span class="sxs-lookup"><span data-stu-id="2914e-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="2914e-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span><span class="sxs-lookup"><span data-stu-id="2914e-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="2914e-130">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2914e-130">Robust Programming</span></span>  
 <span data-ttu-id="2914e-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span><span class="sxs-lookup"><span data-stu-id="2914e-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="2914e-132">You can also minimize problems of reference matching.</span><span class="sxs-lookup"><span data-stu-id="2914e-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2914e-133">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2914e-133">.NET Framework Security</span></span>  
 <span data-ttu-id="2914e-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span><span class="sxs-lookup"><span data-stu-id="2914e-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2914e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2914e-135">See also</span></span>

- [<span data-ttu-id="2914e-136">Scope in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2914e-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="2914e-137">Lifetime in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2914e-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="2914e-138">Access levels in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2914e-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2914e-139">Proměnné</span><span class="sxs-lookup"><span data-stu-id="2914e-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="2914e-140">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="2914e-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="2914e-141">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="2914e-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
