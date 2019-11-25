---
title: '&amp; – operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336059"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="7bcec-102">&amp; Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcec-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="7bcec-103">Generates a string concatenation of two expressions.</span><span class="sxs-lookup"><span data-stu-id="7bcec-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bcec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bcec-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="7bcec-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7bcec-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7bcec-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7bcec-106">Required.</span></span> <span data-ttu-id="7bcec-107">Any `String` or `Object` variable.</span><span class="sxs-lookup"><span data-stu-id="7bcec-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="7bcec-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7bcec-108">Required.</span></span> <span data-ttu-id="7bcec-109">Any expression with a data type that widens to `String`.</span><span class="sxs-lookup"><span data-stu-id="7bcec-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="7bcec-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="7bcec-110">Required.</span></span> <span data-ttu-id="7bcec-111">Any expression with a data type that widens to `String`.</span><span class="sxs-lookup"><span data-stu-id="7bcec-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bcec-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bcec-112">Remarks</span></span>  
 <span data-ttu-id="7bcec-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span><span class="sxs-lookup"><span data-stu-id="7bcec-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="7bcec-114">If either of the data types does not widen to `String`, the compiler generates an error.</span><span class="sxs-lookup"><span data-stu-id="7bcec-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="7bcec-115">The data type of `result` is `String`.</span><span class="sxs-lookup"><span data-stu-id="7bcec-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="7bcec-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span><span class="sxs-lookup"><span data-stu-id="7bcec-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bcec-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="7bcec-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7bcec-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="7bcec-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7bcec-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7bcec-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bcec-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span><span class="sxs-lookup"><span data-stu-id="7bcec-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="7bcec-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="7bcec-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bcec-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bcec-122">Example</span></span>  
 <span data-ttu-id="7bcec-123">This example uses the `&` operator to force string concatenation.</span><span class="sxs-lookup"><span data-stu-id="7bcec-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="7bcec-124">The result is a string value representing the concatenation of the two string operands.</span><span class="sxs-lookup"><span data-stu-id="7bcec-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7bcec-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bcec-125">See also</span></span>

- [<span data-ttu-id="7bcec-126">Operátor &=</span><span class="sxs-lookup"><span data-stu-id="7bcec-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="7bcec-127">Operátory řetězení</span><span class="sxs-lookup"><span data-stu-id="7bcec-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="7bcec-128">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bcec-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7bcec-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="7bcec-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="7bcec-130">Concatenation Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bcec-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
