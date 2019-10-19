---
title: 'Postupy: Převedení objektu na jiný typ v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 39083fc55d30e24c357ec162a15466f81655f4c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582330"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="53257-102">Postupy: Převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53257-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="53257-103">Převedete `Object` proměnnou na jiný datový typ pomocí klíčového slova převodu, jako je [CType funkce](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="53257-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53257-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="53257-104">Example</span></span>  
 <span data-ttu-id="53257-105">Následující příklad převede `Object` proměnnou na `Integer` a `String`.</span><span class="sxs-lookup"><span data-stu-id="53257-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="53257-106">Pokud víte, že obsah `Object` proměnné jsou konkrétního datového typu, je lepší převést proměnnou na tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="53257-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="53257-107">Pokud budete nadále používat `Object` proměnnou, bude se vám účtovat *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazba* (pro typ odkazu).</span><span class="sxs-lookup"><span data-stu-id="53257-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="53257-108">Tyto operace vybírají delší dobu spuštění a zpomalují výkon.</span><span class="sxs-lookup"><span data-stu-id="53257-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53257-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="53257-109">Compiling the Code</span></span>  
 <span data-ttu-id="53257-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="53257-110">This example requires:</span></span>  
  
- <span data-ttu-id="53257-111">Odkaz na obor názvů <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53257-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53257-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53257-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="53257-113">Převody typu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53257-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="53257-114">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="53257-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="53257-115">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="53257-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="53257-116">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="53257-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="53257-117">Převody polí</span><span class="sxs-lookup"><span data-stu-id="53257-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="53257-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="53257-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="53257-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="53257-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="53257-120">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="53257-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
