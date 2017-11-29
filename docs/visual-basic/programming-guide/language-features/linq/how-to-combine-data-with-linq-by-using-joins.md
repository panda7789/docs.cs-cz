---
title: "Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="efd6a-102">Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efd6a-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="efd6a-103">Visual Basic poskytuje `Join` a `Group Join` dotaz klauzule k vám umožní sloučit obsah na základě běžných hodnot mezi kolekce více kolekcí.</span><span class="sxs-lookup"><span data-stu-id="efd6a-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="efd6a-104">Tyto hodnoty se označují jako *klíč* hodnoty.</span><span class="sxs-lookup"><span data-stu-id="efd6a-104">These values are known as *key* values.</span></span> <span data-ttu-id="efd6a-105">Vývojáři, kteří znají relační databáze koncepty rozpozná `Join` klauzule jako vnitřního spojení a `Group Join` klauzule jako prakticky LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="efd6a-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="efd6a-106">Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data pomocí `Join` a `Group Join` dotaz klauzule.</span><span class="sxs-lookup"><span data-stu-id="efd6a-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="efd6a-107">Vytvořte projekt a přidání ukázkových dat</span><span class="sxs-lookup"><span data-stu-id="efd6a-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="efd6a-108">Chcete-li vytvořit projekt, který obsahuje ukázková data a typy</span><span class="sxs-lookup"><span data-stu-id="efd6a-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="efd6a-109">Ke spuštění ukázky v tomto tématu, otevřete Visual Studio a přidat nový projekt konzolové aplikace jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efd6a-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="efd6a-110">Poklikejte na soubor Module1.vb vytvořené jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efd6a-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="efd6a-111">Ukázky v tomto tématu `Person` a `Pet` typy a data z následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="efd6a-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="efd6a-112">Zkopírujte tento kód do výchozí `Module1` modulu vytvořené jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efd6a-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="efd6a-113">Provést vnitřní spojení pomocí klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="efd6a-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="efd6a-114">INNER JOIN kombinuje data z dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="efd6a-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="efd6a-115">Položky, pro které zadané klíčové hodnoty shodují jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="efd6a-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="efd6a-116">Všechny položky z buď kolekce, které nemají odpovídající položku v jiné kolekci jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="efd6a-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="efd6a-117">V jazyce Visual Basic LINQ nabízí dvě možnosti pro provádění vnitřní spojení: implicitní spojení a explicitní spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="efd6a-118">Implicitní spojení určuje kolekce, který se má spojit `From` klauzule a identifikuje odpovídající klíčová pole v `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="efd6a-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="efd6a-119">Visual Basic implicitně spojí dvě kolekce na základě zadaného klíče polí.</span><span class="sxs-lookup"><span data-stu-id="efd6a-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="efd6a-120">Můžete zadat explicitní spojení pomocí `Join` klauzuli, pokud chcete mít konkrétní, o který klíč pole použít ve spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="efd6a-121">V takovém případě `Where` klauzule pořád můžou použít pro filtrování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="efd6a-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="efd6a-122">K provedení operace Inner Join pomocí klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="efd6a-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="efd6a-123">Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady obou implicitní a explicitní vnitřní spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="efd6a-124">Levé vnější spojení provádět pomocí Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="efd6a-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="efd6a-125">LEFT OUTER JOIN zahrnuje všechny položky z kolekce levé spojení a jenom odpovídající hodnoty z kolekce pravé spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="efd6a-126">Všechny položky z kolekce pravé spojení, které nemají odpovídající položku v kolekci levé straně jsou vyloučeny z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="efd6a-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="efd6a-127">`Group Join` Klauzule provádí ve skutečnosti LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="efd6a-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="efd6a-128">Rozdíl mezi co se obvykle označuje jako LEFT OUTER JOIN a co `Group Join` klauzule vrací je, že `Group Join` klauzule skupiny výsledky z kolekce pravé spojení pro každou položku v kolekci levé straně.</span><span class="sxs-lookup"><span data-stu-id="efd6a-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="efd6a-129">V relační databázi LEFT OUTER JOIN vrátí výsledek Neseskupená, ve kterém každá položka v dotazu způsobit obsahuje odpovídající položky z obou kolekcí ve spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="efd6a-130">V takovém případě jsou položky z kolekce levé straně připojení k opakuje pro každý odpovídající položku z kolekce pravé straně.</span><span class="sxs-lookup"><span data-stu-id="efd6a-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="efd6a-131">Zobrazí se, jak to vypadá po dokončení dalšího postupu.</span><span class="sxs-lookup"><span data-stu-id="efd6a-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="efd6a-132">Můžete načíst výsledky `Group Join` dotazu jako výsledek Neseskupená tím, že rozšíří dotaz vrátit položky pro každý výsledek seskupené dotazu.</span><span class="sxs-lookup"><span data-stu-id="efd6a-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="efd6a-133">K tomu, musíte zkontrolovat, zadat dotaz na `DefaultIfEmpty` metoda seskupené kolekce.</span><span class="sxs-lookup"><span data-stu-id="efd6a-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="efd6a-134">Tím se zajistí, že položky z kolekce levé straně připojení k jsou stále zahrnuté ve výsledku dotazu i v případě, že mají žádné odpovídající výsledky z kolekce pravé straně.</span><span class="sxs-lookup"><span data-stu-id="efd6a-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="efd6a-135">Kód můžete přidat do dotazu k poskytnutí výchozí hodnotu výsledek při neexistuje žádná odpovídající hodnota z kolekce pravé spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="efd6a-136">K provedení Left Outer Join pomocí klauzuli Join skupiny</span><span class="sxs-lookup"><span data-stu-id="efd6a-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="efd6a-137">Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady seskupené levé vnější spojení a Neseskupená levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="efd6a-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="efd6a-138">Provést spojení pomocí složených klíče</span><span class="sxs-lookup"><span data-stu-id="efd6a-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="efd6a-139">Můžete použít `And` – klíčové slovo v `Join` nebo `Group Join` klauzule k identifikaci více klíčová pole k použití při kontrole shody hodnoty z kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="efd6a-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="efd6a-140">`And` – Klíčové slovo určuje, zda všechny zadané klíčová pole musí odpovídat položek, který se má spojit.</span><span class="sxs-lookup"><span data-stu-id="efd6a-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="efd6a-141">K provedení spojení pomocí složeného klíče</span><span class="sxs-lookup"><span data-stu-id="efd6a-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="efd6a-142">Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady spojení, které používá složený klíč.</span><span class="sxs-lookup"><span data-stu-id="efd6a-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="efd6a-143">Kód spuštění</span><span class="sxs-lookup"><span data-stu-id="efd6a-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="efd6a-144">Chcete-li přidat kód pro spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="efd6a-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="efd6a-145">Nahraďte `Sub Main` v `Module1` modulu ve vašem projektu s následující kód pro spuštění v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="efd6a-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="efd6a-146">Stisknutím klávesy F5 spusťte v příkladech.</span><span class="sxs-lookup"><span data-stu-id="efd6a-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd6a-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="efd6a-147">See Also</span></span>  
 [<span data-ttu-id="efd6a-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="efd6a-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="efd6a-149">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efd6a-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="efd6a-150">JOIN – klauzule</span><span class="sxs-lookup"><span data-stu-id="efd6a-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="efd6a-151">Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="efd6a-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="efd6a-152">From – klauzule</span><span class="sxs-lookup"><span data-stu-id="efd6a-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="efd6a-153">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="efd6a-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="efd6a-154">Dotazy</span><span class="sxs-lookup"><span data-stu-id="efd6a-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="efd6a-155">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="efd6a-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
