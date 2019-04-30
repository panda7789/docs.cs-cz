---
title: Výraz je hodnota, a proto nemůže být cílem přiřazení.
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802606"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="0048f-102">Výraz je hodnota, a proto nemůže být cílem přiřazení.</span><span class="sxs-lookup"><span data-stu-id="0048f-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="0048f-103">Příkaz se pokusí přiřadit hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="0048f-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="0048f-104">Přiřadit hodnotu pouze pro zapisovatelné proměnná, vlastnost nebo prvku pole za běhu.</span><span class="sxs-lookup"><span data-stu-id="0048f-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="0048f-105">Následující příklad ukazuje, jak k této chybě může dojít.</span><span class="sxs-lookup"><span data-stu-id="0048f-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="0048f-106">Podobné příklady může použít k vlastnostem a prvky pole.</span><span class="sxs-lookup"><span data-stu-id="0048f-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="0048f-107">**Nepřímý přístup.**</span><span class="sxs-lookup"><span data-stu-id="0048f-107">**Indirect Access.**</span></span> <span data-ttu-id="0048f-108">Tuto chybu můžete vygenerovat také nepřímý přístup prostřednictvím hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="0048f-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="0048f-109">Zvažte následující příklad kódu, která se pokusí nastavit hodnotu <xref:System.Drawing.Point> díky přístupu nepřímo prostřednictvím <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="0048f-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="0048f-110">Poslední příkaz v předchozím příkladu se nezdaří, protože se vytvoří dočasný přidělení pro <xref:System.Drawing.Point> vrácené struktury <xref:System.Windows.Forms.Control.Location%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0048f-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="0048f-111">Struktura je hodnotový typ a strukturu dočasné není zachována po spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="0048f-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="0048f-112">Problém je vyřešen deklarování a použití proměnné pro <xref:System.Windows.Forms.Control.Location%2A>, vytváří trvalejší přidělení pro <xref:System.Drawing.Point> struktury.</span><span class="sxs-lookup"><span data-stu-id="0048f-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="0048f-113">Následující příklad ukazuje kód, který můžete nahradit poslední příkaz v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0048f-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="0048f-114">**ID chyby:** BC30068</span><span class="sxs-lookup"><span data-stu-id="0048f-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0048f-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0048f-115">To correct this error</span></span>  
  
- <span data-ttu-id="0048f-116">Pokud příkaz přiřazuje hodnotu výrazu, nahraďte výraz jeden zapisovatelný proměnná, vlastnost nebo pole elementu.</span><span class="sxs-lookup"><span data-stu-id="0048f-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
- <span data-ttu-id="0048f-117">Pokud příkaz vytváří nepřímý přístup prostřednictvím typu hodnoty (obvykle struktury), vytvořte proměnnou pro uchování hodnoty typu.</span><span class="sxs-lookup"><span data-stu-id="0048f-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
- <span data-ttu-id="0048f-118">Přiřaďte proměnné vhodnou strukturou (nebo jiný typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="0048f-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
- <span data-ttu-id="0048f-119">Pro přístup k vlastnosti k ní přiřadit hodnotu, použijte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0048f-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0048f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0048f-120">See also</span></span>

- [<span data-ttu-id="0048f-121">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="0048f-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="0048f-122">Příkazy</span><span class="sxs-lookup"><span data-stu-id="0048f-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="0048f-123">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="0048f-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
