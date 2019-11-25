---
title: 'How to: Declare an Object Variable and Assign an Object to It'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352906"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="d72e5-102">Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d72e5-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="d72e5-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d72e5-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="d72e5-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span><span class="sxs-lookup"><span data-stu-id="d72e5-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="d72e5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d72e5-105">Example</span></span>

<span data-ttu-id="d72e5-106">The following example declares an `Object` variable and assigns the current instance to it.</span><span class="sxs-lookup"><span data-stu-id="d72e5-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="d72e5-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span><span class="sxs-lookup"><span data-stu-id="d72e5-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="d72e5-108">The following example is equivalent to the preceding example.</span><span class="sxs-lookup"><span data-stu-id="d72e5-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="d72e5-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d72e5-109">Compiling the Code</span></span>

<span data-ttu-id="d72e5-110">This example requires:</span><span class="sxs-lookup"><span data-stu-id="d72e5-110">This example requires:</span></span>

- <span data-ttu-id="d72e5-111">A reference to the <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="d72e5-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="d72e5-112">A class, structure, or module in which to put the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="d72e5-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="d72e5-113">A procedure in which to put the assignment statement.</span><span class="sxs-lookup"><span data-stu-id="d72e5-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="d72e5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d72e5-114">See also</span></span>

- [<span data-ttu-id="d72e5-115">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="d72e5-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="d72e5-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="d72e5-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="d72e5-117">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="d72e5-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="d72e5-118">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="d72e5-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="d72e5-119">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="d72e5-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="d72e5-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="d72e5-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d72e5-121">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="d72e5-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
