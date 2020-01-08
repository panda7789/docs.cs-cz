---
title: 'Postupy: převod objektu na jiný typ'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341577"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="254d7-102">Postupy: Převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="254d7-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="254d7-103">Převedete `Object` proměnnou na jiný datový typ pomocí klíčového slova převodu, jako je [CType funkce](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="254d7-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="254d7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="254d7-104">Example</span></span>  
 <span data-ttu-id="254d7-105">Následující příklad převede `Object` proměnnou na `Integer` a `String`.</span><span class="sxs-lookup"><span data-stu-id="254d7-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="254d7-106">Pokud víte, že obsah `Object` proměnné jsou konkrétního datového typu, je lepší převést proměnnou na tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="254d7-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="254d7-107">Pokud budete nadále používat `Object` proměnnou, bude se vám účtovat *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazba* (pro typ odkazu).</span><span class="sxs-lookup"><span data-stu-id="254d7-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="254d7-108">Tyto operace vybírají delší dobu spuštění a zpomalují výkon.</span><span class="sxs-lookup"><span data-stu-id="254d7-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="254d7-109">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="254d7-109">Compile the code</span></span>  
 <span data-ttu-id="254d7-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="254d7-110">This example requires:</span></span>  
  
- <span data-ttu-id="254d7-111">Odkaz na obor názvů <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="254d7-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="254d7-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="254d7-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="254d7-113">Převody typu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="254d7-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="254d7-114">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="254d7-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="254d7-115">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="254d7-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="254d7-116">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="254d7-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="254d7-117">Převody polí</span><span class="sxs-lookup"><span data-stu-id="254d7-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="254d7-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="254d7-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="254d7-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="254d7-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="254d7-120">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="254d7-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
