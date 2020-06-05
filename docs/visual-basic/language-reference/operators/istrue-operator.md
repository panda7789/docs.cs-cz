---
title: IsTrue – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370645"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="8864f-102">IsTrue – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8864f-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="8864f-103">Určuje, zda je výraz `True` .</span><span class="sxs-lookup"><span data-stu-id="8864f-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="8864f-104">Nemůžete volat `IsTrue` explicitně v kódu, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `OrElse` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="8864f-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="8864f-105">Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v `OrElse` klauzuli, je nutné definovat `IsTrue` v této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="8864f-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="8864f-106">Kompilátor považuje `IsTrue` operátory a `IsFalse` za *spárované páry*.</span><span class="sxs-lookup"><span data-stu-id="8864f-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="8864f-107">To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.</span><span class="sxs-lookup"><span data-stu-id="8864f-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="8864f-108">Použití kompilátoru true</span><span class="sxs-lookup"><span data-stu-id="8864f-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="8864f-109">Pokud jste definovali třídu nebo strukturu, můžete použít proměnnou daného typu v `For` `If` příkazu,, `Else If` nebo `While` nebo v `When` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8864f-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="8864f-110">Pokud to uděláte, kompilátor vyžaduje operátor, který převede typ na hodnotu, aby mohl `Boolean` otestovat podmínku.</span><span class="sxs-lookup"><span data-stu-id="8864f-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="8864f-111">Vyhledá vhodný operátor v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="8864f-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="8864f-112">Rozšiřující operátor převodu z vaší třídy nebo struktury na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8864f-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="8864f-113">Rozšiřující operátor převodu z vaší třídy nebo struktury na `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="8864f-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="8864f-114">`IsTrue`Operátor pro třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="8864f-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="8864f-115">Zužující převod na `Boolean?` , který nezahrnuje převod z `Boolean` na `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="8864f-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="8864f-116">Zúžený operátor převodu z vaší třídy nebo struktury na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8864f-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="8864f-117">Pokud jste nedefinovali převod na `Boolean` `IsTrue` operátor nebo, kompilátor signalizuje chybu.</span><span class="sxs-lookup"><span data-stu-id="8864f-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8864f-118">`IsTrue`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má jeho operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8864f-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="8864f-119">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="8864f-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8864f-120">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8864f-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8864f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="8864f-121">Example</span></span>  
 <span data-ttu-id="8864f-122">Následující příklad kódu definuje obrys struktury, která obsahuje definice pro `IsFalse` `IsTrue` operátory a.</span><span class="sxs-lookup"><span data-stu-id="8864f-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="8864f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="8864f-123">See also</span></span>

- [<span data-ttu-id="8864f-124">IsFalse – operátor</span><span class="sxs-lookup"><span data-stu-id="8864f-124">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="8864f-125">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="8864f-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8864f-126">OrElse – operátor</span><span class="sxs-lookup"><span data-stu-id="8864f-126">OrElse Operator</span></span>](orelse-operator.md)
