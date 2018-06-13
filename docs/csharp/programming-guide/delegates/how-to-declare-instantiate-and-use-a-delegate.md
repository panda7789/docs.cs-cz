---
title: 'Postupy: Deklarování, vytváření instancí a použití delegáta (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 19e5883135d65a648bb6afb74a475b761f572a95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333970"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="c078e-102">Postupy: Deklarování, vytváření instancí a použití delegáta (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c078e-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="c078e-103">V jazyce C# 1.0 nebo novější lze deklarovat delegáti, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c078e-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="c078e-104">C# 2.0 poskytuje jednodušší způsob, jak zapsat předchozí deklaraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c078e-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="c078e-105">V C# 2.0 nebo novější, je také možné použít anonymní metody deklarace a inicializace [delegovat](../../../csharp/language-reference/keywords/delegate.md), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c078e-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="c078e-106">V jazyce C# 3.0 nebo novější můžete delegáti také deklarovaný a vytvoření instance pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c078e-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="c078e-107">Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c078e-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="c078e-108">Následující příklad ilustruje deklarování, vytváření instancí a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="c078e-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="c078e-109">`BookDB` Třída zapouzdří knihkupectví databázi, která udržuje databázi knih.</span><span class="sxs-lookup"><span data-stu-id="c078e-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="c078e-110">Poskytuje metody, `ProcessPaperbackBooks`, který vyhledá všechny paperback zarezervuje v databázi a volání delegáta pro každé z nich.</span><span class="sxs-lookup"><span data-stu-id="c078e-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="c078e-111">`delegate` Typ, který se používá jmenuje `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="c078e-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="c078e-112">`Test` Třída používá tato třída tisknout názvy a průměrná cena formátu brožované knih.</span><span class="sxs-lookup"><span data-stu-id="c078e-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="c078e-113">Použití delegátů zvýší úroveň dobré oddělení funkcí mezi databázi pro knihkupectví a kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="c078e-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="c078e-114">Kód klienta nemá žádné informace o tom, jak jsou uložené webu knihy nebo jak kód pro knihkupectví vyhledá formátu brožované knihy.</span><span class="sxs-lookup"><span data-stu-id="c078e-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="c078e-115">Kód pro knihkupectví nemá žádné informace o jaké zpracování provádí na formátu brožované knihy po nich najde.</span><span class="sxs-lookup"><span data-stu-id="c078e-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c078e-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="c078e-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c078e-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c078e-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="c078e-118">Deklarování delegáta.</span><span class="sxs-lookup"><span data-stu-id="c078e-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="c078e-119">Následující příkaz deklaruje nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="c078e-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="c078e-120">Každý typ delegáta popisuje počet a typy argumentů a typ návratová hodnota metody, které může zapouzdřit.</span><span class="sxs-lookup"><span data-stu-id="c078e-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="c078e-121">Vždy, když je potřeba novou sadu typy argumentů nebo typ návratové hodnoty, musí být deklarován nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="c078e-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="c078e-122">Vytváření instancí delegáta.</span><span class="sxs-lookup"><span data-stu-id="c078e-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="c078e-123">Poté, co byla deklarována typem delegáta, musí být objekt delegáta vytvořena a přidružena konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="c078e-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="c078e-124">V předchozím příkladu, Uděláte to pomocí předání `PrintTitle` metodu `ProcessPaperbackBooks` metoda jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c078e-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="c078e-125">Tím se vytvoří nový objekt delegáta přidružené [statické](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="c078e-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="c078e-126">Podobně metoda nestatické `AddBookToTotal` u objektu `totaller` je předána jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c078e-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="c078e-127">V obou případech je předán nový objekt delegáta `ProcessPaperbackBooks` metoda.</span><span class="sxs-lookup"><span data-stu-id="c078e-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="c078e-128">Po vytvoření delegáta metodu je spojena se nikdy změny; Delegát objekty jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="c078e-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="c078e-129">Volání metody delegáta.</span><span class="sxs-lookup"><span data-stu-id="c078e-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="c078e-130">Po vytvoření objektu delegáta objekt delegáta obvykle předaný jiný kód, který bude volat delegát.</span><span class="sxs-lookup"><span data-stu-id="c078e-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="c078e-131">Objekt delegáta nazývá pomocí názvu objektu delegáta, za nímž následuje argumenty v závorce mají být předány delegát.</span><span class="sxs-lookup"><span data-stu-id="c078e-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="c078e-132">Tady je příklad delegáta volání:</span><span class="sxs-lookup"><span data-stu-id="c078e-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="c078e-133">Delegát může být buď volána synchronně, jako v následujícím příkladu, nebo asynchronně pomocí `BeginInvoke` a `EndInvoke` metody.</span><span class="sxs-lookup"><span data-stu-id="c078e-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c078e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="c078e-134">See Also</span></span>  
 [<span data-ttu-id="c078e-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c078e-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c078e-136">Události</span><span class="sxs-lookup"><span data-stu-id="c078e-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="c078e-137">Delegáti</span><span class="sxs-lookup"><span data-stu-id="c078e-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
