---
title: Výraz je hodnota, a proto nemůže být cílem přiřazení.
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: dd5618bd0533f885a6aef8229b2d8cb1bc34c237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590235"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="8641f-102">Výraz je hodnota, a proto nemůže být cílem přiřazení.</span><span class="sxs-lookup"><span data-stu-id="8641f-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="8641f-103">Příkaz se pokusí přiřadit hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="8641f-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="8641f-104">V době běhu můžete přiřadit hodnotu pouze pro zápis proměnnou, vlastnost nebo pole elementu.</span><span class="sxs-lookup"><span data-stu-id="8641f-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="8641f-105">Následující příklad ilustruje, jak této chybě může dojít.</span><span class="sxs-lookup"><span data-stu-id="8641f-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="8641f-106">Podobné příklady může použít k vlastnostem a prvků pole.</span><span class="sxs-lookup"><span data-stu-id="8641f-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="8641f-107">**Nepřímý přístup.**</span><span class="sxs-lookup"><span data-stu-id="8641f-107">**Indirect Access.**</span></span> <span data-ttu-id="8641f-108">Nepřímý přístup prostřednictvím typ hodnoty můžete také vygenerovat tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="8641f-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="8641f-109">Vezměte v úvahu následující příklad kódu, který se pokouší nastavit hodnotu <xref:System.Drawing.Point> díky přístupu k nepřímo přes <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="8641f-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="8641f-110">Poslední příkaz v předchozím příkladu selže, protože se tím vytvoří dočasný přidělení pro <xref:System.Drawing.Point> struktura vrácený <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8641f-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="8641f-111">Struktura je typ hodnoty a strukturu dočasné nezůstanou zachovány po spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="8641f-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="8641f-112">Deklarování a použití proměnné pro vyřešení problému <xref:System.Windows.Forms.Control.Location%2A>, která vytvoří více trvalých přidělení pro <xref:System.Drawing.Point> struktura.</span><span class="sxs-lookup"><span data-stu-id="8641f-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="8641f-113">Následující příklad ukazuje kód, který můžete nahradit poslední příkaz v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8641f-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="8641f-114">**ID chyby:** BC30068</span><span class="sxs-lookup"><span data-stu-id="8641f-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8641f-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8641f-115">To correct this error</span></span>  
  
-   <span data-ttu-id="8641f-116">Pokud příkaz přiřazuje hodnotu výrazu, nahraďte výraz jedné proměnné s možností zápisu, vlastnost nebo pole elementu.</span><span class="sxs-lookup"><span data-stu-id="8641f-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="8641f-117">Pokud se příkaz provede nepřímý přístup prostřednictvím typu hodnoty (obvykle struktura), vytvořte proměnnou pro uložení typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8641f-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="8641f-118">Přiřaďte proměnnou strukturu odpovídající (nebo jiný typ hodnota).</span><span class="sxs-lookup"><span data-stu-id="8641f-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="8641f-119">Použijte proměnnou pro přístup k vlastnosti ji přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8641f-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8641f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8641f-120">See Also</span></span>  
 [<span data-ttu-id="8641f-121">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="8641f-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="8641f-122">Příkazy</span><span class="sxs-lookup"><span data-stu-id="8641f-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="8641f-123">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="8641f-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
