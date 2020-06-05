---
title: 'Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy'
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
ms.openlocfilehash: 3b1f47250453c32735d633b98da0bd0ddb1ed5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393854"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="7fe6e-102">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7fe6e-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="7fe6e-103">Můžete definovat třídu, ze které můžete vytvářet objekty, které poskytují stejné funkce pro různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="7fe6e-104">Chcete-li to provést, zadejte v definici jeden nebo více *parametrů typu* .</span><span class="sxs-lookup"><span data-stu-id="7fe6e-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="7fe6e-105">Třída pak může sloužit jako šablona pro objekty, které používají různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="7fe6e-106">Třída definovaná tímto způsobem se nazývá *Obecná třída*.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="7fe6e-107">Výhodou definování obecné třídy je, že ji definujete pouze jednou a váš kód jej může použít k vytvoření mnoha objektů, které používají širokou škálu datových typů.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="7fe6e-108">Výsledkem je lepší výkon než definování třídy s `Object` typem.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="7fe6e-109">Kromě tříd můžete také definovat a používat obecné struktury, rozhraní, procedury a delegáty.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="7fe6e-110">Definování třídy s parametrem typu</span><span class="sxs-lookup"><span data-stu-id="7fe6e-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="7fe6e-111">Definujte třídu normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="7fe6e-112">Přidejte `(Of` *typeparameter* `)` hned za název třídy pro určení parametru typu.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="7fe6e-113">Pokud máte více než jeden parametr typu, vytvořte v závorkách seznam oddělený čárkami.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="7fe6e-114">Klíčové slovo neopakuje `Of` .</span><span class="sxs-lookup"><span data-stu-id="7fe6e-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="7fe6e-115">Pokud váš kód provádí operace s parametrem typu, který je jiný než jednoduché přiřazení, použijte tento parametr typu s `As` klauzulí k přidání jednoho nebo více *omezení*.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="7fe6e-116">Omezení zaručuje, že typ zadaný pro tento parametr typu splňuje požadavky, jako například následující:</span><span class="sxs-lookup"><span data-stu-id="7fe6e-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="7fe6e-117">Podporuje operaci, například `>` , kterou váš kód provádí</span><span class="sxs-lookup"><span data-stu-id="7fe6e-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="7fe6e-118">Podporuje člena, jako je například metoda, ke které váš kód přistupuje.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="7fe6e-119">Zpřístupňuje konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="7fe6e-120">Pokud nezadáte žádná omezení, mohou být použity pouze operace a členy, které váš kód podporuje, pomocí [datového typu objektu](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="7fe6e-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="7fe6e-121">Další informace najdete v tématu [seznam typů](../../../language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="7fe6e-121">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="7fe6e-122">Identifikujte všechny členy třídy, které mají být deklarovány se zadaným typem a deklarujete je `As` `typeparameter` .</span><span class="sxs-lookup"><span data-stu-id="7fe6e-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="7fe6e-123">To platí pro interní úložiště, parametry procedury a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="7fe6e-124">Ujistěte se, že váš kód používá pouze operace a metody, které jsou podporovány jakýmkoli datovým typem, který může zadat `itemType` .</span><span class="sxs-lookup"><span data-stu-id="7fe6e-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="7fe6e-125">Následující příklad definuje třídu, která spravuje velmi jednoduchý seznam.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="7fe6e-126">Obsahuje seznam interního pole `items` a kód using může deklarovat datový typ prvků seznamu.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="7fe6e-127">Parametrizovaný konstruktor umožňuje použití kódu pro nastavení horní meze `items` a konstruktor bez parametrů nastaví tuto hodnotu na 9 (celkem 10 položek).</span><span class="sxs-lookup"><span data-stu-id="7fe6e-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="7fe6e-128">Můžete deklarovat třídu z `simpleList` , aby obsahovala seznam `Integer` hodnot, jinou třídu pro uložení seznamu `String` hodnot a další pro uložení `Date` hodnot.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="7fe6e-129">S výjimkou datového typu seznamů členů se objekty vytvořené ze všech těchto tříd chovají stejně.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="7fe6e-130">Argument typu, který používá kód `itemType` , může být vnitřní typ, například `Boolean` nebo `Double` , struktura, výčet nebo jakýkoli typ třídy, včetně toho, který definuje vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="7fe6e-131">Třídu lze otestovat `simpleList` pomocí následujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="7fe6e-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="7fe6e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fe6e-132">See also</span></span>

- [<span data-ttu-id="7fe6e-133">Datové typy</span><span class="sxs-lookup"><span data-stu-id="7fe6e-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="7fe6e-134">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fe6e-134">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="7fe6e-135">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="7fe6e-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="7fe6e-136">Tohoto</span><span class="sxs-lookup"><span data-stu-id="7fe6e-136">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="7fe6e-137">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="7fe6e-137">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="7fe6e-138">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="7fe6e-138">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="7fe6e-139">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="7fe6e-139">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
