---
title: Výrazy lambda nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: afefa821f9695dbbfe2a96aee5afd3171ae5b1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700218"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="926cd-102">Výrazy lambda nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz</span><span class="sxs-lookup"><span data-stu-id="926cd-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="926cd-103">Výraz lambda nelze použít pro výraz testů v `Select Case` příkazu.</span><span class="sxs-lookup"><span data-stu-id="926cd-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="926cd-104">Definice výraz lambda vrátí funkce a testovací výraz `Select Case` příkazu musí být typu základní data.</span><span class="sxs-lookup"><span data-stu-id="926cd-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="926cd-105">Následující kód způsobí, že k této chybě:</span><span class="sxs-lookup"><span data-stu-id="926cd-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="926cd-106">**ID chyby:** BC36635</span><span class="sxs-lookup"><span data-stu-id="926cd-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="926cd-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="926cd-107">To correct this error</span></span>  
  
-   <span data-ttu-id="926cd-108">Kontrole kódu k určení, zda jiný podmíněné konstrukce, jako například `If...Then...Else` příkazu by pro vás nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="926cd-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="926cd-109">Pro volání funkce, budete mít určený, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="926cd-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="926cd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="926cd-110">See also</span></span>
- [<span data-ttu-id="926cd-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="926cd-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="926cd-112">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="926cd-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="926cd-113">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="926cd-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
