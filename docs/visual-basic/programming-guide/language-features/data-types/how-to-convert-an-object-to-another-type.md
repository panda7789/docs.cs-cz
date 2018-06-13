---
title: 'Postupy: Převedení objektu na jiný typ v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 367991e4bbca710df54edf73179f855ff79bb56e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647615"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="cc560-102">Postupy: Převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc560-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="cc560-103">Můžete převést `Object` proměnné na jiný datový typ. pomocí klíčového slova převodu [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="cc560-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc560-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc560-104">Example</span></span>  
 <span data-ttu-id="cc560-105">Následující příklad převede `Object` proměnnou `Integer` a `String`.</span><span class="sxs-lookup"><span data-stu-id="cc560-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="cc560-106">Pokud víte, že obsah `Object` proměnné jsou konkrétní datového typu, je lepší převést proměnnou datového typu.</span><span class="sxs-lookup"><span data-stu-id="cc560-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="cc560-107">Pokud budete pokračovat v používání `Object` proměnné, platit buď *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazby* (pro typ odkaz).</span><span class="sxs-lookup"><span data-stu-id="cc560-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="cc560-108">Tyto operace všechny trvat delší dobu provádění a ujistěte se, nižší výkon.</span><span class="sxs-lookup"><span data-stu-id="cc560-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc560-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cc560-109">Compiling the Code</span></span>  
 <span data-ttu-id="cc560-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cc560-110">This example requires:</span></span>  
  
-   <span data-ttu-id="cc560-111">Odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cc560-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc560-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc560-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="cc560-113">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc560-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="cc560-114">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="cc560-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="cc560-115">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="cc560-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="cc560-116">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="cc560-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="cc560-117">Převody polí</span><span class="sxs-lookup"><span data-stu-id="cc560-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="cc560-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="cc560-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="cc560-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="cc560-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="cc560-120">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="cc560-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
