---
title: První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249523"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="b52e8-102">První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="b52e8-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="b52e8-103">Výraz `If` může trvat dva nebo tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="b52e8-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="b52e8-104">Při odeslání pouze dva argumenty, první argument musí být typ odkazu nebo typ hodnoty s hodnotou s hodnotou, kterou lze hodnotit.</span><span class="sxs-lookup"><span data-stu-id="b52e8-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="b52e8-105">Pokud první argument vyhodnotí `Nothing`na něco jiného než , jeho hodnota je vrácena.</span><span class="sxs-lookup"><span data-stu-id="b52e8-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="b52e8-106">Pokud první argument vyhodnotí `Nothing`na , druhý argument je vyhodnocena a vrácena.</span><span class="sxs-lookup"><span data-stu-id="b52e8-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="b52e8-107">Například následující kód obsahuje `If` dva výrazy, jeden se třemi argumenty a jeden se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="b52e8-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="b52e8-108">Výrazy vypočítat a vrátit stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b52e8-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="b52e8-109">Následující výrazy způsobit tuto chybu:</span><span class="sxs-lookup"><span data-stu-id="b52e8-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="b52e8-110">**ID chyby:** BC33107</span><span class="sxs-lookup"><span data-stu-id="b52e8-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b52e8-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b52e8-111">To correct this error</span></span>  
  
- <span data-ttu-id="b52e8-112">Pokud nemůžete změnit kód tak, aby první argument byl typ hodnoty s hodnotou s `If` hodnotou s `If...Then...Else` hodnotou s hodnotou nebo typ odkazu, zvažte převod na výraz se třemi argumenty nebo na příkaz.</span><span class="sxs-lookup"><span data-stu-id="b52e8-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="b52e8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b52e8-113">See also</span></span>

- [<span data-ttu-id="b52e8-114">Operátor If</span><span class="sxs-lookup"><span data-stu-id="b52e8-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="b52e8-115">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="b52e8-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="b52e8-116">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="b52e8-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
