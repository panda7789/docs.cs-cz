---
title: 'Postupy: Řízení rozsahu proměnné (Visual Basic)'
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
ms.openlocfilehash: 7f1d671f6657c7810ec605533493a340baac39c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610345"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="7dc37-102">Postupy: Řízení rozsahu proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dc37-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="7dc37-103">Za normálních okolností je proměnná v *oboru*, nebo viditelné pro použití v rámci oblasti, ve kterém se deklaruje.</span><span class="sxs-lookup"><span data-stu-id="7dc37-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="7dc37-104">V některých případech je proměnná společnosti *úroveň přístupu* mohou mít vliv na svém oboru.</span><span class="sxs-lookup"><span data-stu-id="7dc37-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="7dc37-105">Další informace najdete v tématu [obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="7dc37-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="7dc37-106">Obor bloku nebo úroveň procedury</span><span class="sxs-lookup"><span data-stu-id="7dc37-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="7dc37-107">Aby byla proměnná viditelná pouze v rámci bloku</span><span class="sxs-lookup"><span data-stu-id="7dc37-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="7dc37-108">Místo [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) proměnné mezi zahájení a ukončení příkazy deklarace tohoto bloku, například mezi `For` a `Next` prohlášení o `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="7dc37-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="7dc37-109">Mohou odkazovat na proměnné pouze z v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="7dc37-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="7dc37-110">Aby byla proměnná viditelná pouze v rámci procedury</span><span class="sxs-lookup"><span data-stu-id="7dc37-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="7dc37-111">Místo `Dim` příkaz pro proměnnou uvnitř procesu, ale mimo všechny bloky (například `With`... `End With` bloku).</span><span class="sxs-lookup"><span data-stu-id="7dc37-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="7dc37-112">Mohou odkazovat na proměnné pouze z v rámci procedury, stejně jako dovnitř všechny bloky obsažené v postupu.</span><span class="sxs-lookup"><span data-stu-id="7dc37-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="7dc37-113">Obor na úrovni Namespace nebo modul</span><span class="sxs-lookup"><span data-stu-id="7dc37-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="7dc37-114">Pro usnadnění práce, jeden výraz *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="7dc37-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="7dc37-115">Úroveň přístupu modulu úrovně proměnné určuje její obor.</span><span class="sxs-lookup"><span data-stu-id="7dc37-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="7dc37-116">Obor názvů obsahující modulu, třídy nebo struktury také ovlivňuje oboru.</span><span class="sxs-lookup"><span data-stu-id="7dc37-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="7dc37-117">Ke zviditelnění proměnné v rámci modulu, třídy nebo struktury</span><span class="sxs-lookup"><span data-stu-id="7dc37-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="7dc37-118">Místo `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="7dc37-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="7dc37-119">Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7dc37-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="7dc37-120">Můžete se podívat do proměnné z kamkoli v modulu, třídy nebo struktury, ale ne z mimo něj.</span><span class="sxs-lookup"><span data-stu-id="7dc37-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="7dc37-121">Aby byla proměnná viditelná v celém oboru názvů</span><span class="sxs-lookup"><span data-stu-id="7dc37-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="7dc37-122">Místo `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="7dc37-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="7dc37-123">Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7dc37-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="7dc37-124">Můžete se podívat do proměnné z libovolného místa v rámci oboru názvů obsahujícím modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="7dc37-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dc37-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="7dc37-125">Example</span></span>  
 <span data-ttu-id="7dc37-126">Následující příklad deklaruje proměnnou na úrovni modulu a omezuje viditelnost kódu v rámci modulu.</span><span class="sxs-lookup"><span data-stu-id="7dc37-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
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
  
 <span data-ttu-id="7dc37-127">V předchozím příkladu všechny postupy definované v modulu `demonstrateScope` může odkazovat `String` proměnnou `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="7dc37-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="7dc37-128">Když `usePrivateVariable` volání procedury, zobrazí se obsah proměnné řetězce `strMsg` v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="7dc37-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="7dc37-129">S následující změnou v předchozím příkladu, Řetězcová hodnota `strMsg` lze odkazovat pomocí kódu kdekoli v deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7dc37-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="7dc37-130">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7dc37-130">Robust Programming</span></span>  
 <span data-ttu-id="7dc37-131">Čím užší obor proměnné, méně možností, které máte pro omylem odkazující na jeho místo další proměnnou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="7dc37-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="7dc37-132">Můžete také minimalizovat problémy odpovídající odkaz.</span><span class="sxs-lookup"><span data-stu-id="7dc37-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7dc37-133">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7dc37-133">.NET Framework Security</span></span>  
 <span data-ttu-id="7dc37-134">Čím užší obor proměnné, čím menší pravděpodobnost, že škodlivý kód může být nesprávné použití ho.</span><span class="sxs-lookup"><span data-stu-id="7dc37-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc37-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dc37-135">See also</span></span>

- [<span data-ttu-id="7dc37-136">Obor v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7dc37-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="7dc37-137">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7dc37-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="7dc37-138">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7dc37-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="7dc37-139">Proměnné</span><span class="sxs-lookup"><span data-stu-id="7dc37-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="7dc37-140">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="7dc37-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="7dc37-141">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="7dc37-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
