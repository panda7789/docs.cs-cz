---
title: "New – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="38cb5-102">New – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38cb5-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="38cb5-103">Zavádí `New` klauzuli k vytvoření nové instance objektu, určuje omezení konstruktor parametr typu nebo identifikuje `Sub` postupu jako konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="38cb5-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38cb5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38cb5-104">Remarks</span></span>  
 <span data-ttu-id="38cb5-105">V deklaraci nebo příkaz přiřazení `New` klauzuli musí být zadána definované třídy, ze kterého lze vytvořit instance.</span><span class="sxs-lookup"><span data-stu-id="38cb5-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="38cb5-106">To znamená, že třída musí vystavit jeden nebo více konstruktory, kteří mohou přistupovat k volání kódu.</span><span class="sxs-lookup"><span data-stu-id="38cb5-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="38cb5-107">Můžete použít `New` klauzuli v deklaraci příkaz nebo příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="38cb5-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="38cb5-108">Při spuštění příkazu, zavolá vhodný konstruktor pro zadanou třídu předání argumentů, které jste zadali.</span><span class="sxs-lookup"><span data-stu-id="38cb5-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="38cb5-109">Následující příklad ukazuje to tak, že vytvoříte instancí `Customer` třídu, která má dva konstruktory, jeden, které nepřijímá žádné parametry a ten, který použije parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="38cb5-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="38cb5-110">Vzhledem k tomu, že pole jsou třídy, `New` můžete vytvořit novou instanci pole, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="38cb5-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="38cb5-111">Modul CLR (CLR), vyvolá <xref:System.OutOfMemoryException> chyby, pokud je nedostatek paměti k vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="38cb5-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38cb5-112">`New` – Klíčové slovo se také používá v seznamech typu parametr k určení, zda zadaný typ musí vystavit přístupné bezparametrový konstruktor.</span><span class="sxs-lookup"><span data-stu-id="38cb5-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="38cb5-113">Další informace o parametry typu a omezení najdete v tématu [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="38cb5-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="38cb5-114">Chcete-li vytvořit proceduru konstruktor pro třídu, nastavte název `Sub` postup `New` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="38cb5-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="38cb5-115">Další informace najdete v tématu [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="38cb5-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="38cb5-116">`New` – Klíčové slovo lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="38cb5-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="38cb5-117">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="38cb5-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="38cb5-118">Z</span><span class="sxs-lookup"><span data-stu-id="38cb5-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="38cb5-119">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="38cb5-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="38cb5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="38cb5-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="38cb5-121">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="38cb5-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="38cb5-122">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="38cb5-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="38cb5-123">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38cb5-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="38cb5-124">Doba života objektu: Objekty vytváření a zničení</span><span class="sxs-lookup"><span data-stu-id="38cb5-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
