---
title: Nepovinné (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: f88020c7407fb9c91e06bc2ee177773171e344fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599301"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="d7706-102">Nepovinné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7706-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="d7706-103">Určuje, že při volání procedury lze vynechat argumentu procedury.</span><span class="sxs-lookup"><span data-stu-id="d7706-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7706-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7706-104">Remarks</span></span>  
 <span data-ttu-id="d7706-105">Pro každý volitelný parametr je nutné určit konstantní výraz jako výchozí hodnota tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="d7706-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="d7706-106">Pokud je výsledkem výrazu [nic](../../../visual-basic/language-reference/nothing.md), výchozí hodnota typu dat, hodnota se používá jako výchozí hodnota parametru.</span><span class="sxs-lookup"><span data-stu-id="d7706-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="d7706-107">Pokud seznam parametrů obsahuje volitelný parametr, musí být každý parametr, který následuje také volitelné.</span><span class="sxs-lookup"><span data-stu-id="d7706-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="d7706-108">`Optional` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="d7706-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="d7706-109">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="d7706-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="d7706-110">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="d7706-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="d7706-111">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="d7706-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="d7706-112">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="d7706-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="d7706-113">Při volání procedury s nebo bez volitelné parametry, můžete předat argumentů podle pozice nebo podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d7706-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="d7706-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="d7706-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7706-115">Procedura se volitelné parametry můžete také definovat pomocí přetížení.</span><span class="sxs-lookup"><span data-stu-id="d7706-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="d7706-116">Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze postup, který přijme parametr a ten, který není.</span><span class="sxs-lookup"><span data-stu-id="d7706-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="d7706-117">Další informace najdete v tématu [přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="d7706-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7706-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7706-118">Example</span></span>  
 <span data-ttu-id="d7706-119">V následujícím příkladu definuje procedury, která je volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="d7706-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="d7706-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7706-120">Example</span></span>  
 <span data-ttu-id="d7706-121">Následující příklad ukazuje způsob volání procedury s argumenty předávané podle pozice a argumentů předaných podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d7706-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="d7706-122">Postup má dva volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="d7706-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d7706-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7706-123">See Also</span></span>  
 [<span data-ttu-id="d7706-124">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="d7706-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="d7706-125">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="d7706-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="d7706-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d7706-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
