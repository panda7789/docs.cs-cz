---
title: 'Postupy: Deklarace, vytvoření instance a použití průvodce C# programováním delegátů'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 565ae2a6c42de57570f564edc9d0bde5cab8efa8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590625"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="a0ccb-102">Postupy: Deklarace, vytvoření instance a použití delegáta (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="a0ccb-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="a0ccb-103">V C# 1,0 a novějších, mohou být Delegáti deklarováni, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="a0ccb-104">C#2,0 poskytuje jednodušší způsob, jak napsat předchozí deklaraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="a0ccb-105">V C# 2,0 a novějších je také možné použít anonymní metodu k deklaraci a inicializaci delegáta, [](../../language-reference/keywords/delegate.md)jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="a0ccb-106">V C# 3,0 a novějších, mohou být Delegáti také deklarováni a vytvořeny pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="a0ccb-107">Další informace naleznete v tématu [lambda výrazy](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a0ccb-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="a0ccb-108">Následující příklad znázorňuje deklarování, vytváření instancí a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="a0ccb-109">`BookDB` Třída zapouzdřuje databázi Bookstore, která udržuje databázi knih.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="a0ccb-110">Zpřístupňuje metodu, `ProcessPaperbackBooks`která najde všechny tištěné verze knihy v databázi a zavolá delegáta pro každý z nich.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="a0ccb-111">Typ, který se používá, se `ProcessBookDelegate`nazývá. `delegate`</span><span class="sxs-lookup"><span data-stu-id="a0ccb-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="a0ccb-112">`Test` Třída používá tuto třídu k tisku názvů a průměrné ceny tištěné verze knih.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="a0ccb-113">Použití delegátů podporuje dobré oddělení funkcí mezi databází Bookstore a klientským kódem.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="a0ccb-114">Kód klienta nemá žádné znalosti o tom, jak jsou knihy uložené, nebo jak kód Bookstore najde tištěné verze knihy.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="a0ccb-115">Kód Bookstore nemá žádné znalosti o tom, jaké zpracování se provádí na tištěné verzech knihách, jakmile je najde.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0ccb-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0ccb-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a0ccb-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a0ccb-117">Robust Programming</span></span>  
  
- <span data-ttu-id="a0ccb-118">Deklarace delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="a0ccb-119">Následující příkaz deklaruje nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="a0ccb-120">Každý typ delegáta popisuje počet a typy argumentů a typ návratové hodnoty metod, které mohou být zapouzdřeny.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="a0ccb-121">Pokaždé, když je potřeba nová sada typů argumentů nebo návratový typ hodnoty, musí být deklarovaný nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="a0ccb-122">Vytvoření instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="a0ccb-123">Po deklarování typu delegáta musí být objekt delegáta vytvořen a přidružen k určité metodě.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="a0ccb-124">V předchozím příkladu je třeba předat `PrintTitle` metodu `ProcessPaperbackBooks` metodě jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a0ccb-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="a0ccb-125">Tím se vytvoří nový objekt delegáta přidružený ke [statické](../../language-reference/keywords/static.md) metodě `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="a0ccb-126">Podobně není statická metoda `AddBookToTotal` objektu `totaller` předána jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a0ccb-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="a0ccb-127">V obou případech je `ProcessPaperbackBooks` metodě předán nový objekt delegát.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="a0ccb-128">Po vytvoření delegáta metoda je přidružena bez jakýchkoli změn; objekty delegáta jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="a0ccb-129">Volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="a0ccb-130">Po vytvoření objektu delegáta je objekt delegát obvykle předán jinému kódu, který bude volat delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="a0ccb-131">Objekt delegáta je volán pomocí názvu objektu delegáta následovaný argumenty v závorkách, které mají být předány delegátovi.</span><span class="sxs-lookup"><span data-stu-id="a0ccb-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="a0ccb-132">Následuje příklad volání delegáta:</span><span class="sxs-lookup"><span data-stu-id="a0ccb-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="a0ccb-133">Delegát může být buď volán synchronně, jako v tomto příkladu, nebo asynchronně pomocí `BeginInvoke` metod a. `EndInvoke`</span><span class="sxs-lookup"><span data-stu-id="a0ccb-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ccb-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0ccb-134">See also</span></span>

- [<span data-ttu-id="a0ccb-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a0ccb-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a0ccb-136">Události</span><span class="sxs-lookup"><span data-stu-id="a0ccb-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="a0ccb-137">Delegáti</span><span class="sxs-lookup"><span data-stu-id="a0ccb-137">Delegates</span></span>](./index.md)
