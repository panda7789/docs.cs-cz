---
title: "Převody pole (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="66774-102">Převody pole (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66774-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="66774-103">Typ pole můžete převést na typ různých pole zadaný splňovat následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="66774-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="66774-104">**Stejné pořadí.**</span><span class="sxs-lookup"><span data-stu-id="66774-104">**Equal Rank.**</span></span> <span data-ttu-id="66774-105">Pořadí dvě polí musí být stejná, to znamená, musí mít stejný počet dimenzí.</span><span class="sxs-lookup"><span data-stu-id="66774-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="66774-106">Ale délek příslušných dimenzí, nemusíte být stejné.</span><span class="sxs-lookup"><span data-stu-id="66774-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="66774-107">**Datový typ elementu.**</span><span class="sxs-lookup"><span data-stu-id="66774-107">**Element Data Type.**</span></span> <span data-ttu-id="66774-108">Datové typy elementů obě pole musí být typu odkaz.</span><span class="sxs-lookup"><span data-stu-id="66774-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="66774-109">Nelze převést `Integer` pole k `Long` pole nebo dokonce na `Object` pole, protože nejméně jedna hodnota typu je zahrnuta.</span><span class="sxs-lookup"><span data-stu-id="66774-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="66774-110">Další informace najdete v tématu [typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="66774-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="66774-111">**Konvertibility.**</span><span class="sxs-lookup"><span data-stu-id="66774-111">**Convertibility.**</span></span> <span data-ttu-id="66774-112">Převod, rozšiřující nebo zužující, musí být možné mezi typy element dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="66774-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="66774-113">Příklad, který selže tento požadavek je pokusu o převod mezi `String` pole a pole třídy odvozené od <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66774-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66774-114">Tyto dva typy mají nic společné a mezi nimi existuje žádný převod jakéhokoli druhu.</span><span class="sxs-lookup"><span data-stu-id="66774-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="66774-115">Převod typu jedno pole do jiné rozšíření nebo zužující podle toho, jestli rozšiřující nebo zužující převod příslušných elementů.</span><span class="sxs-lookup"><span data-stu-id="66774-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="66774-116">Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="66774-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="66774-117">Převod na pole objektů</span><span class="sxs-lookup"><span data-stu-id="66774-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="66774-118">Když je deklarovat `Object` pole nebyl zadán, je její typ elementu je `Object` tak dlouho, dokud zůstává Neinicializovaný.</span><span class="sxs-lookup"><span data-stu-id="66774-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="66774-119">Když je nastavena na pole určité třídy, dojde na typu třídy.</span><span class="sxs-lookup"><span data-stu-id="66774-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="66774-120">Základní typ je však stále `Object`, a můžete ho nastavit následně ke druhému nesouvisejícími třídy.</span><span class="sxs-lookup"><span data-stu-id="66774-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="66774-121">Vzhledem k tomu, že všechny třídy jsou odvozeny od `Object`, můžete změnit typ elementu pole z libovolné třídy na jiná třída.</span><span class="sxs-lookup"><span data-stu-id="66774-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="66774-122">V následujícím příkladu, neexistuje žádný převod mezi typy `student` a `String`, ale i odvozena od `Object`, takže všechny jsou platná.</span><span class="sxs-lookup"><span data-stu-id="66774-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="66774-123">Základní typ pole</span><span class="sxs-lookup"><span data-stu-id="66774-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="66774-124">Pokud je původně deklarovat pole s určité třídy, je jeho zdrojovým typem elementu třídy.</span><span class="sxs-lookup"><span data-stu-id="66774-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="66774-125">Pokud je následně nastavena na pole jinou třídu, musí být převod mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="66774-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="66774-126">V následujícím příkladu `students` je `student` pole.</span><span class="sxs-lookup"><span data-stu-id="66774-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="66774-127">Vzhledem k tomu, že neexistuje žádný převod mezi `String` a `student`, poslední příkaz se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="66774-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="66774-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="66774-128">See Also</span></span>  
 [<span data-ttu-id="66774-129">Datové typy</span><span class="sxs-lookup"><span data-stu-id="66774-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="66774-130">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66774-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="66774-131">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="66774-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="66774-132">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="66774-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="66774-133">Postupy: převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66774-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="66774-134">Datové typy</span><span class="sxs-lookup"><span data-stu-id="66774-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="66774-135">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="66774-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="66774-136">Pole</span><span class="sxs-lookup"><span data-stu-id="66774-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
