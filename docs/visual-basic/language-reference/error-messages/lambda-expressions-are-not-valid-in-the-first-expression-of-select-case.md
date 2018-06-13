---
title: Lambda – výrazy nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588918"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="148a2-102">Lambda – výrazy nejsou platné v prvním výrazu &#39;Select Case&#39; – příkaz</span><span class="sxs-lookup"><span data-stu-id="148a2-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="148a2-103">Výraz lambda nelze použít pro výraz testu v `Select Case` příkaz.</span><span class="sxs-lookup"><span data-stu-id="148a2-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="148a2-104">Definice výrazu lambda vrátí funkce a testovací výraz `Select Case` příkaz musí být základní datového typu.</span><span class="sxs-lookup"><span data-stu-id="148a2-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="148a2-105">Následující kód způsobí, že tuto chybu:</span><span class="sxs-lookup"><span data-stu-id="148a2-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="148a2-106">**ID chyby:** BC36635</span><span class="sxs-lookup"><span data-stu-id="148a2-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="148a2-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="148a2-107">To correct this error</span></span>  
  
-   <span data-ttu-id="148a2-108">Zkontrolujte v kódu k určení, zda jiný podmíněné konstrukce, jako například `If...Then...Else` by pro vás pracovní příkaz.</span><span class="sxs-lookup"><span data-stu-id="148a2-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="148a2-109">Pro volání funkce, můžete mít určen, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="148a2-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="148a2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="148a2-110">See Also</span></span>  
 [<span data-ttu-id="148a2-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="148a2-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="148a2-112">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="148a2-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="148a2-113">Příkaz Select...Case</span><span class="sxs-lookup"><span data-stu-id="148a2-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
