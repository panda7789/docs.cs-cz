---
title: Převody pole (Visual Basic)
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
ms.openlocfilehash: 93e6365a70f52f730b016cd4d4ac9382baeeba55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396546"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="ab755-102">Převody pole (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab755-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="ab755-103">Typ pole lze převést na typ jiné pole, za předpokladu splnění následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="ab755-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="ab755-104">**Stejné pořadí.**</span><span class="sxs-lookup"><span data-stu-id="ab755-104">**Equal Rank.**</span></span> <span data-ttu-id="ab755-105">Rozměry dvě pole musí být stejná, to znamená, že musí mít stejný počet rozměrů.</span><span class="sxs-lookup"><span data-stu-id="ab755-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="ab755-106">Délky příslušných dimenzí nemusí však být stejné.</span><span class="sxs-lookup"><span data-stu-id="ab755-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="ab755-107">**Typ dat prvku.**</span><span class="sxs-lookup"><span data-stu-id="ab755-107">**Element Data Type.**</span></span> <span data-ttu-id="ab755-108">Datové typy prvky obou polí musí být typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="ab755-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="ab755-109">Nelze převést `Integer` pole k `Long` pole, nebo dokonce k `Object` pole, protože se účastní alespoň jednu hodnotu typu.</span><span class="sxs-lookup"><span data-stu-id="ab755-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="ab755-110">Další informace najdete v tématu [typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="ab755-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="ab755-111">**Převoditelnosti.**</span><span class="sxs-lookup"><span data-stu-id="ab755-111">**Convertibility.**</span></span> <span data-ttu-id="ab755-112">Převod, rozšíření ani zúžení při, musí být mezi typy prvků dvou polí.</span><span class="sxs-lookup"><span data-stu-id="ab755-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="ab755-113">Je příklad, který tento požadavek se nezdaří pokus o převod mezi `String` pole a pole třídy odvozené z <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab755-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ab755-114">Tyto dva typy nemají co v běžných a neexistuje žádný převod jakéhokoli druhu mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="ab755-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="ab755-115">Převod jednoho pole typu na jiný je rozšíření ani zúžení v závislosti na tom, jestli je převod odpovídajících prvků rozšíření ani zúžení při.</span><span class="sxs-lookup"><span data-stu-id="ab755-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="ab755-116">Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="ab755-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="ab755-117">Převod na pole objektů</span><span class="sxs-lookup"><span data-stu-id="ab755-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="ab755-118">Pokud deklarujete `Object` pole bez inicializuje, jeho typ elementu je `Object` dlouho, dokud zůstává Neinicializovaný.</span><span class="sxs-lookup"><span data-stu-id="ab755-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="ab755-119">Pokud ji nastavíte na pole určité třídy, převezme typu třídy.</span><span class="sxs-lookup"><span data-stu-id="ab755-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="ab755-120">Jeho základní typ je však stále `Object`, a můžete ho nastavit následně do jiného objektu array nesouvisejících třídy.</span><span class="sxs-lookup"><span data-stu-id="ab755-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="ab755-121">Protože všechny třídy odvozovat z `Object`, typ elementu pole z jiné třídy, můžete změnit na jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="ab755-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="ab755-122">V následujícím příkladu, neexistuje žádný převod mezi typy `student` a `String`, ale oba jsou odvozeny z `Object`, takže platí všechna přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ab755-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="ab755-123">Základní typ pole</span><span class="sxs-lookup"><span data-stu-id="ab755-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="ab755-124">Pokud deklarujete původně pole s konkrétní třídou, je jeho základní typ elementu třídy.</span><span class="sxs-lookup"><span data-stu-id="ab755-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="ab755-125">Pokud následně ji nastavíte na pole jiné třídy, musí být převod mezi dvěma třídami.</span><span class="sxs-lookup"><span data-stu-id="ab755-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="ab755-126">V následujícím příkladu `students` je `student` pole.</span><span class="sxs-lookup"><span data-stu-id="ab755-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="ab755-127">Protože neexistuje žádný převod mezi `String` a `student`, poslední příkaz se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ab755-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab755-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab755-128">See Also</span></span>  
 [<span data-ttu-id="ab755-129">Datové typy</span><span class="sxs-lookup"><span data-stu-id="ab755-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ab755-130">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab755-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="ab755-131">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="ab755-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="ab755-132">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="ab755-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="ab755-133">Postupy: převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab755-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="ab755-134">Datové typy</span><span class="sxs-lookup"><span data-stu-id="ab755-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="ab755-135">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="ab755-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ab755-136">Pole</span><span class="sxs-lookup"><span data-stu-id="ab755-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
