---
title: 'Postupy: Deklarování, vytváření instancí a použití delegáta (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 6c53d7572074db44976494e5eed596bf95aaf456
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736176"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="e41e4-102">Postupy: Deklarování, vytváření instancí a použití delegáta (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e41e4-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="e41e4-103">V jazyce C# 1.0 nebo novější delegáty lze deklarovat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e41e4-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="e41e4-104">C# 2.0 umožňuje jednodušší způsob, jak napsat předchozí prohlášení, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e41e4-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="e41e4-105">V jazyce C# 2.0 nebo novější, je také možné použít k deklaraci a inicializaci anonymní metoda [delegovat](../../../csharp/language-reference/keywords/delegate.md), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e41e4-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="e41e4-106">V jazyce C# 3.0 nebo novější můžete delegáti také deklarovány a vytvořit instanci pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e41e4-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="e41e4-107">Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e41e4-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="e41e4-108">Následující příklad ukazuje deklarování, vytváření instancí a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="e41e4-109">`BookDB` Třída zapouzdří knihkupectví databázi, která udržuje databázi knihy.</span><span class="sxs-lookup"><span data-stu-id="e41e4-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="e41e4-110">Zpřístupní metodu, `ProcessPaperbackBooks`, který najde všechny tištěné verze knih v databázi a volání delegáta pro každé z nich.</span><span class="sxs-lookup"><span data-stu-id="e41e4-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="e41e4-111">`delegate` Má typ, který se používá název `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="e41e4-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="e41e4-112">`Test` Třída používá k vytištění názvy a průměrná cena formátu brožované knih, které tato třída.</span><span class="sxs-lookup"><span data-stu-id="e41e4-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="e41e4-113">Použití delegátů podporuje dobré oddělení funkcí mezi knihkupectví databáze a klientský kód.</span><span class="sxs-lookup"><span data-stu-id="e41e4-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="e41e4-114">Klientský kód je vůbec nezná způsob uložení knih nebo jak knihkupectví kód najde formátu brožované knihy.</span><span class="sxs-lookup"><span data-stu-id="e41e4-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="e41e4-115">Kód knihkupectví nemá žádné znalosti z jaké zpracování probíhá ve formátu brožované knihy po nich najde.</span><span class="sxs-lookup"><span data-stu-id="e41e4-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e41e4-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="e41e4-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e41e4-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e41e4-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="e41e4-118">Deklarace delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="e41e4-119">Následující příkaz deklaruje nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="e41e4-120">Každý typ delegáta popisuje počet a typy argumentů a typ vrácené hodnoty metod, které může zapouzdřit.</span><span class="sxs-lookup"><span data-stu-id="e41e4-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="e41e4-121">Pokaždé, když je potřeba nová sada typy argumentů nebo typ vrácené hodnoty, musí být deklarován nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="e41e4-122">Vytvoření instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="e41e4-123">Poté, co je deklarovaný typ delegáta, objektu delegáta musí vytvořit a přidružený k určité metodě.</span><span class="sxs-lookup"><span data-stu-id="e41e4-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="e41e4-124">V předchozím příkladu, můžete to provést předáním `PrintTitle` metodu `ProcessPaperbackBooks` metody jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e41e4-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="e41e4-125">Tím se vytvoří nový objekt delegáta přidružený k [statické](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="e41e4-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="e41e4-126">Podobně, nestatické metody `AddBookToTotal` objektu `totaller` je předán jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e41e4-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="e41e4-127">V obou případech je předat objekt delegáta `ProcessPaperbackBooks` metody.</span><span class="sxs-lookup"><span data-stu-id="e41e4-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="e41e4-128">Po vytvoření delegáta metodě je přidružen k nikdy změny. Delegát objekty jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="e41e4-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="e41e4-129">Volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="e41e4-130">Po vytvoření objektu delegáta objekt delegáta je obvykle předat jiným kódem, který bude volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="e41e4-131">Objekt delegáta je volána za použití názvu objektu delegáta, za nímž následuje argumenty v závorce má být předán delegáta.</span><span class="sxs-lookup"><span data-stu-id="e41e4-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="e41e4-132">Následuje příklad volání delegáta:</span><span class="sxs-lookup"><span data-stu-id="e41e4-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="e41e4-133">Delegát může být buď volat synchronně, jako v následujícím příkladu, nebo asynchronně pomocí `BeginInvoke` a `EndInvoke` metody.</span><span class="sxs-lookup"><span data-stu-id="e41e4-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41e4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e41e4-134">See Also</span></span>

- [<span data-ttu-id="e41e4-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e41e4-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e41e4-136">Události</span><span class="sxs-lookup"><span data-stu-id="e41e4-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="e41e4-137">Delegáti</span><span class="sxs-lookup"><span data-stu-id="e41e4-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
