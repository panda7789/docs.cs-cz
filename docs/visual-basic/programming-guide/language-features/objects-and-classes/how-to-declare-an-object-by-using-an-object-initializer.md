---
title: 'Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 775c40cbb62272f913297d5a58914a0c82c5a7d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780832"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="128f6-102">Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128f6-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="128f6-103">Inicializátory objektů umožňují deklarovat a vytvoří instanci třídy v jediném příkazu.</span><span class="sxs-lookup"><span data-stu-id="128f6-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="128f6-104">Kromě toho můžete inicializovat jednoho nebo více členů instance ve stejnou dobu bez vyvolání konstruktoru s parametry.</span><span class="sxs-lookup"><span data-stu-id="128f6-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="128f6-105">Použijete-li vytvořit instanci typu s názvem inicializátoru objektu, je zavolán výchozí konstruktor pro třídu, za nímž následuje inicializace členů určené ve vámi určeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="128f6-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="128f6-106">Následující postup ukazuje, jak vytvořit instanci `Student` třídy třemi různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="128f6-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="128f6-107">Třída má křestní jméno, příjmení a vlastnosti třídy rok, mimo jiné.</span><span class="sxs-lookup"><span data-stu-id="128f6-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="128f6-108">Všechny tři deklarace vytvoří novou instanci třídy `Student`, s vlastností `First` nastavena na "Michael", vlastnost `Last` nastavená na "Tucker" a všechny ostatní členové nastavená na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="128f6-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="128f6-109">Výsledek deklaraci v postupu je ekvivalentní v následujícím příkladu, který nepoužívá inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="128f6-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="128f6-110">Pro implementaci `Student` najdete v tématu [jak: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="128f6-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="128f6-111">Můžete zkopírovat kód z tohoto tématu nastavit třídy a vytvořit seznam `Student` pro práci s objekty.</span><span class="sxs-lookup"><span data-stu-id="128f6-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="128f6-112">Chcete-li vytvořit objekt s názvem třídy pomocí inicializátoru objektů</span><span class="sxs-lookup"><span data-stu-id="128f6-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="128f6-113">Začněte deklarace, jako kdyby jste naplánovali použijte konstruktor.</span><span class="sxs-lookup"><span data-stu-id="128f6-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="128f6-114">Klíčové slovo `With`následovaný inicializačního seznamu ve složených závorkách.</span><span class="sxs-lookup"><span data-stu-id="128f6-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="128f6-115">V seznamu inicializace zahrňte každou vlastnost, kterou chcete inicializovat a přiřadit je počáteční hodnota.</span><span class="sxs-lookup"><span data-stu-id="128f6-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="128f6-116">Název vlastnosti je začínat tečkou.</span><span class="sxs-lookup"><span data-stu-id="128f6-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="128f6-117">Můžete inicializovat jednoho nebo více členů třídy.</span><span class="sxs-lookup"><span data-stu-id="128f6-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="128f6-118">Alternativně můžete deklarovat novou instanci třídy a pak do něj přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="128f6-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="128f6-119">Nejprve deklarujte instanci `Student`:</span><span class="sxs-lookup"><span data-stu-id="128f6-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="128f6-120">Zahájit vytvoření instance `Student` běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="128f6-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="128f6-121">Typ `With` a potom inicializátoru objektu inicializovat jednoho nebo více členů nové instance.</span><span class="sxs-lookup"><span data-stu-id="128f6-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="128f6-122">Definice v předchozím kroku může zjednodušit vynecháním `As Student`.</span><span class="sxs-lookup"><span data-stu-id="128f6-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="128f6-123">Pokud to uděláte, kompilátor zjistí, že `student3` je instance `Student` pomocí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="128f6-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="128f6-124">Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="128f6-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128f6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="128f6-125">See also</span></span>

- [<span data-ttu-id="128f6-126">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="128f6-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="128f6-127">Postupy: Vytvoření seznamu položek</span><span class="sxs-lookup"><span data-stu-id="128f6-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="128f6-128">Inicializátory objektů: Pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="128f6-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="128f6-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="128f6-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
