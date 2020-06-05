---
title: Složené datové typy
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
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394295"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="63520-102">Složené datové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63520-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="63520-103">Kromě základních datových typů Visual Basic dodávek můžete také sestavit položky různých typů pro vytváření *složených datových typů* , jako jsou struktury, pole a třídy.</span><span class="sxs-lookup"><span data-stu-id="63520-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="63520-104">Můžete sestavit složené datové typy z základních typů a z jiných složených typů.</span><span class="sxs-lookup"><span data-stu-id="63520-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="63520-105">Například můžete definovat pole prvků struktury nebo strukturu s členy pole.</span><span class="sxs-lookup"><span data-stu-id="63520-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="63520-106">Typy dat</span><span class="sxs-lookup"><span data-stu-id="63520-106">Data Types</span></span>  
 <span data-ttu-id="63520-107">Složený typ se liší od datového typu kterékoli z jeho komponent.</span><span class="sxs-lookup"><span data-stu-id="63520-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="63520-108">Například pole `Integer` prvků není `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="63520-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="63520-109">Datový typ pole je obvykle reprezentován pomocí typu prvku, závorek a čárek podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="63520-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="63520-110">Například jednorozměrné pole `String` elementů je reprezentované jako `String()` a dvojrozměrné pole `Boolean` prvků je reprezentované jako `Boolean(,)` .</span><span class="sxs-lookup"><span data-stu-id="63520-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="63520-111">Typy struktury</span><span class="sxs-lookup"><span data-stu-id="63520-111">Structure Types</span></span>  
 <span data-ttu-id="63520-112">Neexistuje žádný jediný datový typ, který by zahrnoval všechny struktury.</span><span class="sxs-lookup"><span data-stu-id="63520-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="63520-113">Místo toho každá definice struktury představuje jedinečný datový typ, a to i v případě, že dvě struktury definují identické prvky ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="63520-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="63520-114">Pokud však vytvoříte dvě nebo více instancí stejné struktury, Visual Basic považují být za stejný datový typ.</span><span class="sxs-lookup"><span data-stu-id="63520-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="63520-115">N-tice</span><span class="sxs-lookup"><span data-stu-id="63520-115">Tuples</span></span>

<span data-ttu-id="63520-116">Řazená kolekce členů je odlehčená struktura, která obsahuje dvě nebo více polí, jejichž typy jsou předdefinované.</span><span class="sxs-lookup"><span data-stu-id="63520-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="63520-117">Řazené kolekce členů jsou podporované od Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="63520-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="63520-118">Řazené kolekce členů se nejčastěji používají pro vracení více hodnot z jednoho volání metody bez nutnosti předávat argumenty odkazem nebo zabalení vrácených polí v rozsáhlejší třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="63520-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="63520-119">Další informace o řazených kolekcích členů najdete v tématu [řazené kolekce členů](tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="63520-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="63520-120">Typy polí</span><span class="sxs-lookup"><span data-stu-id="63520-120">Array Types</span></span>  
 <span data-ttu-id="63520-121">Neexistuje žádný jediný datový typ, který by zahrnoval všechna pole.</span><span class="sxs-lookup"><span data-stu-id="63520-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="63520-122">Datový typ konkrétní instance pole je určen následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="63520-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="63520-123">Fakt, že se jedná o pole</span><span class="sxs-lookup"><span data-stu-id="63520-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="63520-124">Pořadí (počet rozměrů) pole</span><span class="sxs-lookup"><span data-stu-id="63520-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="63520-125">Typ prvku pole</span><span class="sxs-lookup"><span data-stu-id="63520-125">The element type of the array</span></span>  
  
 <span data-ttu-id="63520-126">Konkrétně délka dané dimenze není součástí datového typu instance.</span><span class="sxs-lookup"><span data-stu-id="63520-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="63520-127">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="63520-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="63520-128">V předchozím příkladu proměnné pole `arrayA` a `arrayB` jsou považovány za stejný datový typ –, a to i v případě, že `Byte()` jsou inicializovány na jinou délku.</span><span class="sxs-lookup"><span data-stu-id="63520-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="63520-129">Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementů se liší.</span><span class="sxs-lookup"><span data-stu-id="63520-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="63520-130">Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože jejich pořadí se liší.</span><span class="sxs-lookup"><span data-stu-id="63520-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="63520-131">Proměnné `arrayD` a `arrayE` mají stejný typ – `Short(,)` – protože jejich pořadí a typy prvků jsou stejné, přestože `arrayD` ještě není inicializovaná.</span><span class="sxs-lookup"><span data-stu-id="63520-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="63520-132">Další informace o polích naleznete v tématu [Arrays](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="63520-132">For more information on arrays, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="63520-133">Typy tříd</span><span class="sxs-lookup"><span data-stu-id="63520-133">Class Types</span></span>  
 <span data-ttu-id="63520-134">Neexistuje žádný jediný datový typ obsahující všechny třídy.</span><span class="sxs-lookup"><span data-stu-id="63520-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="63520-135">I když jedna třída může dědit z jiné třídy, každý z nich je samostatný datový typ.</span><span class="sxs-lookup"><span data-stu-id="63520-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="63520-136">Více instancí stejné třídy je stejného datového typu.</span><span class="sxs-lookup"><span data-stu-id="63520-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="63520-137">Pokud přiřadíte jednu proměnnou instance třídy k druhému, nikoli pouze stejný datový typ, nasměrují na stejnou instanci třídy v paměti.</span><span class="sxs-lookup"><span data-stu-id="63520-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="63520-138">Další informace o třídách naleznete v tématu [Objects and Classes](../objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="63520-138">For more information on classes, see [Objects and Classes](../objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63520-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="63520-139">See also</span></span>

- [<span data-ttu-id="63520-140">Datové typy</span><span class="sxs-lookup"><span data-stu-id="63520-140">Data Types</span></span>](index.md)
- [<span data-ttu-id="63520-141">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="63520-141">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="63520-142">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63520-142">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="63520-143">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="63520-143">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="63520-144">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63520-144">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="63520-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="63520-145">Structures</span></span>](structures.md)
- [<span data-ttu-id="63520-146">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="63520-146">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="63520-147">Postupy: Uchování více než jedné hodnoty v proměnné</span><span class="sxs-lookup"><span data-stu-id="63520-147">How to: Hold More Than One Value in a Variable</span></span>](how-to-hold-more-than-one-value-in-a-variable.md)
