---
title: 'Postupy: Deklarování, vytváření instancí a použití delegáta - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 55b8467415b8243327f6902479cd4739df20bb7b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975716"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="32769-102">Postupy: Deklarování, vytváření instancí a použití delegáta (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="32769-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="32769-103">V jazyce C# 1.0 nebo novější delegáty lze deklarovat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32769-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="32769-104">C# 2.0 umožňuje jednodušší způsob, jak napsat předchozí prohlášení, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32769-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="32769-105">V jazyce C# 2.0 nebo novější, je také možné použít k deklaraci a inicializaci anonymní metoda [delegovat](../../../csharp/language-reference/keywords/delegate.md), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32769-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="32769-106">V jazyce C# 3.0 nebo novější můžete delegáti také deklarovány a vytvořit instanci pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32769-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="32769-107">Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="32769-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="32769-108">Následující příklad ukazuje deklarování, vytváření instancí a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="32769-109">`BookDB` Třída zapouzdří knihkupectví databázi, která udržuje databázi knihy.</span><span class="sxs-lookup"><span data-stu-id="32769-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="32769-110">Zpřístupní metodu, `ProcessPaperbackBooks`, který najde všechny tištěné verze knih v databázi a volání delegáta pro každé z nich.</span><span class="sxs-lookup"><span data-stu-id="32769-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="32769-111">`delegate` Má typ, který se používá název `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="32769-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="32769-112">`Test` Třída používá k vytištění názvy a průměrná cena formátu brožované knih, které tato třída.</span><span class="sxs-lookup"><span data-stu-id="32769-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="32769-113">Použití delegátů podporuje dobré oddělení funkcí mezi knihkupectví databáze a klientský kód.</span><span class="sxs-lookup"><span data-stu-id="32769-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="32769-114">Klientský kód je vůbec nezná způsob uložení knih nebo jak knihkupectví kód najde formátu brožované knihy.</span><span class="sxs-lookup"><span data-stu-id="32769-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="32769-115">Kód knihkupectví nemá žádné znalosti z jaké zpracování probíhá ve formátu brožované knihy po nich najde.</span><span class="sxs-lookup"><span data-stu-id="32769-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32769-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="32769-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="32769-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="32769-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="32769-118">Deklarace delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="32769-119">Následující příkaz deklaruje nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="32769-120">Každý typ delegáta popisuje počet a typy argumentů a typ vrácené hodnoty metod, které může zapouzdřit.</span><span class="sxs-lookup"><span data-stu-id="32769-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="32769-121">Pokaždé, když je potřeba nová sada typy argumentů nebo typ vrácené hodnoty, musí být deklarován nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="32769-122">Vytvoření instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="32769-123">Poté, co je deklarovaný typ delegáta, objektu delegáta musí vytvořit a přidružený k určité metodě.</span><span class="sxs-lookup"><span data-stu-id="32769-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="32769-124">V předchozím příkladu, můžete to provést předáním `PrintTitle` metodu `ProcessPaperbackBooks` metody jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="32769-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="32769-125">Tím se vytvoří nový objekt delegáta přidružený k [statické](../../../csharp/language-reference/keywords/static.md) metoda `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="32769-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="32769-126">Podobně, nestatické metody `AddBookToTotal` objektu `totaller` je předán jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="32769-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="32769-127">V obou případech je předat objekt delegáta `ProcessPaperbackBooks` metody.</span><span class="sxs-lookup"><span data-stu-id="32769-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="32769-128">Po vytvoření delegáta metodě je přidružen k nikdy změny. Delegát objekty jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="32769-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="32769-129">Volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="32769-130">Po vytvoření objektu delegáta objekt delegáta je obvykle předat jiným kódem, který bude volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="32769-131">Objekt delegáta je volána za použití názvu objektu delegáta, za nímž následuje argumenty v závorce má být předán delegáta.</span><span class="sxs-lookup"><span data-stu-id="32769-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="32769-132">Následuje příklad volání delegáta:</span><span class="sxs-lookup"><span data-stu-id="32769-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="32769-133">Delegát může být buď volat synchronně, jako v následujícím příkladu, nebo asynchronně pomocí `BeginInvoke` a `EndInvoke` metody.</span><span class="sxs-lookup"><span data-stu-id="32769-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32769-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32769-134">See also</span></span>

- [<span data-ttu-id="32769-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="32769-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="32769-136">Události</span><span class="sxs-lookup"><span data-stu-id="32769-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="32769-137">Delegáti</span><span class="sxs-lookup"><span data-stu-id="32769-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
