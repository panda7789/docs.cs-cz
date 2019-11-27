---
title: Narrowing
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
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351479"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="3c438-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c438-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="3c438-103">Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí být schopný uchovat některé z možných hodnot původní třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3c438-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="3c438-104">Převod s klíčovým slovem zúžení</span><span class="sxs-lookup"><span data-stu-id="3c438-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="3c438-105">Postup převodu musí kromě `Narrowing`zadat `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="3c438-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="3c438-106">Zužující převody nejsou vždycky úspěšné v době běhu a můžou selhat nebo může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="3c438-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="3c438-107">Příklady jsou `Long` pro `Integer`, `String` na `Date`a základní typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="3c438-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="3c438-108">Tento poslední převod je zúžený, protože základní typ nemusí obsahovat všechny členy odvozeného typu, a proto není instancí odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="3c438-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="3c438-109">Pokud je `Option Strict` `On`, musí používat kód `CType` pro všechny zužující převody.</span><span class="sxs-lookup"><span data-stu-id="3c438-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="3c438-110">Klíčové slovo `Narrowing` lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="3c438-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="3c438-111">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="3c438-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c438-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c438-112">See also</span></span>

- [<span data-ttu-id="3c438-113">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="3c438-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="3c438-114">Widening</span><span class="sxs-lookup"><span data-stu-id="3c438-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="3c438-115">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="3c438-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3c438-116">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="3c438-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="3c438-117">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="3c438-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="3c438-118">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="3c438-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
