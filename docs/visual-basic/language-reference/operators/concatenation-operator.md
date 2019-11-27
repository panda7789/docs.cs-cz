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
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="15e3f-102">Operátor &amp; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15e3f-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="15e3f-103">Generuje řetězení řetězců dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="15e3f-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15e3f-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="15e3f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="15e3f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="15e3f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="15e3f-106">Required.</span></span> <span data-ttu-id="15e3f-107">Jakákoli `String` nebo proměnná `Object`.</span><span class="sxs-lookup"><span data-stu-id="15e3f-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="15e3f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="15e3f-108">Required.</span></span> <span data-ttu-id="15e3f-109">Libovolný výraz s datovým typem, který se rozšíří na `String`.</span><span class="sxs-lookup"><span data-stu-id="15e3f-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="15e3f-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="15e3f-110">Required.</span></span> <span data-ttu-id="15e3f-111">Libovolný výraz s datovým typem, který se rozšíří na `String`.</span><span class="sxs-lookup"><span data-stu-id="15e3f-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15e3f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15e3f-112">Remarks</span></span>  
 <span data-ttu-id="15e3f-113">Pokud datový typ `expression1` nebo `expression2` není `String`, ale rozšíří na `String`, je převeden na `String`.</span><span class="sxs-lookup"><span data-stu-id="15e3f-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="15e3f-114">Pokud se některý z datových typů nerozšíří na `String`, kompilátor vygeneruje chybu.</span><span class="sxs-lookup"><span data-stu-id="15e3f-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="15e3f-115">Datový typ `result` je `String`.</span><span class="sxs-lookup"><span data-stu-id="15e3f-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="15e3f-116">Pokud se jeden nebo oba výrazy vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo pokud mají hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType>, považují se za řetězec s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="15e3f-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15e3f-117">Operátor `&` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="15e3f-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="15e3f-118">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="15e3f-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="15e3f-119">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="15e3f-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15e3f-120">Znak ampersand (&) lze také použít k identifikaci proměnných jako typ `Long`.</span><span class="sxs-lookup"><span data-stu-id="15e3f-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="15e3f-121">Další informace naleznete v tématu [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="15e3f-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15e3f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="15e3f-122">Example</span></span>  
 <span data-ttu-id="15e3f-123">V tomto příkladu se používá operátor `&` k vynucení zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="15e3f-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="15e3f-124">Výsledkem je řetězcová hodnota představující zřetězení dvou řetězcových operandů.</span><span class="sxs-lookup"><span data-stu-id="15e3f-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="15e3f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15e3f-125">See also</span></span>

- [<span data-ttu-id="15e3f-126">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="15e3f-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="15e3f-127">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="15e3f-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="15e3f-128">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e3f-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="15e3f-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="15e3f-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="15e3f-130">Operátory zřetězení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e3f-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
