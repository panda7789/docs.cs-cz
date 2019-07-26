---
title: Výraz je hodnota, a proto nemůže být cílem přiřazení.
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513039"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="9b805-102">Výraz je hodnota, a proto nemůže být cílem přiřazení.</span><span class="sxs-lookup"><span data-stu-id="9b805-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="9b805-103">Příkaz se pokusí přiřadit hodnotu k výrazu.</span><span class="sxs-lookup"><span data-stu-id="9b805-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="9b805-104">V době běhu můžete přiřadit hodnotu pouze k zapisovatelné proměnné, vlastnosti nebo prvku Array.</span><span class="sxs-lookup"><span data-stu-id="9b805-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="9b805-105">Následující příklad ukazuje, jak k této chybě může dojít.</span><span class="sxs-lookup"><span data-stu-id="9b805-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="9b805-106">Podobné příklady mohou být použity pro vlastnosti a prvky pole.</span><span class="sxs-lookup"><span data-stu-id="9b805-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="9b805-107">**Nepřímý přístup.**</span><span class="sxs-lookup"><span data-stu-id="9b805-107">**Indirect Access.**</span></span> <span data-ttu-id="9b805-108">Tuto chybu může generovat také nepřímý přístup prostřednictvím typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b805-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="9b805-109">Vezměte v úvahu následující příklad kódu, který se pokusí nastavit hodnotu <xref:System.Drawing.Point> přímým přístupem prostřednictvím. <xref:System.Windows.Forms.Control.Location%2A></span><span class="sxs-lookup"><span data-stu-id="9b805-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="9b805-110">Poslední příkaz v předchozím příkladu se nezdařil, protože vytváří pouze dočasné přidělení pro <xref:System.Drawing.Point> strukturu vrácenou <xref:System.Windows.Forms.Control.Location%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="9b805-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="9b805-111">Struktura je typ hodnoty a dočasná struktura není po spuštění příkazu uchována.</span><span class="sxs-lookup"><span data-stu-id="9b805-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="9b805-112">Problém je vyřešen deklarováním a použitím proměnné pro <xref:System.Windows.Forms.Control.Location%2A>, která vytvoří <xref:System.Drawing.Point> pro strukturu trvalé přidělení.</span><span class="sxs-lookup"><span data-stu-id="9b805-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="9b805-113">Následující příklad ukazuje kód, který může nahradit poslední příkaz v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9b805-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="9b805-114">**ID chyby:** BC30068</span><span class="sxs-lookup"><span data-stu-id="9b805-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9b805-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9b805-115">To correct this error</span></span>

- <span data-ttu-id="9b805-116">Pokud příkaz přiřadí hodnotu výrazu, nahraďte výraz jedinou zapisovatelnou proměnnou, vlastností nebo elementem pole.</span><span class="sxs-lookup"><span data-stu-id="9b805-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="9b805-117">Pokud příkaz vytvoří nepřímý přístup prostřednictvím typu hodnoty (obvykle struktury), vytvořte proměnnou pro uchování typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b805-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="9b805-118">Přiřaďte proměnné příslušnou strukturu (nebo jiný typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="9b805-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="9b805-119">Pro přístup k vlastnosti použijte proměnnou k přiřazení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9b805-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b805-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b805-120">See also</span></span>

- [<span data-ttu-id="9b805-121">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="9b805-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="9b805-122">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9b805-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="9b805-123">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="9b805-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
