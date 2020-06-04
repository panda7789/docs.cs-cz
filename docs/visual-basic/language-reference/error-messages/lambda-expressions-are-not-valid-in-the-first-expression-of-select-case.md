---
title: Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 08f7cd9dd95a10cad0df6539ba43122495347bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397360"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="4ad3b-102">Použití výrazů lambda v prvním výrazu příkazu 'Select Case' je neplatné.</span><span class="sxs-lookup"><span data-stu-id="4ad3b-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>
<span data-ttu-id="4ad3b-103">Výraz lambda nelze použít pro výraz testu v `Select Case` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4ad3b-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="4ad3b-104">Definice výrazů lambda vrací funkce a výraz testu `Select Case` příkazu musí být základní datový typ.</span><span class="sxs-lookup"><span data-stu-id="4ad3b-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="4ad3b-105">Následující kód způsobuje tuto chybu:</span><span class="sxs-lookup"><span data-stu-id="4ad3b-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="4ad3b-106">**ID chyby:** BC36635</span><span class="sxs-lookup"><span data-stu-id="4ad3b-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ad3b-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4ad3b-107">To correct this error</span></span>  
  
- <span data-ttu-id="4ad3b-108">Projděte si kód, abyste zjistili, jestli pro vás funguje jiná podmíněná konstrukce, jako je třeba `If...Then...Else` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4ad3b-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
- <span data-ttu-id="4ad3b-109">Možná budete chtít zavolat funkci, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4ad3b-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ad3b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ad3b-110">See also</span></span>

- [<span data-ttu-id="4ad3b-111">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="4ad3b-111">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="4ad3b-112">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="4ad3b-112">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="4ad3b-113">Select...Case – příkaz</span><span class="sxs-lookup"><span data-stu-id="4ad3b-113">Select...Case Statement</span></span>](../statements/select-case-statement.md)
