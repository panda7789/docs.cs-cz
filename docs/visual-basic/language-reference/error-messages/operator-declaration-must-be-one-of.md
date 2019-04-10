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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299186"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="3dda6-102">Operátor musí být jeden z: +,-, \*,\,/, ^, &amp;, Like, Mod a, Or, Xor, Not, \< \<, >>...</span><span class="sxs-lookup"><span data-stu-id="3dda6-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="3dda6-103">Je možné deklarovat pouze operátor, který opravňuje k přetížení.</span><span class="sxs-lookup"><span data-stu-id="3dda6-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="3dda6-104">V následující tabulce jsou uvedeny operátory, které je možné deklarovat.</span><span class="sxs-lookup"><span data-stu-id="3dda6-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="3dda6-105">Type</span><span class="sxs-lookup"><span data-stu-id="3dda6-105">Type</span></span>|<span data-ttu-id="3dda6-106">Operátory</span><span class="sxs-lookup"><span data-stu-id="3dda6-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="3dda6-107">Unární</span><span class="sxs-lookup"><span data-stu-id="3dda6-107">Unary</span></span>|`+`<span data-ttu-id="3dda6-108">, `-`, `IsFalse`, `IsTrue`,</span><span class="sxs-lookup"><span data-stu-id="3dda6-108">, `-`, `IsFalse`, `IsTrue`,</span></span> `Not`|  
|<span data-ttu-id="3dda6-109">binární</span><span class="sxs-lookup"><span data-stu-id="3dda6-109">Binary</span></span>|`+`<span data-ttu-id="3dda6-110">, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`,</span><span class="sxs-lookup"><span data-stu-id="3dda6-110">, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`,</span></span> `Xor`|  
|<span data-ttu-id="3dda6-111">Převod (unární)</span><span class="sxs-lookup"><span data-stu-id="3dda6-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="3dda6-112">Všimněte si, že `=` operátor v binárním seznamu je relační operátor, operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3dda6-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="3dda6-113">**ID chyby:** BC33000</span><span class="sxs-lookup"><span data-stu-id="3dda6-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3dda6-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3dda6-114">To correct this error</span></span>  
  
1. <span data-ttu-id="3dda6-115">Vyberte operátor ze sady přetížitelné operátory.</span><span class="sxs-lookup"><span data-stu-id="3dda6-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="3dda6-116">Pokud potřebujete funkce přetížení operátor nelze přetížit přímo, vytvořte `Function` proceduru, která mají příslušné parametry a vrátí odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3dda6-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dda6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dda6-117">See also</span></span>

- [<span data-ttu-id="3dda6-118">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="3dda6-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="3dda6-119">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="3dda6-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="3dda6-120">Postupy: Definování operátoru</span><span class="sxs-lookup"><span data-stu-id="3dda6-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="3dda6-121">Postupy: Definování operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="3dda6-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="3dda6-122">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="3dda6-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
