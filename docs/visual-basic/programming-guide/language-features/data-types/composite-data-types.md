---
title: Složené datové typy (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833812"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="149ff-102">Složené datové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="149ff-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="149ff-103">Kromě základní datové typy jazyka Visual Basic nabízí, můžete také sestavit položky k vytvoření různých typů *složené datové typy* například třídy, struktury a pole.</span><span class="sxs-lookup"><span data-stu-id="149ff-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="149ff-104">Složené datové typy můžete vytvořit ze základních typů a z dalších složené typy.</span><span class="sxs-lookup"><span data-stu-id="149ff-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="149ff-105">Například můžete definovat pole prvky struktury nebo strukturu s členy pole.</span><span class="sxs-lookup"><span data-stu-id="149ff-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="149ff-106">Datové typy</span><span class="sxs-lookup"><span data-stu-id="149ff-106">Data Types</span></span>  
 <span data-ttu-id="149ff-107">Složený typ se liší od typu dat jeho součástí.</span><span class="sxs-lookup"><span data-stu-id="149ff-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="149ff-108">Například pole `Integer` prvky není `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="149ff-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="149ff-109">Datový typ pole se obvykle vyjadřuje typ elementu, závorek a čárky podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="149ff-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="149ff-110">Například jednorozměrné pole `String` elementů je vyjádřena jako `String()`a dvourozměrné pole `Boolean` elementů je vyjádřena jako `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="149ff-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="149ff-111">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="149ff-111">Structure Types</span></span>  
 <span data-ttu-id="149ff-112">Neexistuje žádný jednotlivý typ dat obsahující všechny struktury.</span><span class="sxs-lookup"><span data-stu-id="149ff-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="149ff-113">Místo toho každá definice struktury představuje jedinečný datový typ, i v případě, že dvě struktury definují stejné prvky ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="149ff-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="149ff-114">Nicméně pokud vytvoříte dvě nebo víc instancí se stejnou strukturou, Visual Basic je považuje za stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="149ff-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="149ff-115">N-tice</span><span class="sxs-lookup"><span data-stu-id="149ff-115">Tuples</span></span>

<span data-ttu-id="149ff-116">Řazená kolekce členů je zjednodušené strukturu, která obsahuje dvě nebo více polí, jejichž typy jsou předdefinovány.</span><span class="sxs-lookup"><span data-stu-id="149ff-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="149ff-117">Řazené kolekce členů jsou podporovány, počínaje rokem 2017 jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="149ff-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="149ff-118">Řazené kolekce členů se nejčastěji používají k vrácení více hodnot z jedné metody volání bez nutnosti předávat argumenty odkazem nebo balení pole vrácené ve více zobrazené třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="149ff-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="149ff-119">Zobrazit [řazených kolekcí členů](tuples.md) tématu pro další informace o řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="149ff-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="149ff-120">Typy polí</span><span class="sxs-lookup"><span data-stu-id="149ff-120">Array Types</span></span>  
 <span data-ttu-id="149ff-121">Neexistuje žádný jednotlivý typ dat skládající se z aplikací všechna pole.</span><span class="sxs-lookup"><span data-stu-id="149ff-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="149ff-122">Datový typ konkrétní instanci pole se určuje takto:</span><span class="sxs-lookup"><span data-stu-id="149ff-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="149ff-123">Skutečnost, že se pole</span><span class="sxs-lookup"><span data-stu-id="149ff-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="149ff-124">Pořadí (počet rozměrů) v poli</span><span class="sxs-lookup"><span data-stu-id="149ff-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="149ff-125">Typ prvku pole</span><span class="sxs-lookup"><span data-stu-id="149ff-125">The element type of the array</span></span>  
  
 <span data-ttu-id="149ff-126">Délka dané dimenze zejména, není součástí instance datového typu.</span><span class="sxs-lookup"><span data-stu-id="149ff-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="149ff-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="149ff-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="149ff-128">V předchozím příkladu pole proměnné `arrayA` a `arrayB` jsou považovány za stejný datový typ. – `Byte()` – i když jsou inicializovány na různých délek.</span><span class="sxs-lookup"><span data-stu-id="149ff-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="149ff-129">Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementů se liší.</span><span class="sxs-lookup"><span data-stu-id="149ff-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="149ff-130">Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože jejich pořadí se liší.</span><span class="sxs-lookup"><span data-stu-id="149ff-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="149ff-131">Proměnné `arrayD` a `arrayE` mají stejný typ – `Short(,)` – protože jejich pořadí a typy elementů jsou stejné, i když `arrayD` ještě není inicializovaná.</span><span class="sxs-lookup"><span data-stu-id="149ff-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="149ff-132">Další informace o polích naleznete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="149ff-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="149ff-133">Typy tříd</span><span class="sxs-lookup"><span data-stu-id="149ff-133">Class Types</span></span>  
 <span data-ttu-id="149ff-134">Neexistuje žádný jednotlivý typ dat obsahující všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="149ff-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="149ff-135">I když jedna třída může dědit z jiné třídy, každá je samostatná datová typu.</span><span class="sxs-lookup"><span data-stu-id="149ff-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="149ff-136">Více instancí jedné třídy mají stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="149ff-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="149ff-137">Pokud přiřadíte jednu proměnnou instance třídy na jiný, nejen mají stejný datový typ., ukazují na stejnou instanci třídy v paměti.</span><span class="sxs-lookup"><span data-stu-id="149ff-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="149ff-138">Další informace o třídách naleznete v tématu [objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="149ff-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149ff-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="149ff-139">See also</span></span>

- [<span data-ttu-id="149ff-140">Datové typy</span><span class="sxs-lookup"><span data-stu-id="149ff-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="149ff-141">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="149ff-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="149ff-142">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="149ff-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="149ff-143">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="149ff-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="149ff-144">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="149ff-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="149ff-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="149ff-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="149ff-146">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="149ff-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="149ff-147">Postupy: Uchování více než jedné hodnoty v proměnné</span><span class="sxs-lookup"><span data-stu-id="149ff-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
