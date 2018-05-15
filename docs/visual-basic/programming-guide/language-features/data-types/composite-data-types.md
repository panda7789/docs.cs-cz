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
ms.openlocfilehash: 73867a5881db7c94d258e8716c4ff4c5b1119e71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="127ab-102">Složené datové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="127ab-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="127ab-103">Kromě základní datové typy jazyka Visual Basic dodávek, je možné sestavit položkami různých typů vytvořit *složené datové typy* například struktury, pole a třídy.</span><span class="sxs-lookup"><span data-stu-id="127ab-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="127ab-104">Složené datové typy můžete vytvořit z základní typy a z jiných složené typy.</span><span class="sxs-lookup"><span data-stu-id="127ab-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="127ab-105">Můžete například definovat pole elementy struktury nebo strukturu se členy pole.</span><span class="sxs-lookup"><span data-stu-id="127ab-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="127ab-106">Datové typy</span><span class="sxs-lookup"><span data-stu-id="127ab-106">Data Types</span></span>  
 <span data-ttu-id="127ab-107">Složeného typu se liší od datového typu všech jeho součástí.</span><span class="sxs-lookup"><span data-stu-id="127ab-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="127ab-108">Například pole `Integer` elementy není `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="127ab-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="127ab-109">Datového typu pole je obvykle reprezentována pomocí typ elementu, kulaté závorky a čárky podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="127ab-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="127ab-110">Například jednorozměrné pole z `String` elementy je reprezentován jako `String()`a dvourozměrná pole `Boolean` elementy je reprezentován jako `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="127ab-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="127ab-111">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="127ab-111">Structure Types</span></span>  
 <span data-ttu-id="127ab-112">Neexistuje žádný single – datový typ, která obsahuje všechny struktury.</span><span class="sxs-lookup"><span data-stu-id="127ab-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="127ab-113">Místo toho každá definice struktury představuje jedinečné datového typu, i v případě, že dvě struktury definovat identické prvky ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="127ab-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="127ab-114">Ale pokud vytvoříte dva nebo více instancí stejnou strukturu, Visual Basic je považuje za stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="127ab-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="127ab-115">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="127ab-115">Tuples</span></span>

<span data-ttu-id="127ab-116">Řazené kolekce členů je lightweight struktura, která obsahuje dvě nebo více polí, jejichž typy jsou předdefinovány.</span><span class="sxs-lookup"><span data-stu-id="127ab-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="127ab-117">Řazené kolekce členů jsou podporované počínaje 2017 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="127ab-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="127ab-118">Řazené kolekce členů se nejčastěji používají k vrácení více hodnot z volání jedné metody bez nutnosti předání argumentů odkazem nebo balení pole vrácené ve plně zobrazené třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="127ab-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="127ab-119">Najdete v článku [řazených kolekcí členů](tuples.md) téma pro další informace o řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="127ab-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="127ab-120">Typy polí</span><span class="sxs-lookup"><span data-stu-id="127ab-120">Array Types</span></span>  
 <span data-ttu-id="127ab-121">Neexistuje žádný single – datový typ, která obsahuje všechna pole.</span><span class="sxs-lookup"><span data-stu-id="127ab-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="127ab-122">Datový typ konkrétní instanci pole je dáno následující:</span><span class="sxs-lookup"><span data-stu-id="127ab-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="127ab-123">Skutečnost, že se pole</span><span class="sxs-lookup"><span data-stu-id="127ab-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="127ab-124">Pořadí (počet dimenzí) pole</span><span class="sxs-lookup"><span data-stu-id="127ab-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="127ab-125">Typ elementu pole</span><span class="sxs-lookup"><span data-stu-id="127ab-125">The element type of the array</span></span>  
  
 <span data-ttu-id="127ab-126">Délka dané dimenze konkrétně není částí instance datového typu.</span><span class="sxs-lookup"><span data-stu-id="127ab-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="127ab-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="127ab-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="127ab-128">V předchozím příkladu pole proměnných `arrayA` a `arrayB` jsou považovány za stejný datový typ. – `Byte()` – i když jsou inicializovány do různých délek.</span><span class="sxs-lookup"><span data-stu-id="127ab-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="127ab-129">Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementu se liší.</span><span class="sxs-lookup"><span data-stu-id="127ab-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="127ab-130">Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože jejich pořadí se liší.</span><span class="sxs-lookup"><span data-stu-id="127ab-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="127ab-131">Proměnné `arrayD` a `arrayE` stejný typ – `Short(,)` – protože jejich pořadí a typy elementů jsou stejné, i když `arrayD` ještě není inicializovaná.</span><span class="sxs-lookup"><span data-stu-id="127ab-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="127ab-132">Další informace o pole najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="127ab-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="127ab-133">Typy tříd</span><span class="sxs-lookup"><span data-stu-id="127ab-133">Class Types</span></span>  
 <span data-ttu-id="127ab-134">Neexistuje žádný single – datový typ, která obsahuje všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="127ab-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="127ab-135">I když jedna třída může dědit vlastnosti z jiné třídy, každá je samostatný datovým typem.</span><span class="sxs-lookup"><span data-stu-id="127ab-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="127ab-136">Více instancí stejné třídy mají stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="127ab-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="127ab-137">Chcete-li přiřadit jednu proměnnou instance třídy do druhého, nejen mají stejný datový typ., odkazují na stejnou instanci třídy v paměti.</span><span class="sxs-lookup"><span data-stu-id="127ab-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="127ab-138">Další informace o třídách naleznete v tématu [objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="127ab-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127ab-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="127ab-139">See Also</span></span>  
 [<span data-ttu-id="127ab-140">Datové typy</span><span class="sxs-lookup"><span data-stu-id="127ab-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="127ab-141">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="127ab-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="127ab-142">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="127ab-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="127ab-143">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="127ab-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="127ab-144">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="127ab-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="127ab-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="127ab-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="127ab-146">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="127ab-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="127ab-147">Postupy: Do proměnné umístit více než jednu hodnotu</span><span class="sxs-lookup"><span data-stu-id="127ab-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
