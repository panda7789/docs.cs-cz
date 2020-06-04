---
title: Převody polí
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 1d20b01200d3f967e3355dc6e9651291003d140e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402002"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="43f93-102">Převody pole (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43f93-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="43f93-103">Typ pole můžete převést na jiný typ pole, pokud splňujete následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="43f93-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="43f93-104">**Stejné pořadí.**</span><span class="sxs-lookup"><span data-stu-id="43f93-104">**Equal Rank.**</span></span> <span data-ttu-id="43f93-105">Pořadí dvou polí musí být stejné, to znamená, že musí mít stejný počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="43f93-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="43f93-106">Nicméně délky příslušných dimenzí nemusejí být stejné.</span><span class="sxs-lookup"><span data-stu-id="43f93-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="43f93-107">**Datový typ elementu.**</span><span class="sxs-lookup"><span data-stu-id="43f93-107">**Element Data Type.**</span></span> <span data-ttu-id="43f93-108">Datové typy prvků obou polí musí být odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="43f93-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="43f93-109">Pole nelze převést `Integer` na `Long` pole nebo dokonce na `Object` pole, protože je zapojen alespoň jeden typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="43f93-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="43f93-110">Další informace naleznete v tématu [typy hodnot a typy odkazů](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="43f93-110">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="43f93-111">**Převoditelnosti.**</span><span class="sxs-lookup"><span data-stu-id="43f93-111">**Convertibility.**</span></span> <span data-ttu-id="43f93-112">Převod, buď rozšiřující nebo zúžený, musí být možný mezi typy prvků obou polí.</span><span class="sxs-lookup"><span data-stu-id="43f93-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="43f93-113">Příklad, který tento požadavek neprojde, je pokus o převod mezi `String` polem a polem třídy odvozené z <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="43f93-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="43f93-114">Tyto dva typy nemají nic společného a mezi nimi neexistují žádné konverze žádného druhu.</span><span class="sxs-lookup"><span data-stu-id="43f93-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="43f93-115">Převod jednoho typu pole na jiný je rozšiřující nebo zúžený v závislosti na tom, zda je převod odpovídajících prvků rozšiřující nebo zúžený.</span><span class="sxs-lookup"><span data-stu-id="43f93-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="43f93-116">Další informace najdete v tématu [rozšiřování a zúžení převodů](widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="43f93-116">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="43f93-117">Převod na pole objektů</span><span class="sxs-lookup"><span data-stu-id="43f93-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="43f93-118">Při deklaraci `Object` pole bez jeho inicializace je jeho typ prvku `Object` tak dlouho, dokud zůstává Neinicializovaný.</span><span class="sxs-lookup"><span data-stu-id="43f93-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="43f93-119">Když je nastavena na pole konkrétní třídy, převezme typ dané třídy.</span><span class="sxs-lookup"><span data-stu-id="43f93-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="43f93-120">Jeho nadřízený typ je však stále nadále `Object` a lze jej následně nastavit na jiné pole nesouvisející třídy.</span><span class="sxs-lookup"><span data-stu-id="43f93-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="43f93-121">Vzhledem k tomu, že všechny třídy jsou odvozeny z `Object` , můžete změnit typ elementu pole z libovolné třídy na jinou třídu.</span><span class="sxs-lookup"><span data-stu-id="43f93-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="43f93-122">V následujícím příkladu neexistuje žádný převod mezi typy `student` a `String` , ale obě jsou odvozeny z `Object` , takže všechna přiřazení jsou platná.</span><span class="sxs-lookup"><span data-stu-id="43f93-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="43f93-123">Základní typ pole</span><span class="sxs-lookup"><span data-stu-id="43f93-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="43f93-124">Pokud jste původně deklarovali pole s určitou třídou, jeho základní typ prvku je tato třída.</span><span class="sxs-lookup"><span data-stu-id="43f93-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="43f93-125">Pokud jste následně nastavili pole jiné třídy, musí být převod mezi těmito dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="43f93-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="43f93-126">V následujícím příkladu `students` je `student` pole.</span><span class="sxs-lookup"><span data-stu-id="43f93-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="43f93-127">Vzhledem k tomu, že mezi a neexistuje žádný převod `String` `student` , poslední příkaz se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="43f93-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="43f93-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="43f93-128">See also</span></span>

- [<span data-ttu-id="43f93-129">Datové typy</span><span class="sxs-lookup"><span data-stu-id="43f93-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="43f93-130">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43f93-130">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="43f93-131">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="43f93-131">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="43f93-132">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="43f93-132">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="43f93-133">Postupy: Převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43f93-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="43f93-134">Datové typy</span><span class="sxs-lookup"><span data-stu-id="43f93-134">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="43f93-135">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="43f93-135">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="43f93-136">Pole</span><span class="sxs-lookup"><span data-stu-id="43f93-136">Arrays</span></span>](../arrays/index.md)
