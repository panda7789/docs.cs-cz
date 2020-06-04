---
title: Výraz je hodnota, a proto nemůže být cílem přiřazení.
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409504"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="e380b-102">Výraz je hodnota, a proto nemůže být cílem přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e380b-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="e380b-103">Příkaz se pokusí přiřadit hodnotu k výrazu.</span><span class="sxs-lookup"><span data-stu-id="e380b-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="e380b-104">V době běhu můžete přiřadit hodnotu pouze k zapisovatelné proměnné, vlastnosti nebo prvku Array.</span><span class="sxs-lookup"><span data-stu-id="e380b-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="e380b-105">Následující příklad ukazuje, jak k této chybě může dojít.</span><span class="sxs-lookup"><span data-stu-id="e380b-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="e380b-106">Podobné příklady mohou být použity pro vlastnosti a prvky pole.</span><span class="sxs-lookup"><span data-stu-id="e380b-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="e380b-107">**Nepřímý přístup.**</span><span class="sxs-lookup"><span data-stu-id="e380b-107">**Indirect Access.**</span></span> <span data-ttu-id="e380b-108">Tuto chybu může generovat také nepřímý přístup prostřednictvím typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e380b-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="e380b-109">Vezměte v úvahu následující příklad kódu, který se pokusí nastavit hodnotu přímým <xref:System.Drawing.Point> přístupem prostřednictvím <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="e380b-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="e380b-110">Poslední příkaz v předchozím příkladu se nezdařil, protože vytváří pouze dočasné přidělení pro <xref:System.Drawing.Point> strukturu vrácenou <xref:System.Windows.Forms.Control.Location%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="e380b-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="e380b-111">Struktura je typ hodnoty a dočasná struktura není po spuštění příkazu uchována.</span><span class="sxs-lookup"><span data-stu-id="e380b-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="e380b-112">Problém je vyřešen deklarováním a použitím proměnné pro <xref:System.Windows.Forms.Control.Location%2A> , která vytvoří pro strukturu trvalé přidělení <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="e380b-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="e380b-113">Následující příklad ukazuje kód, který může nahradit poslední příkaz v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e380b-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="e380b-114">**ID chyby:** BC30068</span><span class="sxs-lookup"><span data-stu-id="e380b-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e380b-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e380b-115">To correct this error</span></span>

- <span data-ttu-id="e380b-116">Pokud příkaz přiřadí hodnotu výrazu, nahraďte výraz jedinou zapisovatelnou proměnnou, vlastností nebo elementem pole.</span><span class="sxs-lookup"><span data-stu-id="e380b-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="e380b-117">Pokud příkaz vytvoří nepřímý přístup prostřednictvím typu hodnoty (obvykle struktury), vytvořte proměnnou pro uchování typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e380b-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="e380b-118">Přiřaďte proměnné příslušnou strukturu (nebo jiný typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="e380b-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="e380b-119">Pro přístup k vlastnosti použijte proměnnou k přiřazení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e380b-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="e380b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e380b-120">See also</span></span>

- [<span data-ttu-id="e380b-121">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="e380b-121">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="e380b-122">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e380b-122">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="e380b-123">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="e380b-123">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
