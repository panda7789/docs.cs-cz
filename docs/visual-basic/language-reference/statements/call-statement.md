---
title: Call – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: a04ebddc7db176188876da1082e1e6946e1e8eec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005164"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="ac098-102">Call – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac098-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="ac098-103">Přenáší řízení na proceduru `Function`, `Sub` nebo Dynamic-Link Library (DLL).</span><span class="sxs-lookup"><span data-stu-id="ac098-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac098-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac098-104">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ac098-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ac098-105">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="ac098-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ac098-106">Required.</span></span> <span data-ttu-id="ac098-107">Název procedury, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="ac098-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="ac098-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ac098-108">Optional.</span></span> <span data-ttu-id="ac098-109">Seznam proměnných nebo výrazů představujících argumenty, které jsou předány proceduře při volání.</span><span class="sxs-lookup"><span data-stu-id="ac098-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="ac098-110">Více argumentů je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="ac098-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="ac098-111">Pokud zahrnete `argumentList`, musíte ho uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="ac098-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="ac098-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac098-112">Remarks</span></span>

 <span data-ttu-id="ac098-113">Při volání procedury můžete použít klíčové slovo `Call`.</span><span class="sxs-lookup"><span data-stu-id="ac098-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="ac098-114">U většiny volání procedur nemusíte používat toto klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ac098-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="ac098-115">Pokud pojmenovaný výraz nezačíná identifikátorem, obvykle se používá klíčové slovo `Call`.</span><span class="sxs-lookup"><span data-stu-id="ac098-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="ac098-116">Použití klíčového slova `Call` pro jiné použití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="ac098-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="ac098-117">Pokud procedura vrátí hodnotu, příkaz `Call` ho zahodí.</span><span class="sxs-lookup"><span data-stu-id="ac098-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="ac098-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac098-118">Example</span></span>

 <span data-ttu-id="ac098-119">Následující kód ukazuje dva příklady, kde klíčové slovo `Call` je nezbytné pro volání procedury.</span><span class="sxs-lookup"><span data-stu-id="ac098-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="ac098-120">V obou příkladech se u volaného výrazu nezahájí identifikátor.</span><span class="sxs-lookup"><span data-stu-id="ac098-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="ac098-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac098-121">See also</span></span>

- [<span data-ttu-id="ac098-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="ac098-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="ac098-123">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="ac098-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="ac098-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="ac098-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="ac098-125">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="ac098-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
