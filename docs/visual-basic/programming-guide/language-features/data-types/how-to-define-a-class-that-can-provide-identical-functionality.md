---
title: 'Postupy: Definujte třídu, která poskytne identické funkce pro různé datové typy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 9121041f936c091cda0e2af41b4f5be8d826d582
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318441"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="30bce-102">Postupy: Definujte třídu, která poskytne identické funkce pro různé datové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30bce-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="30bce-103">Můžete definovat třídu z které můžete vytvořit objekty, které poskytne identické funkce pro různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="30bce-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="30bce-104">K tomuto účelu můžete zadat jednu nebo víc *parametry typu* v definici.</span><span class="sxs-lookup"><span data-stu-id="30bce-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="30bce-105">Třída pak může sloužit jako šablona pro objekty, které používají různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="30bce-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="30bce-106">Třída definována tímto způsobem se nazývá *obecnou třídu*.</span><span class="sxs-lookup"><span data-stu-id="30bce-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="30bce-107">Výhodou definování obecné třídy je, že definujete pouze jednou a váš kód můžete použít k vytvoření mnoho objektů, které používají širokou škálu datových typů.</span><span class="sxs-lookup"><span data-stu-id="30bce-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="30bce-108">Výsledkem je lepší výkon než definováním třídy s `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="30bce-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="30bce-109">Kromě tříd můžete také definovat a použijte obecné struktury, rozhraní, postupy a delegáti.</span><span class="sxs-lookup"><span data-stu-id="30bce-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="30bce-110">Chcete-li definovat třídu s parametrem typu</span><span class="sxs-lookup"><span data-stu-id="30bce-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="30bce-111">Definování třídy obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="30bce-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="30bce-112">Přidat `(Of` *typeparameter* `)` bezprostředně za název třídy pro zadání parametru typu.</span><span class="sxs-lookup"><span data-stu-id="30bce-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="30bce-113">Pokud máte více než jeden parametr typu, vytvořte seznam oddělený čárkami v závorkách.</span><span class="sxs-lookup"><span data-stu-id="30bce-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="30bce-114">Neopakovat `Of` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="30bce-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="30bce-115">Pokud váš kód provádí operace u parametru typu jiného než jednoduché přiřazení, použijte tento parametr typu `As` klauzule, které chcete přidat jeden nebo více *omezení*.</span><span class="sxs-lookup"><span data-stu-id="30bce-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="30bce-116">Omezení zaručuje, že na typ zadaný pro parametr typu splňuje požadavek, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="30bce-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="30bce-117">Podporuje operace, jako například `>`, který váš kód provádí</span><span class="sxs-lookup"><span data-stu-id="30bce-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="30bce-118">Podporuje členu, například metody, které váš kód přistupuje k</span><span class="sxs-lookup"><span data-stu-id="30bce-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="30bce-119">Zpřístupňuje konstruktor bez parametrů</span><span class="sxs-lookup"><span data-stu-id="30bce-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="30bce-120">Pokud nezadáte žádné omezení, pouze konzole operations Console a váš kód může použít členy jsou jsou podporovány [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="30bce-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="30bce-121">Další informace najdete v tématu [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="30bce-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="30bce-122">Každý člen třídy, který je deklarován s zadaný typ identifikovat a deklarujte ji `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="30bce-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="30bce-123">To platí pro interní úložiště, postup parametrů a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="30bce-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="30bce-124">Ujistěte se, váš kód používá pouze operace a metody, které jsou podporovány libovolného datového typu, mohou poskytnout `itemType`.</span><span class="sxs-lookup"><span data-stu-id="30bce-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="30bce-125">Následující příklad definuje třídu, která spravuje velmi jednoduchý seznam.</span><span class="sxs-lookup"><span data-stu-id="30bce-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="30bce-126">Obsahuje seznam v poli interní `items`a pomocí kódu můžete deklarovat typ dat prvků seznamu.</span><span class="sxs-lookup"><span data-stu-id="30bce-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="30bce-127">Umožňuje do parametrizovaného konstruktoru na pomocí kódu pro nastavení horní mez `items`, a nastaví výchozí konstruktor do 9 (pro celkem 10 položek).</span><span class="sxs-lookup"><span data-stu-id="30bce-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="30bce-128">Je možné deklarovat třídu z `simpleList` k uložení seznamu `Integer` hodnoty, jiné třídy pro uložení seznamu `String` hodnoty a druhý pro uložení `Date` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="30bce-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="30bce-129">S výjimkou datový typ seznam členů chovají stejně jako objekty vytvořené z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="30bce-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="30bce-130">Argument typu, který pomocí kódu poskytuje `itemType` vnitřní typ může být například `Boolean` nebo `Double`, strukturu, výčet nebo libovolný typ třídy, včetně ten, který definuje vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="30bce-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="30bce-131">Třídu můžete otestovat `simpleList` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="30bce-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="30bce-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30bce-132">See also</span></span>

- [<span data-ttu-id="30bce-133">Datové typy</span><span class="sxs-lookup"><span data-stu-id="30bce-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="30bce-134">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30bce-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="30bce-135">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="30bce-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="30bce-136">z</span><span class="sxs-lookup"><span data-stu-id="30bce-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="30bce-137">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="30bce-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="30bce-138">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="30bce-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="30bce-139">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="30bce-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
