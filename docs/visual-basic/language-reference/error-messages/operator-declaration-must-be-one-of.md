---
title: 'Operátor musí být jeden z: +,-, *,-, -, ^, &amp;, Like, Mod a, Or, Xor, Not, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue nebo IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: f32935dd4aaccd3040655b418badc13c1988c1b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622270"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="18a75-102">Operátor musí být jeden z: +,-, \*,\,/, ^, &amp;, Like, Mod a, Or, Xor, Not, &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="18a75-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="18a75-103">Je možné deklarovat pouze operátor, který opravňuje k přetížení.</span><span class="sxs-lookup"><span data-stu-id="18a75-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="18a75-104">V následující tabulce jsou uvedeny operátory, které je možné deklarovat.</span><span class="sxs-lookup"><span data-stu-id="18a75-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="18a75-105">Typ</span><span class="sxs-lookup"><span data-stu-id="18a75-105">Type</span></span>|<span data-ttu-id="18a75-106">Operátory</span><span class="sxs-lookup"><span data-stu-id="18a75-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="18a75-107">Unární</span><span class="sxs-lookup"><span data-stu-id="18a75-107">Unary</span></span>|<span data-ttu-id="18a75-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="18a75-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="18a75-109">binární</span><span class="sxs-lookup"><span data-stu-id="18a75-109">Binary</span></span>|<span data-ttu-id="18a75-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="18a75-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="18a75-111">Převod (unární)</span><span class="sxs-lookup"><span data-stu-id="18a75-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="18a75-112">Všimněte si, že `=` operátor v binárním seznamu je relační operátor, operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="18a75-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="18a75-113">**ID chyby:** BC33000</span><span class="sxs-lookup"><span data-stu-id="18a75-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18a75-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="18a75-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="18a75-115">Vyberte operátor ze sady přetížitelné operátory.</span><span class="sxs-lookup"><span data-stu-id="18a75-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="18a75-116">Pokud potřebujete funkce přetížení operátor nelze přetížit přímo, vytvořte `Function` proceduru, která mají příslušné parametry a vrátí odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="18a75-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a75-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18a75-117">See also</span></span>
- [<span data-ttu-id="18a75-118">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="18a75-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="18a75-119">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="18a75-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="18a75-120">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="18a75-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="18a75-121">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="18a75-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="18a75-122">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="18a75-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
