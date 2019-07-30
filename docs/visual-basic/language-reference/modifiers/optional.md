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
ms.openlocfilehash: 3758f17634395236abf2cd7059418bf6f8b6c062
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630931"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="591fa-102">Nepovinné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="591fa-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="591fa-103">Určuje, že při volání procedury lze argument procedury vynechat.</span><span class="sxs-lookup"><span data-stu-id="591fa-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="591fa-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="591fa-104">Remarks</span></span>

<span data-ttu-id="591fa-105">Pro každý volitelný parametr je nutné zadat konstantní výraz jako výchozí hodnotu tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="591fa-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="591fa-106">Pokud je výraz vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md), je jako výchozí hodnota parametru použita výchozí hodnota datového typu value.</span><span class="sxs-lookup"><span data-stu-id="591fa-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="591fa-107">Pokud seznam parametrů obsahuje volitelný parametr, všechny parametry, které následují, musí být také volitelné.</span><span class="sxs-lookup"><span data-stu-id="591fa-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="591fa-108">V těchto kontextech lze použít Modifikátor:`Optional`</span><span class="sxs-lookup"><span data-stu-id="591fa-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="591fa-109">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="591fa-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="591fa-110">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="591fa-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="591fa-111">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="591fa-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="591fa-112">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="591fa-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="591fa-113">Při volání procedury s nepovinnými parametry nebo bez nich můžete předat argumenty podle umístění nebo podle názvu.</span><span class="sxs-lookup"><span data-stu-id="591fa-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="591fa-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="591fa-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="591fa-115">Můžete také definovat proceduru s nepovinnými parametry pomocí přetížení.</span><span class="sxs-lookup"><span data-stu-id="591fa-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="591fa-116">Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze procedury, jednu, která přijímá parametr a druhý.</span><span class="sxs-lookup"><span data-stu-id="591fa-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="591fa-117">Další informace najdete v tématu [přetížení procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="591fa-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="591fa-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="591fa-118">Example</span></span>

<span data-ttu-id="591fa-119">Následující příklad definuje proceduru, která má volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="591fa-119">The following example defines a procedure that has an optional parameter.</span></span>

```vb
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

## <a name="example"></a><span data-ttu-id="591fa-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="591fa-120">Example</span></span>

<span data-ttu-id="591fa-121">Následující příklad ukazuje způsob volání procedury s argumenty předanými pozicí a s argumenty předanými názvem.</span><span class="sxs-lookup"><span data-stu-id="591fa-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="591fa-122">Procedura má dva volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="591fa-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="591fa-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="591fa-123">See also</span></span>

- [<span data-ttu-id="591fa-124">Seznam parametrů</span><span class="sxs-lookup"><span data-stu-id="591fa-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="591fa-125">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="591fa-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="591fa-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="591fa-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
