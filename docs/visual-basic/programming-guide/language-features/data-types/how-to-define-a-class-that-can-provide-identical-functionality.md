---
title: "Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c8594a23391793e1be3d969f7eacc199cbc6caa9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="e927e-102">Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e927e-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="e927e-103">Můžete definice třídy, ze kterého můžete vytvořit objekty, které poskytují identické funkce pro různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="e927e-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="e927e-104">K tomuto účelu můžete zadat jednu nebo několik *parametry typu* v definici.</span><span class="sxs-lookup"><span data-stu-id="e927e-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="e927e-105">Třída může pak sloužit jako šablona pro objekty, které používají různé datové typy.</span><span class="sxs-lookup"><span data-stu-id="e927e-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="e927e-106">Třídy definované tímto způsobem se nazývá *– obecná třída*.</span><span class="sxs-lookup"><span data-stu-id="e927e-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="e927e-107">Výhodou definování obecné třídy je, že definujete jen jednou a váš kód můžete použít k vytvoření mnoho objektů, které používají širokou škálu datové typy.</span><span class="sxs-lookup"><span data-stu-id="e927e-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="e927e-108">To vede k lepší výkon než definice třídy s `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="e927e-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="e927e-109">Kromě třídy můžete také definovat a použít obecné struktury, rozhraní, postupy a delegáti.</span><span class="sxs-lookup"><span data-stu-id="e927e-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="e927e-110">Chcete-li definovat třídu s parametrem typu</span><span class="sxs-lookup"><span data-stu-id="e927e-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="e927e-111">Definujte třídu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="e927e-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="e927e-112">Přidat `(Of` *typeparameter* `)` ihned po název třídy pro určení typu parametru.</span><span class="sxs-lookup"><span data-stu-id="e927e-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="e927e-113">Pokud máte více než jeden parametr typu, vytvořte seznam oddělený čárkami do závorek.</span><span class="sxs-lookup"><span data-stu-id="e927e-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="e927e-114">Neopakujte `Of` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e927e-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="e927e-115">Pokud váš kód provádí operace pro parametr typu než jednoduché přiřazení, použijte tento parametr typu s `As` klauzule chcete přidat jeden nebo více *omezení*.</span><span class="sxs-lookup"><span data-stu-id="e927e-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="e927e-116">Omezení zaručuje, že typ zadaný pro parametr typu splňuje požadavek například následující:</span><span class="sxs-lookup"><span data-stu-id="e927e-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="e927e-117">Podporuje operace, jako například `>`, který provádí kódu</span><span class="sxs-lookup"><span data-stu-id="e927e-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="e927e-118">Podporuje členem, jako je například metoda, který přistupuje k kódu</span><span class="sxs-lookup"><span data-stu-id="e927e-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="e927e-119">Zpřístupní konstruktor bez parametrů</span><span class="sxs-lookup"><span data-stu-id="e927e-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="e927e-120">Pokud nezadáte žádné omezení, jenom operace a členy můžete použít kódu jsou jsou podporovány [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e927e-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="e927e-121">Další informace najdete v tématu [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="e927e-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="e927e-122">Identifikovat každých třída člena, který je třeba deklarovat s zadaný typ a deklarujte ji `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="e927e-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="e927e-123">To platí pro interní úložiště, postup parametry a návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e927e-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="e927e-124">Ujistěte se, váš kód používá jenom operace a metody, které jsou podporovány všechny datový typ, můžete zadat do `itemType`.</span><span class="sxs-lookup"><span data-stu-id="e927e-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="e927e-125">Následující příklad definuje třídu, která spravuje seznam velmi jednoduché.</span><span class="sxs-lookup"><span data-stu-id="e927e-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="e927e-126">V poli interní drží seznamu `items`a pomocí kódu můžou deklarovat datový typ seznamu elementů.</span><span class="sxs-lookup"><span data-stu-id="e927e-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="e927e-127">Parametrizované konstruktor umožňuje použití kódu nastavit horní mez `items`, a nastaví výchozí konstruktor, to do 9 (pro celkem 10 položek).</span><span class="sxs-lookup"><span data-stu-id="e927e-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     <span data-ttu-id="e927e-128">Je možné deklarovat vytvoření třídy z `simpleList` pro uložení seznamu `Integer` hodnoty, jiné třídy pro uložení seznamu `String` hodnoty a druhý pro uložení `Date` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e927e-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="e927e-129">S výjimkou datový typ ze seznamu členů chovají stejně jako objekty vytvořené z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="e927e-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="e927e-130">Argument typu, který pomocí kódu poskytuje `itemType` může být například vnitřního typu `Boolean` nebo `Double`, struktury, výčet nebo libovolného typu třídy, včetně ten, který definuje vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e927e-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="e927e-131">Můžete otestovat třída `simpleList` následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="e927e-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e927e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e927e-132">See Also</span></span>  
 [<span data-ttu-id="e927e-133">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e927e-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="e927e-134">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e927e-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="e927e-135">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="e927e-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="e927e-136">Z</span><span class="sxs-lookup"><span data-stu-id="e927e-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="e927e-137">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="e927e-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="e927e-138">Postupy: Použití obecné třídy</span><span class="sxs-lookup"><span data-stu-id="e927e-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="e927e-139">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="e927e-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
