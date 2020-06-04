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
ms.openlocfilehash: 8b21f22edea84448e3f2969c3e4b07c08a17a338
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357345"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="dae56-102">Postupy: Řízení rozsahu proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dae56-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="dae56-103">V normálním případě je proměnná v *oboru*, nebo viditelná pro referenci, v celé oblasti, ve které ji deklarujete.</span><span class="sxs-lookup"><span data-stu-id="dae56-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="dae56-104">V některých případech může mít *úroveň přístupu* proměnné vliv na svůj rozsah.</span><span class="sxs-lookup"><span data-stu-id="dae56-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="dae56-105">Další informace najdete v tématu věnovaném [oboru v Visual Basic](scope.md).</span><span class="sxs-lookup"><span data-stu-id="dae56-105">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="dae56-106">Rozsah na úrovni bloku nebo procedury</span><span class="sxs-lookup"><span data-stu-id="dae56-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="dae56-107">Chcete-li proměnnou zobrazit pouze v rámci bloku</span><span class="sxs-lookup"><span data-stu-id="dae56-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="dae56-108">Umístěte [příkaz Dim](../../../language-reference/statements/dim-statement.md) pro proměnnou mezi příkazy inicializace a ukončující deklarace tohoto bloku, například mezi `For` `Next` příkazy a `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="dae56-108">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="dae56-109">Na proměnnou můžete odkazovat pouze v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="dae56-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="dae56-110">Chcete-li proměnnou zobrazit pouze v rámci procedury</span><span class="sxs-lookup"><span data-stu-id="dae56-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="dae56-111">Do `Dim` procedury umístěte příkaz pro proměnnou, ale mimo libovolný blok (například `With` ... `End With` Block).</span><span class="sxs-lookup"><span data-stu-id="dae56-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="dae56-112">Na proměnnou můžete odkazovat pouze v rámci procedury, včetně uvnitř libovolného bloku, který je obsažen v proceduře.</span><span class="sxs-lookup"><span data-stu-id="dae56-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="dae56-113">Rozsah na úrovni modulu nebo oboru názvů</span><span class="sxs-lookup"><span data-stu-id="dae56-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="dae56-114">Pro usnadnění práce se *úroveň modulu* s jedním termínem aplikuje rovnoměrně na moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="dae56-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="dae56-115">Úroveň přístupu proměnné na úrovni modulu určuje její obor.</span><span class="sxs-lookup"><span data-stu-id="dae56-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="dae56-116">Obor názvů, který obsahuje modul, třídu nebo strukturu, má vliv také na obor.</span><span class="sxs-lookup"><span data-stu-id="dae56-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="dae56-117">Chcete-li zviditelnit proměnnou v rámci modulu, třídy nebo struktury</span><span class="sxs-lookup"><span data-stu-id="dae56-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="dae56-118">Umístěte `Dim` příkaz pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.</span><span class="sxs-lookup"><span data-stu-id="dae56-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="dae56-119">Do příkazu zahrňte klíčové slovo [Private](../../../language-reference/modifiers/private.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="dae56-119">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="dae56-120">Na proměnnou můžete odkazovat odkudkoli v rámci modulu, třídy nebo struktury, ale ne z vnějšku.</span><span class="sxs-lookup"><span data-stu-id="dae56-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="dae56-121">Chcete-li nastavit proměnnou v rámci oboru názvů jako viditelné</span><span class="sxs-lookup"><span data-stu-id="dae56-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="dae56-122">Umístěte `Dim` příkaz pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.</span><span class="sxs-lookup"><span data-stu-id="dae56-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="dae56-123">Do příkazu zahrňte klíčové slovo [Friend](../../../language-reference/modifiers/friend.md) nebo [Public](../../../language-reference/modifiers/public.md) `Dim` .</span><span class="sxs-lookup"><span data-stu-id="dae56-123">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="dae56-124">Na proměnnou můžete odkazovat odkudkoli v rámci oboru názvů obsahujícího modul, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="dae56-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dae56-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="dae56-125">Example</span></span>  
 <span data-ttu-id="dae56-126">Následující příklad deklaruje proměnnou na úrovni modulu a omezí její viditelnost na kód v rámci modulu.</span><span class="sxs-lookup"><span data-stu-id="dae56-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
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
  
 <span data-ttu-id="dae56-127">V předchozím příkladu všechny procedury definované v modulu `demonstrateScope` mohou odkazovat na `String` proměnnou `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="dae56-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="dae56-128">Při `usePrivateVariable` volání procedury se zobrazí obsah proměnné řetězce `strMsg` v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="dae56-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="dae56-129">S následující změnou v předchozím příkladu může být řetězcová proměnná `strMsg` odkazována pomocí kódu kdekoli v oboru názvů své deklarace.</span><span class="sxs-lookup"><span data-stu-id="dae56-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="dae56-130">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="dae56-130">Robust Programming</span></span>  
 <span data-ttu-id="dae56-131">Čím užší je rozsah proměnné, tím menší je počet příležitostí, které se na ni neodkazují na místo jiné proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="dae56-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="dae56-132">Můžete také minimalizovat problémy s porovnáním odkazů.</span><span class="sxs-lookup"><span data-stu-id="dae56-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dae56-133">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dae56-133">.NET Framework Security</span></span>  
 <span data-ttu-id="dae56-134">Zúžení rozsahu proměnné, menší pravděpodobnost, že škodlivý kód může nevhodným způsobem používat.</span><span class="sxs-lookup"><span data-stu-id="dae56-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae56-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="dae56-135">See also</span></span>

- [<span data-ttu-id="dae56-136">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dae56-136">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="dae56-137">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dae56-137">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="dae56-138">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dae56-138">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="dae56-139">Proměnné</span><span class="sxs-lookup"><span data-stu-id="dae56-139">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="dae56-140">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="dae56-140">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="dae56-141">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="dae56-141">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
