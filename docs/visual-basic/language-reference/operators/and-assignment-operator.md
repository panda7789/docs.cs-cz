---
title: '&amp;= – Operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371983"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="2e561-102">&amp;= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e561-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="2e561-103">Zřetězí `String` výraz na `String` proměnnou nebo vlastnost a přiřadí výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2e561-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e561-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e561-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2e561-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2e561-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2e561-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="2e561-106">Required.</span></span> <span data-ttu-id="2e561-107">Jakákoli `String` proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2e561-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="2e561-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="2e561-108">Required.</span></span> <span data-ttu-id="2e561-109">Libovolný `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="2e561-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e561-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e561-110">Remarks</span></span>  
 <span data-ttu-id="2e561-111">Element na levé straně `&=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="2e561-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2e561-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="2e561-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="2e561-113">`&=`Operátor zřetězí `String` výraz na základě jeho práva na `String` proměnnou nebo vlastnost vlevo a výsledek přiřadí proměnné nebo vlastnosti nalevo.</span><span class="sxs-lookup"><span data-stu-id="2e561-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2e561-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="2e561-114">Overloading</span></span>  
 <span data-ttu-id="2e561-115">[Operátor&](concatenation-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="2e561-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2e561-116">Přetížení `&` operátoru ovlivňuje chování `&=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="2e561-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="2e561-117">Pokud váš kód používá `&=` pro třídu nebo strukturu, která je přetížena `&` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="2e561-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2e561-118">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2e561-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e561-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e561-119">Example</span></span>  
 <span data-ttu-id="2e561-120">Následující příklad používá `&=` operátor ke zřetězení dvou `String` proměnných a přiřazení výsledku k první proměnné.</span><span class="sxs-lookup"><span data-stu-id="2e561-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2e561-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e561-121">See also</span></span>

- [<span data-ttu-id="2e561-122">Operátor&</span><span class="sxs-lookup"><span data-stu-id="2e561-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="2e561-123">+ = – Operátor</span><span class="sxs-lookup"><span data-stu-id="2e561-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="2e561-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="2e561-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="2e561-125">Operátory řetězení</span><span class="sxs-lookup"><span data-stu-id="2e561-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="2e561-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e561-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="2e561-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="2e561-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="2e561-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="2e561-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
