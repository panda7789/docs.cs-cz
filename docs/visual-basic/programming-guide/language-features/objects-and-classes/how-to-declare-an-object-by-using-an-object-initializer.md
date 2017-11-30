---
title: "Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c818765cbeac7a3080ee666d464052493e5bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="f684e-102">Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f684e-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="f684e-103">Inicializátory objektů umožňují deklarace a vytvoří instanci třídy v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="f684e-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="f684e-104">Navíc můžete inicializovat jednoho nebo více členů instance ve stejnou dobu, bez vyvolání parametrizované konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f684e-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="f684e-105">Při vytvoření instance typu s názvem pomocí inicializátoru objektu, se nazývá výchozí konstruktor pro třídu, za nímž následuje inicializace určené členů v pořadí, ve kterém zadáte.</span><span class="sxs-lookup"><span data-stu-id="f684e-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="f684e-106">Následující postup ukazuje, jak vytvořit instanci `Student` třída třemi různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f684e-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="f684e-107">Třída nemá křestní jméno, příjmení a vlastnosti třídy roku, mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="f684e-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="f684e-108">Všechny tři deklarace vytvoří novou instanci třídy `Student`, s vlastností `First` nastavena na "Michael", vlastnost `Last` nastavený na "Tucker", a všechny ostatní členy na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f684e-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="f684e-109">Výsledek každé deklarace v postupu je ekvivalentní v následujícím příkladu, který nepoužívá inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="f684e-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 <span data-ttu-id="f684e-110">Implementace `Student` třídy najdete v tématu [postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="f684e-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="f684e-111">Můžete zkopírovat kód z tohoto tématu nastavit třídy a vytvoří seznam `Student` objekty, které chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="f684e-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="f684e-112">Chcete-li vytvořit objekt s názvem třídy pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="f684e-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="f684e-113">Začněte deklaraci, jako když plánujete použít konstruktor.</span><span class="sxs-lookup"><span data-stu-id="f684e-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="f684e-114">Zadejte klíčové slovo `With`, za nímž následují seznamu k inicializaci složené závorky.</span><span class="sxs-lookup"><span data-stu-id="f684e-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="f684e-115">V seznamu inicializace zahrňte každou vlastnost, kterou chcete inicializovat a přiřadit výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f684e-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="f684e-116">Název vlastnosti je začínat tečkou.</span><span class="sxs-lookup"><span data-stu-id="f684e-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     <span data-ttu-id="f684e-117">Jeden nebo více členů třídy můžete inicializovat.</span><span class="sxs-lookup"><span data-stu-id="f684e-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="f684e-118">Alternativně můžete deklarovat novou instanci třídy a pak do ní přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f684e-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="f684e-119">Nejprve deklarujte instanci `Student`:</span><span class="sxs-lookup"><span data-stu-id="f684e-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="f684e-120">Zahájit vytvoření instance `Student` běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f684e-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="f684e-121">Typ `With` a pak inicializátoru objektu k inicializaci nové instance jednoho nebo více členů.</span><span class="sxs-lookup"><span data-stu-id="f684e-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  <span data-ttu-id="f684e-122">Definice v předchozím kroku můžete zjednodušit tím vynechání `As Student`.</span><span class="sxs-lookup"><span data-stu-id="f684e-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="f684e-123">Pokud to uděláte, kompilátor zjistí, `student3` je instance `Student` pomocí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="f684e-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     <span data-ttu-id="f684e-124">Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f684e-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f684e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="f684e-125">See Also</span></span>  
 [<span data-ttu-id="f684e-126">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="f684e-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="f684e-127">Postupy: vytvoření seznamu položek</span><span class="sxs-lookup"><span data-stu-id="f684e-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [<span data-ttu-id="f684e-128">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f684e-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="f684e-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="f684e-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
