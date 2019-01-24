---
title: New – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 0e8ec5877cba5f5cf97e1677460da06fd87cce1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587551"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="d424e-102">New – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d424e-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="d424e-103">Zavádí `New` klauzule, která vytvoří novou instanci objektu, určuje omezení konstruktoru u parametru typu nebo identifikuje `Sub` postupu jako konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="d424e-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d424e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d424e-104">Remarks</span></span>  
 <span data-ttu-id="d424e-105">V deklaraci nebo příkazu přiřazení `New` klauzuli musí být zadána s definicí třídy, ze kterého lze vytvořit instance.</span><span class="sxs-lookup"><span data-stu-id="d424e-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="d424e-106">To znamená, že třída musí vystavit jeden nebo více konstruktorů, které volající kód může přistupovat.</span><span class="sxs-lookup"><span data-stu-id="d424e-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="d424e-107">Můžete použít `New` klauzuli v příkazu deklarace nebo příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d424e-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="d424e-108">Když příkaz spustíte, zavolá odpovídající konstruktor zadané třídy, prochází žádné argumenty, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="d424e-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="d424e-109">Následující příklad ukazuje to ve vytváření instancí `Customer` třídu, která má dva konstruktory, která nepřijímá žádné parametry a ten, který se použije parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="d424e-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="d424e-110">Protože pole jsou třídy, `New` můžete vytvořit novou instanci pole, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d424e-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="d424e-111">Vyvolá common language runtime (CLR) <xref:System.OutOfMemoryException> chyby, pokud není dostatek paměti k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="d424e-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d424e-112">`New` – Klíčové slovo se také používá v seznamech parametrů typu k určení, že zadaný typ musí vystavit dostupný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="d424e-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="d424e-113">Další informace o parametry typu a omezení, najdete v části [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d424e-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="d424e-114">Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d424e-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="d424e-115">Další informace najdete v tématu [doba života objektu: Způsob vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="d424e-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="d424e-116">`New` – Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="d424e-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d424e-117">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="d424e-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="d424e-118">z</span><span class="sxs-lookup"><span data-stu-id="d424e-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="d424e-119">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="d424e-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d424e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d424e-120">See also</span></span>
- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="d424e-121">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d424e-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="d424e-122">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="d424e-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="d424e-123">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d424e-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d424e-124">Doba života objektu: Způsob vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="d424e-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
