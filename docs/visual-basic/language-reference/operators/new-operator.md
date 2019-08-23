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
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955880"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="3666b-102">New – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3666b-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="3666b-103">Zavádí klauzuli pro vytvoření nové instance objektu, určuje omezení konstruktoru pro parametr typu nebo `Sub` identifikuje proceduru jako konstruktor třídy. `New`</span><span class="sxs-lookup"><span data-stu-id="3666b-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3666b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3666b-104">Remarks</span></span>  
 <span data-ttu-id="3666b-105">V deklaraci nebo příkazu `New` přiřazení musí klauzule určovat definovanou třídu, ze které lze instanci vytvořit.</span><span class="sxs-lookup"><span data-stu-id="3666b-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="3666b-106">To znamená, že třída musí vystavit jeden nebo více konstruktorů, ke kterým může přistupovat volající kód.</span><span class="sxs-lookup"><span data-stu-id="3666b-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="3666b-107">Můžete použít `New` klauzuli v příkazu deklarace nebo v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3666b-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="3666b-108">Při spuštění příkazu volá příslušný konstruktor zadané třídy a předává všechny argumenty, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="3666b-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="3666b-109">Následující příklad ukazuje to vytvořením instancí `Customer` třídy, která má dva konstruktory, jeden, který přebírá žádné parametry a jeden, který přijímá řetězcový parametr.</span><span class="sxs-lookup"><span data-stu-id="3666b-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="3666b-110">Vzhledem k tomu, že `New` pole jsou třídy, může vytvořit novou instanci pole, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="3666b-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="3666b-111">Modul CLR (Common Language Runtime) vyvolá <xref:System.OutOfMemoryException> chybu, pokud není k dispozici dostatek paměti pro vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="3666b-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3666b-112">`New` Klíčové slovo se používá také v seznamech parametrů typu k určení toho, že zadaný typ musí vystavit přístupný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="3666b-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="3666b-113">Další informace o parametrech typu a omezeních najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="3666b-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="3666b-114">Chcete-li vytvořit proceduru konstruktoru pro třídu, nastavte název `Sub` procedury `New` na klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3666b-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="3666b-115">Další informace najdete v tématu [životnost objektu: Způsob vytváření a zničení](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)objektů.</span><span class="sxs-lookup"><span data-stu-id="3666b-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="3666b-116">`New` Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="3666b-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3666b-117">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="3666b-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="3666b-118">Tohoto</span><span class="sxs-lookup"><span data-stu-id="3666b-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="3666b-119">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="3666b-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3666b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3666b-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="3666b-121">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3666b-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="3666b-122">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="3666b-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="3666b-123">Obecné typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3666b-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="3666b-124">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="3666b-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
