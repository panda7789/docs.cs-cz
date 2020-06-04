---
title: 'Postupy: Deklarace objektu pomocí inicializátoru objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404872"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="09b64-102">Postupy: Deklarace objektu pomocí inicializátoru objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09b64-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="09b64-103">Inicializátory objektů umožňují deklarovat a vytvořit instanci instance třídy v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="09b64-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="09b64-104">Kromě toho můžete inicializovat jednoho nebo více členů instance současně bez vyvolání parametrizovaného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="09b64-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="09b64-105">Použijete-li inicializátor objektu k vytvoření instance pojmenovaného typu, je volán konstruktor bez parametrů pro třídu, následovaný inicializací zadaných členů v pořadí, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="09b64-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="09b64-106">Následující postup ukazuje, jak vytvořit instanci `Student` třídy třemi různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="09b64-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="09b64-107">Třída má jako křestní jméno, příjmení a vlastnosti roku třídy mezi ostatními.</span><span class="sxs-lookup"><span data-stu-id="09b64-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="09b64-108">Každá ze tří deklarací vytvoří novou instanci třídy `Student` s vlastností `First` nastavenou na "Michael", vlastnost `Last` nastavenou na "Tucker" a všechny ostatní členy nastavené na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="09b64-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="09b64-109">Výsledek každé deklarace v proceduře je ekvivalentní následujícímu příkladu, který nepoužívá inicializátor objektu.</span><span class="sxs-lookup"><span data-stu-id="09b64-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="09b64-110">Implementaci `Student` třídy naleznete v tématu [How to: Create a list of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="09b64-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="09b64-111">Můžete zkopírovat kód z tohoto tématu a nastavit třídu a vytvořit seznam `Student` objektů, se kterými chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="09b64-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="09b64-112">Vytvoření objektu pojmenované třídy pomocí inicializátoru objektu</span><span class="sxs-lookup"><span data-stu-id="09b64-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="09b64-113">Zahajte deklaraci, jako kdybyste naplánovali použití konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="09b64-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="09b64-114">Zadejte klíčové slovo `With` následovaný inicializačním seznamem ve složených závorkách.</span><span class="sxs-lookup"><span data-stu-id="09b64-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="09b64-115">V inicializačním seznamu Zahrňte všechny vlastnosti, které chcete inicializovat, a přiřaďte k ní počáteční hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09b64-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="09b64-116">Před název vlastnosti je uvedena tečka.</span><span class="sxs-lookup"><span data-stu-id="09b64-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="09b64-117">Můžete inicializovat jednoho nebo více členů třídy.</span><span class="sxs-lookup"><span data-stu-id="09b64-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="09b64-118">Alternativně můžete deklarovat novou instanci třídy a pak jí přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09b64-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="09b64-119">Nejdřív deklarujte instanci `Student` :</span><span class="sxs-lookup"><span data-stu-id="09b64-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="09b64-120">Začněte vytvářet instanci `Student` normálním způsobem.</span><span class="sxs-lookup"><span data-stu-id="09b64-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="09b64-121">Zadejte `With` a pak inicializátor objektu pro inicializaci jednoho nebo více členů nové instance.</span><span class="sxs-lookup"><span data-stu-id="09b64-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="09b64-122">Definici v předchozím kroku můžete zjednodušit tím, že ji vynecháte `As Student` .</span><span class="sxs-lookup"><span data-stu-id="09b64-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="09b64-123">Pokud to uděláte, kompilátor určí, že `student3` je instancí aplikace `Student` pomocí odvození místního typu.</span><span class="sxs-lookup"><span data-stu-id="09b64-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="09b64-124">Další informace naleznete v tématu [odvození místního typu](../variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="09b64-124">For more information, see [Local Type Inference](../variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b64-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="09b64-125">See also</span></span>

- [<span data-ttu-id="09b64-126">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="09b64-126">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="09b64-127">Postupy: Vytvoření seznamu položek</span><span class="sxs-lookup"><span data-stu-id="09b64-127">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="09b64-128">Inicializátory objektů: pojmenované a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="09b64-128">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="09b64-129">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="09b64-129">Anonymous Types</span></span>](anonymous-types.md)
