---
title: 'Postupy: Přesun dat do a z proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818529"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="0d719-102">Postupy: Přesun dat do a z proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d719-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="0d719-103">Uložení hodnoty do proměnné tak, že vložíte název proměnné na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0d719-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="0d719-104">Ukládání dat do proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="0d719-105">K uložení hodnoty v proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="0d719-106">Použijte název proměnné na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0d719-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="0d719-107">Následující příklad nastaví hodnotu proměnné `alpha`.</span><span class="sxs-lookup"><span data-stu-id="0d719-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="0d719-108">Hodnota generovaná na pravé straně příkazu přiřazení je uložen v proměnné.</span><span class="sxs-lookup"><span data-stu-id="0d719-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="0d719-109">Získání dat z proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="0d719-110">Hodnota proměnné načtete zahrnutím název proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="0d719-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="0d719-111">Načíst hodnotu z proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="0d719-112">Použijte název proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="0d719-112">Use the variable name in an expression.</span></span> <span data-ttu-id="0d719-113">Proměnnou můžete použít kdekoli můžete použít konstanta nebo literál, s výjimkou ve výrazu, který definuje hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="0d719-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="0d719-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="0d719-114">-or-</span></span>  
  
-   <span data-ttu-id="0d719-115">Použijte název proměnné po rovnosti (`=`) Přihlaste se příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0d719-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="0d719-116">Následující příklad přečte hodnotu proměnné `startValue` a použije se hodnota proměnné `counter` ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="0d719-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="0d719-117">Hodnota proměnné podílí na výraz, stejně jako by konstantu, a pak je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0d719-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d719-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d719-118">See also</span></span>

- [<span data-ttu-id="0d719-119">Proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="0d719-120">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="0d719-121">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="0d719-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
