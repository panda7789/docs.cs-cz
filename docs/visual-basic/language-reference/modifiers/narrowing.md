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
ms.openlocfilehash: 54a18d0cc10e42829b48b0ef75bb77ab0d47b45f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597455"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="6f1ec-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f1ec-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="6f1ec-103">Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí obsahovat některé možné hodnoty z původní třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="6f1ec-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="6f1ec-104">Převádění s Narrowing – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="6f1ec-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="6f1ec-105">Musíte zadat procesu převodu `Public Shared` kromě `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="6f1ec-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="6f1ec-106">Zužující převody není vždy úspěch v době běhu a může selhat nebo dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="6f1ec-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="6f1ec-107">Příklady `Long` k `Integer`, `String` k `Date`a základní typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="6f1ec-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="6f1ec-108">Tento poslední převod je zužující, protože základní typ nemusí obsahovat všechny členy odvozený typ a proto není instance odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="6f1ec-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="6f1ec-109">Pokud `Option Strict` je `On`, využívání kód musíte použít `CType` pro všechny zužující převody.</span><span class="sxs-lookup"><span data-stu-id="6f1ec-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="6f1ec-110">`Narrowing` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="6f1ec-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="6f1ec-111">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="6f1ec-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f1ec-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f1ec-112">See Also</span></span>  
 [<span data-ttu-id="6f1ec-113">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="6f1ec-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="6f1ec-114">Widening</span><span class="sxs-lookup"><span data-stu-id="6f1ec-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="6f1ec-115">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="6f1ec-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="6f1ec-116">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="6f1ec-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="6f1ec-117">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="6f1ec-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="6f1ec-118">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="6f1ec-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
