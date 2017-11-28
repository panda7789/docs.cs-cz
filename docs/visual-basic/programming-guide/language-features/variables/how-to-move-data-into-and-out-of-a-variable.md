---
title: "Postupy: Přesun dat do proměnné a z proměnné (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="550e8-102">Postupy: Přesun dat do proměnné a z proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550e8-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="550e8-103">Hodnotu můžete uložit jako proměnnou umístěním název proměnné na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="550e8-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="550e8-104">Ukládání dat do proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="550e8-105">K uložení hodnotu do proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="550e8-106">Použijte název proměnné na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="550e8-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="550e8-107">Následující příklad nastaví hodnotu proměnné `alpha`.</span><span class="sxs-lookup"><span data-stu-id="550e8-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="550e8-108">Hodnota generovaná na pravé straně přiřazení příkazu je uložené v proměnné.</span><span class="sxs-lookup"><span data-stu-id="550e8-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="550e8-109">Získání dat z proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="550e8-110">Hodnota proměnné můžete načíst tak, že včetně názvu proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="550e8-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="550e8-111">K načtení hodnoty z proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="550e8-112">Použijte název proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="550e8-112">Use the variable name in an expression.</span></span> <span data-ttu-id="550e8-113">Proměnnou můžete použít kdekoli můžete použít konstantu nebo literál, s výjimkou v výraz, který definuje hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="550e8-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="550e8-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="550e8-114">-or-</span></span>  
  
-   <span data-ttu-id="550e8-115">Použijte název proměnné následující rovno (`=`) přihlásit příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="550e8-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="550e8-116">Následující příklad načte hodnotu proměnné `startValue` a pak používá hodnotu proměnné `counter` ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="550e8-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="550e8-117">Hodnota proměnné se účastní výraz stejně, jako by konstanta, a pak je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="550e8-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="550e8-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="550e8-118">See Also</span></span>  
 [<span data-ttu-id="550e8-119">Proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="550e8-120">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="550e8-121">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="550e8-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
