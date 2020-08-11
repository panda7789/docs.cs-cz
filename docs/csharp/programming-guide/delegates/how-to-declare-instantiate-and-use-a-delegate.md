---
title: Postup deklarace, vytvoření instance a použití delegáta – Průvodce programováním v C#
description: Přečtěte si, jak deklarovat, vytvářet instance a použít delegáta. Podívejte se na příklady, které se týkají C# 1,0, 2,0 a 3,0 a novější.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: b741b3bc9c03faaa5fa2c01bd8f70d4be9b099c2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063663"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="ee4a2-104">Postup deklarace, vytvoření instance a použití delegáta (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ee4a2-104">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="ee4a2-105">V C# 1,0 a novějších lze delegáty deklarovat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-105">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="ee4a2-106">C# 2,0 poskytuje jednodušší způsob, jak napsat předchozí deklaraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="ee4a2-107">V C# 2,0 a novější je také možné použít anonymní metodu k deklaraci a inicializaci [delegáta](../../language-reference/builtin-types/reference-types.md), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-107">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="ee4a2-108">V jazyce C# 3,0 a novějším mohou být Delegáti deklarováni a vytvořeny pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-108">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="ee4a2-109">Další informace naleznete v tématu [lambda výrazy](../../language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ee4a2-109">For more information, see [Lambda Expressions](../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="ee4a2-110">Následující příklad znázorňuje deklarování, vytváření instancí a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-110">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="ee4a2-111">`BookDB`Třída zapouzdřuje databázi Bookstore, která udržuje databázi knih.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-111">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="ee4a2-112">Zpřístupňuje metodu, `ProcessPaperbackBooks` která najde všechny tištěné verze knihy v databázi a zavolá delegáta pro každý z nich.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-112">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="ee4a2-113">`delegate`Typ, který se používá, se nazývá `ProcessBookDelegate` .</span><span class="sxs-lookup"><span data-stu-id="ee4a2-113">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="ee4a2-114">`Test`Třída používá tuto třídu k tisku názvů a průměrné ceny tištěné verze knih.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-114">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="ee4a2-115">Použití delegátů podporuje dobré oddělení funkcí mezi databází Bookstore a klientským kódem.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-115">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="ee4a2-116">Kód klienta nemá žádné znalosti o tom, jak jsou knihy uložené, nebo jak kód Bookstore najde tištěné verze knihy.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-116">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="ee4a2-117">Kód Bookstore nemá žádné znalosti o tom, jaké zpracování se provádí na tištěné verzech knihách, jakmile je najde.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-117">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee4a2-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee4a2-118">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ee4a2-119">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ee4a2-119">Robust Programming</span></span>  
  
- <span data-ttu-id="ee4a2-120">Deklarace delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-120">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="ee4a2-121">Následující příkaz deklaruje nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-121">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="ee4a2-122">Každý typ delegáta popisuje počet a typy argumentů a typ návratové hodnoty metod, které mohou být zapouzdřeny.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-122">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="ee4a2-123">Pokaždé, když je potřeba nová sada typů argumentů nebo návratový typ hodnoty, musí být deklarovaný nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-123">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="ee4a2-124">Vytvoření instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-124">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="ee4a2-125">Po deklarování typu delegáta musí být objekt delegáta vytvořen a přidružen k určité metodě.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-125">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="ee4a2-126">V předchozím příkladu je třeba předat `PrintTitle` metodu `ProcessPaperbackBooks` metodě jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ee4a2-126">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="ee4a2-127">Tím se vytvoří nový objekt delegáta přidružený ke [statické](../../language-reference/keywords/static.md) metodě `Test.PrintTitle` .</span><span class="sxs-lookup"><span data-stu-id="ee4a2-127">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="ee4a2-128">Podobně není statická metoda `AddBookToTotal` objektu `totaller` předána jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ee4a2-128">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="ee4a2-129">V obou případech je metodě předán nový objekt delegát `ProcessPaperbackBooks` .</span><span class="sxs-lookup"><span data-stu-id="ee4a2-129">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="ee4a2-130">Po vytvoření delegáta metoda je přidružena bez jakýchkoli změn; objekty delegáta jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-130">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="ee4a2-131">Volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-131">Calling a delegate.</span></span>  
  
     <span data-ttu-id="ee4a2-132">Po vytvoření objektu delegáta je objekt delegát obvykle předán jinému kódu, který bude volat delegáta.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-132">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="ee4a2-133">Objekt delegáta je volán pomocí názvu objektu delegáta následovaný argumenty v závorkách, které mají být předány delegátovi.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-133">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="ee4a2-134">Následuje příklad volání delegáta:</span><span class="sxs-lookup"><span data-stu-id="ee4a2-134">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="ee4a2-135">Delegát může být buď volán synchronně, jako v tomto příkladu, nebo asynchronně pomocí `BeginInvoke` `EndInvoke` metod a.</span><span class="sxs-lookup"><span data-stu-id="ee4a2-135">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4a2-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee4a2-136">See also</span></span>

- [<span data-ttu-id="ee4a2-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ee4a2-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee4a2-138">Události</span><span class="sxs-lookup"><span data-stu-id="ee4a2-138">Events</span></span>](../events/index.md)
- [<span data-ttu-id="ee4a2-139">Delegáty</span><span class="sxs-lookup"><span data-stu-id="ee4a2-139">Delegates</span></span>](./index.md)
