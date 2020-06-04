---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410500"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="76cf8-102">Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76cf8-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="76cf8-103">Proměnnou [datového typu objektu](../../../language-reference/data-types/object-data-type.md) deklarujete zadáním `As Object` v [příkazu Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="76cf8-103">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="76cf8-104">Objektu této proměnné přiřadíte umístěním objektu za znaménko rovná se ( `=` ) v příkazu přiřazení nebo v klauzuli inicializace.</span><span class="sxs-lookup"><span data-stu-id="76cf8-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="76cf8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="76cf8-105">Example</span></span>

<span data-ttu-id="76cf8-106">Následující příklad deklaruje `Object` proměnnou a přiřadí k ní aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="76cf8-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="76cf8-107">Můžete zkombinovat deklaraci a přiřazení inicializací proměnné jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="76cf8-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="76cf8-108">Následující příklad je ekvivalentní k předchozímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="76cf8-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="76cf8-109">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="76cf8-109">Compile the code</span></span>

<span data-ttu-id="76cf8-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="76cf8-110">This example requires:</span></span>

- <span data-ttu-id="76cf8-111">Odkaz na <xref:System> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="76cf8-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="76cf8-112">Třída, struktura nebo modul, do kterého se má příkaz Vložit `Dim` .</span><span class="sxs-lookup"><span data-stu-id="76cf8-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="76cf8-113">Postup pro vložení příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="76cf8-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="76cf8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="76cf8-114">See also</span></span>

- [<span data-ttu-id="76cf8-115">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="76cf8-115">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="76cf8-116">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="76cf8-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="76cf8-117">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="76cf8-117">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="76cf8-118">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="76cf8-118">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="76cf8-119">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="76cf8-119">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="76cf8-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="76cf8-120">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="76cf8-121">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="76cf8-121">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
