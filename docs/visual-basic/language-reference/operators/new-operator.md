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
ms.openlocfilehash: 0fe511b2c16681d7bab7eeda7c121fcbbaa2f5dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603636"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="12096-102">New – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12096-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="12096-103">Zavádí `New` klauzuli k vytvoření nové instance objektu, určuje omezení konstruktor parametr typu nebo identifikuje `Sub` postupu jako konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="12096-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12096-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12096-104">Remarks</span></span>  
 <span data-ttu-id="12096-105">V deklaraci nebo příkaz přiřazení `New` klauzuli musí být zadána definované třídy, ze kterého lze vytvořit instance.</span><span class="sxs-lookup"><span data-stu-id="12096-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="12096-106">To znamená, že třída musí vystavit jeden nebo více konstruktory, kteří mohou přistupovat k volání kódu.</span><span class="sxs-lookup"><span data-stu-id="12096-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="12096-107">Můžete použít `New` klauzuli v deklaraci příkaz nebo příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="12096-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="12096-108">Při spuštění příkazu, zavolá vhodný konstruktor pro zadanou třídu předání argumentů, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="12096-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="12096-109">Následující příklad ukazuje to tak, že vytvoříte instancí `Customer` třídu, která má dva konstruktory, jeden, které nepřijímá žádné parametry a ten, který použije parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="12096-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="12096-110">Vzhledem k tomu, že pole jsou třídy, `New` můžete vytvořit novou instanci pole, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="12096-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="12096-111">Modul CLR (CLR), vyvolá <xref:System.OutOfMemoryException> chyby, pokud je nedostatek paměti k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="12096-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12096-112">`New` – Klíčové slovo se také používá v seznamech typu parametr k určení, zda zadaný typ musí vystavit přístupné bezparametrový konstruktor.</span><span class="sxs-lookup"><span data-stu-id="12096-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="12096-113">Další informace o parametry typu a omezení najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="12096-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="12096-114">Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="12096-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="12096-115">Další informace najdete v tématu [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="12096-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="12096-116">`New` – Klíčové slovo lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="12096-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="12096-117">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="12096-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="12096-118">z</span><span class="sxs-lookup"><span data-stu-id="12096-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="12096-119">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="12096-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="12096-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="12096-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="12096-121">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="12096-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="12096-122">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="12096-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="12096-123">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12096-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="12096-124">Doba života objektu: Vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="12096-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
