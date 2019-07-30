---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k němu v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630872"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="000f9-102">Postupy: Deklarace objektové proměnné a přiřazení objektu k němu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="000f9-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="000f9-103">Proměnnou [datového typu objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) deklarujete zadáním `As Object` v [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="000f9-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="000f9-104">Objektu této proměnné přiřadíte umístěním objektu za znaménko rovná se (`=`) v příkazu přiřazení nebo v klauzuli inicializace.</span><span class="sxs-lookup"><span data-stu-id="000f9-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="000f9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="000f9-105">Example</span></span>

<span data-ttu-id="000f9-106">Následující příklad deklaruje `Object` proměnnou a přiřadí k ní aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="000f9-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="000f9-107">Můžete zkombinovat deklaraci a přiřazení inicializací proměnné jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="000f9-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="000f9-108">Následující příklad je ekvivalentní k předchozímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="000f9-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="000f9-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="000f9-109">Compiling the Code</span></span>

<span data-ttu-id="000f9-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="000f9-110">This example requires:</span></span>

- <span data-ttu-id="000f9-111">Odkaz na <xref:System> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="000f9-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="000f9-112">Třída, struktura nebo modul, do kterého se má `Dim` příkaz Vložit.</span><span class="sxs-lookup"><span data-stu-id="000f9-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="000f9-113">Postup pro vložení příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="000f9-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="000f9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="000f9-114">See also</span></span>

- [<span data-ttu-id="000f9-115">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="000f9-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="000f9-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="000f9-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="000f9-117">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="000f9-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="000f9-118">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="000f9-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="000f9-119">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="000f9-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="000f9-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="000f9-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="000f9-121">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="000f9-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
