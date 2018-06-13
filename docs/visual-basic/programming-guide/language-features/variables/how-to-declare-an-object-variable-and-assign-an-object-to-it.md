---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648873"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="be5f2-102">Postupy: Deklarace objektové proměnné a přiřazení objektu k proměnné v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be5f2-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="be5f2-103">Deklarace proměnné [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md) zadáním `As Object` v [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="be5f2-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="be5f2-104">Přiřazení objektu k tuto proměnnou tím, že objekt za znaménkem rovnítka (`=`) v klauzuli příkaz nebo inicializace přiřazení.</span><span class="sxs-lookup"><span data-stu-id="be5f2-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be5f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="be5f2-105">Example</span></span>  
 <span data-ttu-id="be5f2-106">Následující příklad deklaruje `Object` proměnnou a přiřadí aktuální instance k němu.</span><span class="sxs-lookup"><span data-stu-id="be5f2-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="be5f2-107">Deklarace a přiřazení můžete kombinovat podle inicializace proměnné jako součást jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="be5f2-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="be5f2-108">Následující příklad je ekvivalentní v předcházejícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="be5f2-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be5f2-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="be5f2-109">Compiling the Code</span></span>  
 <span data-ttu-id="be5f2-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="be5f2-110">This example requires:</span></span>  
  
-   <span data-ttu-id="be5f2-111">Odkaz na <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="be5f2-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="be5f2-112">Třída, struktura nebo modul, ve kterém se umístí `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="be5f2-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="be5f2-113">Postup, do kterého chcete vložit příkaz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="be5f2-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be5f2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="be5f2-114">See Also</span></span>  
 [<span data-ttu-id="be5f2-115">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="be5f2-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="be5f2-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="be5f2-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="be5f2-117">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="be5f2-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="be5f2-118">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="be5f2-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="be5f2-119">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="be5f2-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="be5f2-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="be5f2-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="be5f2-121">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="be5f2-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
