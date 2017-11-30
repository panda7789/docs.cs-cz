---
title: "Lambda – výrazy nejsou platné v prvním výrazu a & č. 39; Vyberte případ & č. 39; příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords: BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="fc4e3-102">Lambda – výrazy nejsou platné v prvním výrazu a & č. 39; Vyberte případ & č. 39; příkaz</span><span class="sxs-lookup"><span data-stu-id="fc4e3-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="fc4e3-103">Výraz lambda nelze použít pro výraz testu v `Select Case` příkaz.</span><span class="sxs-lookup"><span data-stu-id="fc4e3-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="fc4e3-104">Definice výrazu lambda vrátí funkce a testovací výraz `Select Case` příkaz musí být základní datového typu.</span><span class="sxs-lookup"><span data-stu-id="fc4e3-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="fc4e3-105">Následující kód způsobí, že tuto chybu:</span><span class="sxs-lookup"><span data-stu-id="fc4e3-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="fc4e3-106">**ID chyby:** BC36635</span><span class="sxs-lookup"><span data-stu-id="fc4e3-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fc4e3-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fc4e3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="fc4e3-108">Zkontrolujte v kódu k určení, zda jiný podmíněné konstrukce, jako například `If...Then...Else` by pro vás pracovní příkaz.</span><span class="sxs-lookup"><span data-stu-id="fc4e3-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="fc4e3-109">Pro volání funkce, můžete mít určen, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="fc4e3-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc4e3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc4e3-110">See Also</span></span>  
 [<span data-ttu-id="fc4e3-111">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="fc4e3-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="fc4e3-112">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="fc4e3-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="fc4e3-113">Vyberte... Case – příkaz</span><span class="sxs-lookup"><span data-stu-id="fc4e3-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
