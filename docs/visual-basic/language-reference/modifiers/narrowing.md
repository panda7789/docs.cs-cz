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
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362356"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="e32f9-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e32f9-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="e32f9-103">Označuje, že operátor převodu ( `CType` ) převede třídu nebo strukturu na typ, který nemusí být schopný uchovat některé z možných hodnot původní třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="e32f9-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="e32f9-104">Převod s klíčovým slovem zúžení</span><span class="sxs-lookup"><span data-stu-id="e32f9-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="e32f9-105">Postup převodu musí být `Public Shared` kromě `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="e32f9-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="e32f9-106">Zužující převody nejsou vždycky úspěšné v době běhu a můžou selhat nebo může dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="e32f9-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="e32f9-107">Příklady jsou `Long` `Integer` , `String` do a `Date` základní typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="e32f9-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="e32f9-108">Tento poslední převod je zúžený, protože základní typ nemusí obsahovat všechny členy odvozeného typu, a proto není instancí odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="e32f9-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="e32f9-109">V takovém případě `Option Strict` `On` musí kód náročné použít `CType` pro všechny zužující převody.</span><span class="sxs-lookup"><span data-stu-id="e32f9-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="e32f9-110">`Narrowing`Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="e32f9-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="e32f9-111">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="e32f9-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e32f9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e32f9-112">See also</span></span>

- [<span data-ttu-id="e32f9-113">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="e32f9-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="e32f9-114">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="e32f9-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="e32f9-115">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="e32f9-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e32f9-116">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="e32f9-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="e32f9-117">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="e32f9-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="e32f9-118">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="e32f9-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
