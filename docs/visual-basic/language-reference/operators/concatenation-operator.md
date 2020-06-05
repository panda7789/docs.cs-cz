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
ms.openlocfilehash: d778c0c99d6d074fe8b73aaf3660074643e7e136
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371606"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="38c5b-102">&amp;– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38c5b-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="38c5b-103">Generuje řetězení řetězců dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="38c5b-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38c5b-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="38c5b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="38c5b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="38c5b-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="38c5b-106">Required.</span></span> <span data-ttu-id="38c5b-107">Jakékoli `String` `Object` proměnné nebo.</span><span class="sxs-lookup"><span data-stu-id="38c5b-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="38c5b-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="38c5b-108">Required.</span></span> <span data-ttu-id="38c5b-109">Libovolný výraz s datovým typem, který se rozšiřuje na `String` .</span><span class="sxs-lookup"><span data-stu-id="38c5b-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="38c5b-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="38c5b-110">Required.</span></span> <span data-ttu-id="38c5b-111">Libovolný výraz s datovým typem, který se rozšiřuje na `String` .</span><span class="sxs-lookup"><span data-stu-id="38c5b-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38c5b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38c5b-112">Remarks</span></span>  
 <span data-ttu-id="38c5b-113">Pokud datový typ nebo není `expression1` `expression2` `String` , ale rozšiřuje se na `String` , je převeden na `String` .</span><span class="sxs-lookup"><span data-stu-id="38c5b-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="38c5b-114">Pokud se některý z datových typů nerozšíří na `String` , kompilátor vygeneruje chybu.</span><span class="sxs-lookup"><span data-stu-id="38c5b-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="38c5b-115">Datový typ `result` je `String` .</span><span class="sxs-lookup"><span data-stu-id="38c5b-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="38c5b-116">Pokud se jeden nebo oba výrazy vyhodnotí jako [Nothing](../nothing.md) nebo pokud mají hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType> , považují se za řetězec s hodnotou "".</span><span class="sxs-lookup"><span data-stu-id="38c5b-116">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38c5b-117">`&`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="38c5b-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="38c5b-118">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="38c5b-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="38c5b-119">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="38c5b-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38c5b-120">Znak ampersand (&) lze také použít k identifikaci proměnných jako typu `Long` .</span><span class="sxs-lookup"><span data-stu-id="38c5b-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="38c5b-121">Další informace naleznete v tématu [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="38c5b-121">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38c5b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="38c5b-122">Example</span></span>  
 <span data-ttu-id="38c5b-123">V tomto příkladu se používá `&` operátor k vynucení zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="38c5b-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="38c5b-124">Výsledkem je řetězcová hodnota představující zřetězení dvou řetězcových operandů.</span><span class="sxs-lookup"><span data-stu-id="38c5b-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="38c5b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="38c5b-125">See also</span></span>

- [<span data-ttu-id="38c5b-126">&= – operátor</span><span class="sxs-lookup"><span data-stu-id="38c5b-126">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="38c5b-127">Operátory řetězení</span><span class="sxs-lookup"><span data-stu-id="38c5b-127">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="38c5b-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38c5b-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="38c5b-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="38c5b-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="38c5b-130">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38c5b-130">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
