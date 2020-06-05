---
title: 'Postupy: Převedení objektu na jiný typ'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393958"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="43af0-102">Postupy: Převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43af0-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="43af0-103">Proměnnou převedete `Object` na jiný datový typ pomocí klíčového slova pro převod, jako je například [CType funkce](../../../language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="43af0-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43af0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="43af0-104">Example</span></span>  
 <span data-ttu-id="43af0-105">Následující příklad převede `Object` proměnnou na `Integer` a `String` .</span><span class="sxs-lookup"><span data-stu-id="43af0-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="43af0-106">Pokud víte, že obsah `Object` proměnné je určitého datového typu, je lepší převést proměnnou na tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="43af0-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="43af0-107">Pokud budete nadále používat `Object` proměnnou, získáte buď *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazba* (pro typ odkazu).</span><span class="sxs-lookup"><span data-stu-id="43af0-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="43af0-108">Tyto operace vybírají delší dobu spuštění a zpomalují výkon.</span><span class="sxs-lookup"><span data-stu-id="43af0-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="43af0-109">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="43af0-109">Compile the code</span></span>  
 <span data-ttu-id="43af0-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="43af0-110">This example requires:</span></span>  
  
- <span data-ttu-id="43af0-111">Odkaz na <xref:System?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="43af0-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43af0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="43af0-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="43af0-113">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43af0-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="43af0-114">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="43af0-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="43af0-115">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="43af0-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="43af0-116">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="43af0-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="43af0-117">Převody polí</span><span class="sxs-lookup"><span data-stu-id="43af0-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="43af0-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="43af0-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="43af0-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="43af0-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="43af0-120">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="43af0-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
