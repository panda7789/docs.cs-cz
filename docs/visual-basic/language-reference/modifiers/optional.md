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
ms.openlocfilehash: 67ceedffecdfba8ec0c2829a3af31d194f18bd88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920663"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="74170-102">Nepovinné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74170-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="74170-103">Určuje, že argumentu procedury může při volání procedury vynechat.</span><span class="sxs-lookup"><span data-stu-id="74170-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74170-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74170-104">Remarks</span></span>  
 <span data-ttu-id="74170-105">Pro každý volitelný parametr musíte zadat konstantní výraz jako výchozí hodnota tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="74170-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="74170-106">Pokud je výraz vyhodnocen [nic](../../../visual-basic/language-reference/nothing.md), je použita výchozí hodnota datového typu hodnoty jako výchozí hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="74170-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="74170-107">Pokud seznam parametrů obsahuje volitelný parametr, každý parametr, která ji následuje musí být také volitelný.</span><span class="sxs-lookup"><span data-stu-id="74170-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="74170-108">`Optional` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="74170-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="74170-109">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="74170-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="74170-110">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="74170-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="74170-111">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="74170-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="74170-112">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="74170-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="74170-113">Při volání procedury s nebo bez něj volitelné parametry, můžete předat argumenty podle umístění nebo podle názvu.</span><span class="sxs-lookup"><span data-stu-id="74170-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="74170-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="74170-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74170-115">Proceduru s volitelnými parametry lze definovat také pomocí přetížení.</span><span class="sxs-lookup"><span data-stu-id="74170-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="74170-116">Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze procedury, ten, který přijímá parametr a ten, který nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="74170-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="74170-117">Další informace najdete v tématu [přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="74170-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74170-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="74170-118">Example</span></span>  
 <span data-ttu-id="74170-119">Následující příklad definuje proceduru, která je volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="74170-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="74170-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="74170-120">Example</span></span>  
 <span data-ttu-id="74170-121">Následující příklad ukazuje, jak volání procedury s argumenty předány podle pozice a s argumenty předány podle názvu.</span><span class="sxs-lookup"><span data-stu-id="74170-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="74170-122">Postup má dva volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="74170-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="74170-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74170-123">See also</span></span>

- [<span data-ttu-id="74170-124">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="74170-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="74170-125">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="74170-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="74170-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="74170-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
