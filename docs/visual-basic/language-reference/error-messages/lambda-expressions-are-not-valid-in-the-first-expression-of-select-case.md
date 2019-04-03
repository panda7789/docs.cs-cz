---
title: Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e51ba4ad0910d0db2b927f84303e5c55515f4b84
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843446"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="0c98f-102">Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.</span><span class="sxs-lookup"><span data-stu-id="0c98f-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>
<span data-ttu-id="0c98f-103">Výraz lambda nelze použít pro výraz testů v `Select Case` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0c98f-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="0c98f-104">Definice výraz lambda vrátí funkce a testovací výraz `Select Case` příkazu musí být typu základní data.</span><span class="sxs-lookup"><span data-stu-id="0c98f-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="0c98f-105">Následující kód způsobí, že k této chybě:</span><span class="sxs-lookup"><span data-stu-id="0c98f-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="0c98f-106">**ID chyby:** BC36635</span><span class="sxs-lookup"><span data-stu-id="0c98f-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c98f-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0c98f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="0c98f-108">Kontrole kódu k určení, zda jiný podmíněné konstrukce, jako například `If...Then...Else` příkazu by pro vás nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="0c98f-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="0c98f-109">Pro volání funkce, budete mít určený, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0c98f-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c98f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c98f-110">See also</span></span>

- [<span data-ttu-id="0c98f-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="0c98f-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="0c98f-112">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="0c98f-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="0c98f-113">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="0c98f-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
