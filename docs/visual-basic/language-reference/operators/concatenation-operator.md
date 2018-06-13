---
title: '&amp; Operátor (Visual Basic)'
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
ms.openlocfilehash: 28d8cdb22974d77edf055ab9b2c6c767872e6783
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604299"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="5efd5-102">&amp; Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5efd5-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="5efd5-103">Vytvoří spojení řetězců dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="5efd5-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5efd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5efd5-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="5efd5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="5efd5-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="5efd5-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5efd5-106">Required.</span></span> <span data-ttu-id="5efd5-107">Všechny `String` nebo `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="5efd5-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="5efd5-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5efd5-108">Required.</span></span> <span data-ttu-id="5efd5-109">Jakýkoli výraz s datovým typem, který rozšiřuje na `String`.</span><span class="sxs-lookup"><span data-stu-id="5efd5-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="5efd5-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5efd5-110">Required.</span></span> <span data-ttu-id="5efd5-111">Jakýkoli výraz s datovým typem, který rozšiřuje na `String`.</span><span class="sxs-lookup"><span data-stu-id="5efd5-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5efd5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5efd5-112">Remarks</span></span>  
 <span data-ttu-id="5efd5-113">Pokud datový typ `expression1` nebo `expression2` není `String` ale rozšiřuje na `String`, jsou převedeny na `String`.</span><span class="sxs-lookup"><span data-stu-id="5efd5-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="5efd5-114">Pokud některý z datové typy není rozšíří do `String`, kompilátor, vygeneruje se chyba.</span><span class="sxs-lookup"><span data-stu-id="5efd5-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="5efd5-115">Datový typ `result` je `String`.</span><span class="sxs-lookup"><span data-stu-id="5efd5-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="5efd5-116">Pokud jeden nebo oba výrazy vyhodnocení [nic](../../../visual-basic/language-reference/nothing.md) nebo mít hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType>, jsou považovány za řetězec s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="5efd5-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5efd5-117">`&` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="5efd5-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5efd5-118">Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="5efd5-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5efd5-119">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5efd5-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5efd5-120">Znak ampersand (&) dají použít také k identifikaci proměnné jako typ `Long`.</span><span class="sxs-lookup"><span data-stu-id="5efd5-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="5efd5-121">Další informace najdete v tématu [– znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="5efd5-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5efd5-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5efd5-122">Example</span></span>  
 <span data-ttu-id="5efd5-123">Tento příklad používá `&` operátor vynutit zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="5efd5-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="5efd5-124">Výsledkem je řetězcovou hodnotu představující zřetězení operandy dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="5efd5-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5efd5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="5efd5-125">See Also</span></span>  
 [<span data-ttu-id="5efd5-126">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="5efd5-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="5efd5-127">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="5efd5-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="5efd5-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5efd5-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="5efd5-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="5efd5-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="5efd5-130">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5efd5-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
