---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="c118e-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c118e-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="c118e-103">Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí obsahovat některé možné hodnoty z původní třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="c118e-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="c118e-104">Převádění s Narrowing – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="c118e-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="c118e-105">Musíte zadat procesu převodu `Public Shared` kromě `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="c118e-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="c118e-106">Zužující převody není vždy úspěch v době běhu a může selhat nebo dojít ke ztrátě dat.</span><span class="sxs-lookup"><span data-stu-id="c118e-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="c118e-107">Příklady `Long` k `Integer`, `String` k `Date`a základní typ pro odvozený typ.</span><span class="sxs-lookup"><span data-stu-id="c118e-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="c118e-108">Tento poslední převod je zužující, protože základní typ nemusí obsahovat všechny členy odvozený typ a proto není instance odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="c118e-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="c118e-109">Pokud `Option Strict` je `On`, využívání kód musíte použít `CType` pro všechny zužující převody.</span><span class="sxs-lookup"><span data-stu-id="c118e-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="c118e-110">`Narrowing` – Klíčové slovo lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="c118e-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="c118e-111">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="c118e-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c118e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c118e-112">See Also</span></span>  
 [<span data-ttu-id="c118e-113">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="c118e-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="c118e-114">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="c118e-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="c118e-115">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="c118e-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="c118e-116">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="c118e-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="c118e-117">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="c118e-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="c118e-118">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="c118e-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
