---
title: První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: ca16c6604ee071668a5c65d7e9052b233e2313c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403015"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="52d3e-102">První operand v binárním výrazu 'If' musí být typu, který povoluje hodnotu Null, nebo typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="52d3e-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="52d3e-103">`If`Výraz může přijmout buď dva, nebo tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="52d3e-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="52d3e-104">Když odesíláte pouze dva argumenty, první argument musí být odkazový typ nebo typ hodnoty s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="52d3e-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="52d3e-105">Pokud je první argument vyhodnocen jako cokoli jiného než `Nothing` , je vrácena jeho hodnota.</span><span class="sxs-lookup"><span data-stu-id="52d3e-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="52d3e-106">Pokud je první argument vyhodnocen jako `Nothing` , je vyhodnocen a vrácen druhý argument.</span><span class="sxs-lookup"><span data-stu-id="52d3e-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="52d3e-107">Například následující kód obsahuje dva `If` výrazy, jeden se třemi argumenty a jeden se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="52d3e-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="52d3e-108">Výrazy vypočítávají a vracejí stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="52d3e-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="52d3e-109">Tato chyba způsobí tyto výrazy:</span><span class="sxs-lookup"><span data-stu-id="52d3e-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="52d3e-110">**ID chyby:** BC33107</span><span class="sxs-lookup"><span data-stu-id="52d3e-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52d3e-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="52d3e-111">To correct this error</span></span>  
  
- <span data-ttu-id="52d3e-112">Pokud nemůžete změnit kód tak, aby první argument byl typ hodnoty s možnou hodnotou null nebo odkazový typ, zvažte převod na výraz se třemi argumenty `If` nebo na `If...Then...Else` příkaz.</span><span class="sxs-lookup"><span data-stu-id="52d3e-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="52d3e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="52d3e-113">See also</span></span>

- [<span data-ttu-id="52d3e-114">If – operátor</span><span class="sxs-lookup"><span data-stu-id="52d3e-114">If Operator</span></span>](../operators/if-operator.md)
- [<span data-ttu-id="52d3e-115">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="52d3e-115">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="52d3e-116">Typy hodnot s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="52d3e-116">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
