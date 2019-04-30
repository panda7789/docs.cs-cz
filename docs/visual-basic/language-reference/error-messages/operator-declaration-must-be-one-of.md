---
title: 'Operátor musí být jeden z: +,-, *,-, -, ^, &amp;, Like, Mod a, Or, Xor, Not, <<>>,, =, <>, <, < =, >, > =, CType, IsTrue nebo IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 4283547109ec312cc4fe07a054bbb8db3bff660f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946598"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="c8c2b-102">Operátor musí být jeden z: +,-, \*,\,/, ^, &amp;, Like, Mod a, Or, Xor, Not, \< \<, >>...</span><span class="sxs-lookup"><span data-stu-id="c8c2b-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="c8c2b-103">Je možné deklarovat pouze operátor, který opravňuje k přetížení.</span><span class="sxs-lookup"><span data-stu-id="c8c2b-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="c8c2b-104">V následující tabulce jsou uvedeny operátory, které je možné deklarovat.</span><span class="sxs-lookup"><span data-stu-id="c8c2b-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="c8c2b-105">Type</span><span class="sxs-lookup"><span data-stu-id="c8c2b-105">Type</span></span>|<span data-ttu-id="c8c2b-106">Operátory</span><span class="sxs-lookup"><span data-stu-id="c8c2b-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="c8c2b-107">Unární</span><span class="sxs-lookup"><span data-stu-id="c8c2b-107">Unary</span></span>|<span data-ttu-id="c8c2b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="c8c2b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="c8c2b-109">binární</span><span class="sxs-lookup"><span data-stu-id="c8c2b-109">Binary</span></span>|<span data-ttu-id="c8c2b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="c8c2b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="c8c2b-111">Převod (unární)</span><span class="sxs-lookup"><span data-stu-id="c8c2b-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="c8c2b-112">Všimněte si, že `=` operátor v binárním seznamu je relační operátor, operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="c8c2b-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="c8c2b-113">**ID chyby:** BC33000</span><span class="sxs-lookup"><span data-stu-id="c8c2b-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8c2b-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c8c2b-114">To correct this error</span></span>  
  
1. <span data-ttu-id="c8c2b-115">Vyberte operátor ze sady přetížitelné operátory.</span><span class="sxs-lookup"><span data-stu-id="c8c2b-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="c8c2b-116">Pokud potřebujete funkce přetížení operátor nelze přetížit přímo, vytvořte `Function` proceduru, která mají příslušné parametry a vrátí odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c8c2b-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c2b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8c2b-117">See also</span></span>

- [<span data-ttu-id="c8c2b-118">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="c8c2b-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c8c2b-119">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="c8c2b-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="c8c2b-120">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="c8c2b-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="c8c2b-121">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="c8c2b-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="c8c2b-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="c8c2b-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
