---
title: 'Postupy: Převést objekt na jiný typ v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 1e515c0f4ce8e787754c61a9b53d247fa93c49f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906526"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="ed282-102">Postupy: Převést objekt na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed282-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="ed282-103">Převedete `Object` proměnné na jiný datový typ. pomocí klíčového slova převodu [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="ed282-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed282-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed282-104">Example</span></span>  
 <span data-ttu-id="ed282-105">Následující příklad převádí `Object` proměnné `Integer` a `String`.</span><span class="sxs-lookup"><span data-stu-id="ed282-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="ed282-106">Pokud víte, že obsah `Object` proměnné jsou konkrétní datového typu, je vhodnější převést proměnnou datového typu.</span><span class="sxs-lookup"><span data-stu-id="ed282-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="ed282-107">Pokud budete nadále používat `Object` proměnné, se vám účtovat buď *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazby* (pro odkazový typ).</span><span class="sxs-lookup"><span data-stu-id="ed282-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="ed282-108">Tyto operace všechny trvat delší dobu spuštění a provést pomalejší výkon.</span><span class="sxs-lookup"><span data-stu-id="ed282-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed282-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ed282-109">Compiling the Code</span></span>  
 <span data-ttu-id="ed282-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ed282-110">This example requires:</span></span>  
  
- <span data-ttu-id="ed282-111">Odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ed282-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed282-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed282-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="ed282-113">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed282-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="ed282-114">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="ed282-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="ed282-115">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="ed282-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="ed282-116">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="ed282-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="ed282-117">Převody polí</span><span class="sxs-lookup"><span data-stu-id="ed282-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="ed282-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="ed282-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ed282-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="ed282-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="ed282-120">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="ed282-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
