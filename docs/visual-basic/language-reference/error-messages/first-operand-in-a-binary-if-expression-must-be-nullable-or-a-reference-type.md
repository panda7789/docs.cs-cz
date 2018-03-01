---
title: "První operand v binárním & č. 39; Pokud & č. 39; Výraz musí být null nebo zadejte odkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f66b110c02076120c55a3bff28c3d7614bf8be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="c093a-102">První operand v binárním & č. 39; Pokud & č. 39; Výraz musí být null nebo zadejte odkaz</span><span class="sxs-lookup"><span data-stu-id="c093a-102">First operand in a binary &#39;If&#39; expression must be nullable or a reference type</span></span>
<span data-ttu-id="c093a-103">`If` Výrazu může trvat dvě nebo tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="c093a-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="c093a-104">Při odesílání pouze dva argumenty, první argument musí být odkazového typu nebo typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="c093a-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="c093a-105">Pokud je první argument výsledkem k ničemu jiné než `Nothing`, je vrácena jeho hodnota.</span><span class="sxs-lookup"><span data-stu-id="c093a-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="c093a-106">Pokud se vyhodnotí jako první argument `Nothing`, druhý argument je vyhodnocena a vrácena.</span><span class="sxs-lookup"><span data-stu-id="c093a-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="c093a-107">Například následující kód obsahuje dva `If` výrazy, jeden s tři argumenty a jednu s dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="c093a-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="c093a-108">Výrazy výpočtu a vrací stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c093a-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="c093a-109">Tuto chybu způsobí těchto výrazů:</span><span class="sxs-lookup"><span data-stu-id="c093a-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="c093a-110">**ID chyby:** BC33107</span><span class="sxs-lookup"><span data-stu-id="c093a-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c093a-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c093a-111">To correct this error</span></span>  
  
-   <span data-ttu-id="c093a-112">Pokud kód nelze změnit tak, aby první argument na typ s možnou hodnotou Null nebo odkaz na typ, zvažte, převod argumentem tři `If` výrazu, nebo `If...Then...Else` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c093a-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="c093a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c093a-113">See Also</span></span>  
 [<span data-ttu-id="c093a-114">Pokud operátor</span><span class="sxs-lookup"><span data-stu-id="c093a-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="c093a-115">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="c093a-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="c093a-116">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="c093a-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
