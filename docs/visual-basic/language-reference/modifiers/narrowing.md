---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838843"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="ffd57-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffd57-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="ffd57-103">Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí být schopný uchovat některou z možných hodnot původní třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="ffd57-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="ffd57-104">Pomocí klíčového slova zužující převod</span><span class="sxs-lookup"><span data-stu-id="ffd57-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="ffd57-105">Proces převodu musíte zadat `Public Shared` kromě `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="ffd57-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="ffd57-106">Zužující převody nejsou vždy v době spuštění úspěšné a může selhat nebo ztrátě dat se vám účtovat.</span><span class="sxs-lookup"><span data-stu-id="ffd57-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="ffd57-107">Mezi příklady patří `Long` k `Integer`, `String` k `Date`a základního typu odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="ffd57-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="ffd57-108">Tento poslední převod je zužující, protože základní typ nemusí obsahovat všechny členy odvozeného typu a proto není instance odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="ffd57-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="ffd57-109">Pokud `Option Strict` je `On`, využívání kódu musí používat `CType` pro všechny zužujících převodů.</span><span class="sxs-lookup"><span data-stu-id="ffd57-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="ffd57-110">`Narrowing` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="ffd57-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="ffd57-111">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="ffd57-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ffd57-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffd57-112">See also</span></span>

- [<span data-ttu-id="ffd57-113">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="ffd57-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ffd57-114">Widening</span><span class="sxs-lookup"><span data-stu-id="ffd57-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="ffd57-115">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="ffd57-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="ffd57-116">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="ffd57-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="ffd57-117">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="ffd57-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="ffd57-118">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="ffd57-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
