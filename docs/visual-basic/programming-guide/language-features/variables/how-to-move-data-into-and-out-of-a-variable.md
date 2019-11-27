---
title: 'Postupy: Přesun dat do proměnné a z proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bc5a7377a5e2e4c7ebe7291fd5f0093c4d6e996d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346892"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="b6e09-102">Postupy: Přesun dat do proměnné a z proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6e09-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="b6e09-103">Hodnotu v proměnné uložíte tak, že na levou stranu příkazu přiřazení umístíte název proměnné.</span><span class="sxs-lookup"><span data-stu-id="b6e09-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="b6e09-104">Vložení dat do proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-104">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="b6e09-105">Uložení hodnoty do proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-105">To store a value in a variable</span></span>

- <span data-ttu-id="b6e09-106">Použijte název proměnné na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b6e09-106">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="b6e09-107">Následující příklad nastaví hodnotu proměnné `alpha`.</span><span class="sxs-lookup"><span data-stu-id="b6e09-107">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="b6e09-108">Hodnota generovaná na pravé straně příkazu přiřazení je uložena v proměnné.</span><span class="sxs-lookup"><span data-stu-id="b6e09-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="b6e09-109">Získávání dat z proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-109">Getting Data from a Variable</span></span>

<span data-ttu-id="b6e09-110">Načtěte hodnotu proměnné zahrnutím názvu proměnné do výrazu.</span><span class="sxs-lookup"><span data-stu-id="b6e09-110">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="b6e09-111">Načtení hodnoty z proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-111">To retrieve a value from a variable</span></span>

- <span data-ttu-id="b6e09-112">Použijte název proměnné ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="b6e09-112">Use the variable name in an expression.</span></span> <span data-ttu-id="b6e09-113">Proměnnou můžete použít všude, kde můžete použít konstantu nebo literál, s výjimkou výrazu, který definuje hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="b6e09-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="b6e09-114">\-nebo-</span><span class="sxs-lookup"><span data-stu-id="b6e09-114">\-or-</span></span>

- <span data-ttu-id="b6e09-115">Použijte název proměnné za znaménkem EQUAL (`=`) v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b6e09-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="b6e09-116">Následující příklad přečte hodnotu proměnné `startValue` a poté používá hodnotu proměnné `counter` ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="b6e09-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="b6e09-117">Hodnota proměnné se účastní ve výrazu stejně jako konstanta a pak je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b6e09-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6e09-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6e09-118">See also</span></span>

- [<span data-ttu-id="b6e09-119">Proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="b6e09-120">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="b6e09-121">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="b6e09-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
