---
title: 'Postupy: Deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: e172d62e5bfadded254d5a5fd25b1dcf2da9634d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663579"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="bddf8-102">Postupy: Deklarace objektové proměnné a přiřazení objektu k v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bddf8-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="bddf8-103">Můžete deklarovat proměnnou [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) zadáním `As Object` v [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bddf8-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="bddf8-104">Přiřaďte objekt na takovou proměnnou tak, že objekt za znaménkem rovnítka (`=`) v klauzuli přiřazení příkazu nebo inicializace.</span><span class="sxs-lookup"><span data-stu-id="bddf8-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bddf8-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="bddf8-105">Example</span></span>  
 <span data-ttu-id="bddf8-106">Následující příklad deklaruje `Object` proměnné a přiřazuje aktuální instance k němu.</span><span class="sxs-lookup"><span data-stu-id="bddf8-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="bddf8-107">Deklaraci a přiřazení můžete kombinovat pomocí inicializace proměnné jako součást její deklarace.</span><span class="sxs-lookup"><span data-stu-id="bddf8-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="bddf8-108">Následující příklad je ekvivalentní k předchozímu příkladu.</span><span class="sxs-lookup"><span data-stu-id="bddf8-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bddf8-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bddf8-109">Compiling the Code</span></span>  
 <span data-ttu-id="bddf8-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bddf8-110">This example requires:</span></span>  
  
- <span data-ttu-id="bddf8-111">Odkaz na <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bddf8-111">A reference to the <xref:System> namespace.</span></span>  
  
- <span data-ttu-id="bddf8-112">Třídy, struktury nebo modul, ve které chcete umístit `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="bddf8-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
- <span data-ttu-id="bddf8-113">Postup, ve kterém chcete změnit příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="bddf8-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bddf8-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bddf8-114">See also</span></span>

- [<span data-ttu-id="bddf8-115">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="bddf8-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="bddf8-116">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="bddf8-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="bddf8-117">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="bddf8-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="bddf8-118">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="bddf8-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="bddf8-119">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="bddf8-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="bddf8-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="bddf8-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="bddf8-121">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="bddf8-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
