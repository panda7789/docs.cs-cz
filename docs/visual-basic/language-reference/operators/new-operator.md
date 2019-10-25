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
ms.openlocfilehash: c0870f4b056658a22928769c369024cdda24f354
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799035"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="232d4-102">New – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232d4-102">New Operator (Visual Basic)</span></span>

<span data-ttu-id="232d4-103">Zavádí klauzuli `New` pro vytvoření nové instance objektu, určuje omezení konstruktoru pro parametr typu nebo identifikuje `Sub` proceduru jako konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="232d4-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="232d4-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="232d4-104">Remarks</span></span>

<span data-ttu-id="232d4-105">V deklaraci nebo příkazu přiřazení musí klauzule `New` určovat definovanou třídu, ze které lze instanci vytvořit.</span><span class="sxs-lookup"><span data-stu-id="232d4-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="232d4-106">To znamená, že třída musí vystavit jeden nebo více konstruktorů, ke kterým může přistupovat volající kód.</span><span class="sxs-lookup"><span data-stu-id="232d4-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="232d4-107">V příkazu deklarace nebo příkazu přiřazení můžete použít klauzuli `New`.</span><span class="sxs-lookup"><span data-stu-id="232d4-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="232d4-108">Při spuštění příkazu volá příslušný konstruktor zadané třídy a předává všechny argumenty, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="232d4-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="232d4-109">Následující příklad ukazuje to vytvořením instancí třídy `Customer`, která má dva konstruktory, jeden, který přebírá žádné parametry a jeden, který přijímá řetězcový parametr:</span><span class="sxs-lookup"><span data-stu-id="232d4-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="232d4-110">Vzhledem k tomu, že pole jsou třídy, `New` mohou vytvořit novou instanci pole, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="232d4-110">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="232d4-111">Modul CLR (Common Language Runtime) vyvolá chybu <xref:System.OutOfMemoryException>, pokud není k dispozici dostatek paměti pro vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="232d4-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="232d4-112">Klíčové slovo `New` se používá také v seznamech parametrů typu k určení toho, že zadaný typ musí vystavit přístupný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="232d4-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="232d4-113">Další informace o parametrech typu a omezeních najdete v tématu [seznam typů](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="232d4-113">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="232d4-114">Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury na klíčové slovo `New`.</span><span class="sxs-lookup"><span data-stu-id="232d4-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="232d4-115">Další informace naleznete v tématu [Doba života objektu: vytváření a zničení objektů](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="232d4-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="232d4-116">Klíčové slovo `New` lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="232d4-116">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="232d4-117">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="232d4-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="232d4-118">Tohoto</span><span class="sxs-lookup"><span data-stu-id="232d4-118">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="232d4-119">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="232d4-119">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="232d4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="232d4-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="232d4-121">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="232d4-121">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="232d4-122">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="232d4-122">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="232d4-123">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="232d4-123">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="232d4-124">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="232d4-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
