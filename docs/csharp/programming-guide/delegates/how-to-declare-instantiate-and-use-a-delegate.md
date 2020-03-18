---
title: Jak deklarovat, vytvořit instanci a použít průvodce programováním v jazyce Delegate – Programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712361"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="ace98-102">Jak deklarovat, konkretizovat a používat delegate (C# Programovací příručka)</span><span class="sxs-lookup"><span data-stu-id="ace98-102">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="ace98-103">V jazyce C# 1.0 a novější delegáti mohou být deklarovány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ace98-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="ace98-104">C# 2.0 poskytuje jednodušší způsob, jak napsat předchozí deklarace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ace98-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="ace98-105">V C# 2.0 a novější je také možné použít anonymní metodu k deklarování a inicializaci [delegáta](../../language-reference/builtin-types/reference-types.md), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ace98-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="ace98-106">V jazyce C# 3.0 a novější delegáti mohou být také deklarovány a vytvořena instance pomocí výrazu lambda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ace98-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="ace98-107">Další informace naleznete v tématu [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ace98-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="ace98-108">Následující příklad ukazuje deklarování, vytváření instancí a použití delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="ace98-109">Třída `BookDB` zapouzdřuje databázi knihkupectví, která udržuje databázi knih.</span><span class="sxs-lookup"><span data-stu-id="ace98-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="ace98-110">Zpřístupní metodu `ProcessPaperbackBooks`, která vyhledá všechny brožované knihy v databázi a zavolá delegáta pro každou z nich.</span><span class="sxs-lookup"><span data-stu-id="ace98-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="ace98-111">Použitý `delegate` typ je pojmenován `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="ace98-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="ace98-112">Třída `Test` používá tuto třídu k tisku názvů a průměrné ceny brožknih.</span><span class="sxs-lookup"><span data-stu-id="ace98-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="ace98-113">Použití delegátů podporuje dobré oddělení funkcí mezi databází knihkupectví a klientským kódem.</span><span class="sxs-lookup"><span data-stu-id="ace98-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="ace98-114">Klientský kód nemá žádné znalosti o tom, jak jsou knihy uloženy nebo jak kód knihkupectví najde brožované knihy.</span><span class="sxs-lookup"><span data-stu-id="ace98-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="ace98-115">Kód knihkupectví nemá žádné znalosti o tom, jaké zpracování se provádí na brožované knihy poté, co je najde.</span><span class="sxs-lookup"><span data-stu-id="ace98-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace98-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ace98-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ace98-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ace98-117">Robust Programming</span></span>  
  
- <span data-ttu-id="ace98-118">Deklarování delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="ace98-119">Následující příkaz deklaruje nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="ace98-120">Každý typ delegáta popisuje počet a typy argumentů a typ vrácené hodnoty metod, které může zapouzdřit.</span><span class="sxs-lookup"><span data-stu-id="ace98-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="ace98-121">Kdykoli je potřeba nová sada typů argumentů nebo typ vrácené hodnoty, musí být deklarován nový typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="ace98-122">Vytvoření instance delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="ace98-123">Po deklarování typu delegáta musí být objekt delegáta vytvořen a přidružen k určité metodě.</span><span class="sxs-lookup"><span data-stu-id="ace98-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="ace98-124">V předchozím příkladu to provést `PrintTitle` předáním `ProcessPaperbackBooks` metody metodě jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ace98-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="ace98-125">Tím se vytvoří nový objekt delegáta přidružený ke [statické](../../language-reference/keywords/static.md) metodě `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="ace98-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="ace98-126">Podobně je nestatická `AddBookToTotal` metoda objektu `totaller` předána jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ace98-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="ace98-127">V obou případech je metodě `ProcessPaperbackBooks` předán nový objekt delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="ace98-128">Po vytvoření delegáta se metoda, ke které je přidružen, nikdy nezmění; delegovat objekty jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="ace98-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="ace98-129">Volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="ace98-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="ace98-130">Po vytvoření objektu delegáta je objekt delegáta obvykle předán jinému kódu, který bude delegáta volat.</span><span class="sxs-lookup"><span data-stu-id="ace98-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="ace98-131">Objekt delegáta je volán pomocí názvu objektu delegáta následovaným argumenty v závorce, které mají být předány delegátovi.</span><span class="sxs-lookup"><span data-stu-id="ace98-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="ace98-132">Následuje příklad volání delegáta:</span><span class="sxs-lookup"><span data-stu-id="ace98-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="ace98-133">Delegát může být volána synchronně, jako v tomto příkladu, nebo `BeginInvoke` `EndInvoke` asynchronně pomocí a metody.</span><span class="sxs-lookup"><span data-stu-id="ace98-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace98-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="ace98-134">See also</span></span>

- [<span data-ttu-id="ace98-135">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ace98-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ace98-136">Akce</span><span class="sxs-lookup"><span data-stu-id="ace98-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="ace98-137">Delegáty</span><span class="sxs-lookup"><span data-stu-id="ace98-137">Delegates</span></span>](./index.md)
