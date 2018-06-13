---
title: 'Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: f0279cc13e938b6f7853ef11fee1ef046f192316
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653452"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="08c0f-102">Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08c0f-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="08c0f-103">Visual Basic poskytuje `Join` a `Group Join` dotaz klauzule k vám umožní sloučit obsah na základě běžných hodnot mezi kolekce více kolekcí.</span><span class="sxs-lookup"><span data-stu-id="08c0f-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="08c0f-104">Tyto hodnoty se označují jako *klíč* hodnoty.</span><span class="sxs-lookup"><span data-stu-id="08c0f-104">These values are known as *key* values.</span></span> <span data-ttu-id="08c0f-105">Vývojáři, kteří znají relační databáze koncepty rozpozná `Join` klauzule jako vnitřního spojení a `Group Join` klauzule jako prakticky LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="08c0f-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="08c0f-106">Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data pomocí `Join` a `Group Join` dotaz klauzule.</span><span class="sxs-lookup"><span data-stu-id="08c0f-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="08c0f-107">Vytvořte projekt a přidání ukázkových dat</span><span class="sxs-lookup"><span data-stu-id="08c0f-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="08c0f-108">Chcete-li vytvořit projekt, který obsahuje ukázková data a typy</span><span class="sxs-lookup"><span data-stu-id="08c0f-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="08c0f-109">Ke spuštění ukázky v tomto tématu, otevřete Visual Studio a přidat nový projekt konzolové aplikace jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08c0f-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="08c0f-110">Poklikejte na soubor Module1.vb vytvořené jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08c0f-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="08c0f-111">Ukázky v tomto tématu `Person` a `Pet` typy a data z následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="08c0f-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="08c0f-112">Zkopírujte tento kód do výchozí `Module1` modulu vytvořené jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08c0f-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="08c0f-113">Provést vnitřní spojení pomocí klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="08c0f-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="08c0f-114">INNER JOIN kombinuje data z dvě kolekce.</span><span class="sxs-lookup"><span data-stu-id="08c0f-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="08c0f-115">Položky, pro které zadané klíčové hodnoty shodují jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="08c0f-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="08c0f-116">Všechny položky z buď kolekce, které nemají odpovídající položku v jiné kolekci jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="08c0f-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="08c0f-117">V jazyce Visual Basic LINQ nabízí dvě možnosti pro provádění vnitřní spojení: implicitní spojení a explicitní spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="08c0f-118">Implicitní spojení určuje kolekce, který se má spojit `From` klauzule a identifikuje odpovídající klíčová pole v `Where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="08c0f-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="08c0f-119">Visual Basic implicitně spojí dvě kolekce na základě zadaného klíče polí.</span><span class="sxs-lookup"><span data-stu-id="08c0f-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="08c0f-120">Můžete zadat explicitní spojení pomocí `Join` klauzuli, pokud chcete mít konkrétní, o který klíč pole použít ve spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="08c0f-121">V takovém případě `Where` klauzule pořád můžou použít pro filtrování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="08c0f-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="08c0f-122">K provedení operace Inner Join pomocí klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="08c0f-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="08c0f-123">Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady obou implicitní a explicitní vnitřní spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="08c0f-124">Levé vnější spojení provádět pomocí Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="08c0f-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="08c0f-125">LEFT OUTER JOIN zahrnuje všechny položky z kolekce levé spojení a jenom odpovídající hodnoty z kolekce pravé spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="08c0f-126">Všechny položky z kolekce pravé spojení, které nemají odpovídající položku v kolekci levé straně jsou vyloučeny z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="08c0f-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="08c0f-127">`Group Join` Klauzule provádí ve skutečnosti LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="08c0f-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="08c0f-128">Rozdíl mezi co se obvykle označuje jako LEFT OUTER JOIN a co `Group Join` klauzule vrací je, že `Group Join` klauzule skupiny výsledky z kolekce pravé spojení pro každou položku v kolekci levé straně.</span><span class="sxs-lookup"><span data-stu-id="08c0f-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="08c0f-129">V relační databázi LEFT OUTER JOIN vrátí výsledek Neseskupená, ve kterém každá položka v dotazu způsobit obsahuje odpovídající položky z obou kolekcí ve spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="08c0f-130">V takovém případě jsou položky z kolekce levé straně připojení k opakuje pro každý odpovídající položku z kolekce pravé straně.</span><span class="sxs-lookup"><span data-stu-id="08c0f-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="08c0f-131">Zobrazí se, jak to vypadá po dokončení dalšího postupu.</span><span class="sxs-lookup"><span data-stu-id="08c0f-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="08c0f-132">Můžete načíst výsledky `Group Join` dotazu jako výsledek Neseskupená tím, že rozšíří dotaz vrátit položky pro každý výsledek seskupené dotazu.</span><span class="sxs-lookup"><span data-stu-id="08c0f-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="08c0f-133">K tomu, musíte zkontrolovat, zadat dotaz na `DefaultIfEmpty` metoda seskupené kolekce.</span><span class="sxs-lookup"><span data-stu-id="08c0f-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="08c0f-134">Tím se zajistí, že položky z kolekce levé straně připojení k jsou stále zahrnuté ve výsledku dotazu i v případě, že mají žádné odpovídající výsledky z kolekce pravé straně.</span><span class="sxs-lookup"><span data-stu-id="08c0f-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="08c0f-135">Kód můžete přidat do dotazu k poskytnutí výchozí hodnotu výsledek při neexistuje žádná odpovídající hodnota z kolekce pravé spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="08c0f-136">K provedení Left Outer Join pomocí klauzuli Join skupiny</span><span class="sxs-lookup"><span data-stu-id="08c0f-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="08c0f-137">Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady seskupené levé vnější spojení a Neseskupená levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="08c0f-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="08c0f-138">Provést spojení pomocí složených klíče</span><span class="sxs-lookup"><span data-stu-id="08c0f-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="08c0f-139">Můžete použít `And` – klíčové slovo v `Join` nebo `Group Join` klauzule k identifikaci více klíčová pole k použití při kontrole shody hodnoty z kolekce se připojený.</span><span class="sxs-lookup"><span data-stu-id="08c0f-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="08c0f-140">`And` – Klíčové slovo určuje, zda všechny zadané klíčová pole musí odpovídat položek, který se má spojit.</span><span class="sxs-lookup"><span data-stu-id="08c0f-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="08c0f-141">K provedení spojení pomocí složeného klíče</span><span class="sxs-lookup"><span data-stu-id="08c0f-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="08c0f-142">Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady spojení, které používá složený klíč.</span><span class="sxs-lookup"><span data-stu-id="08c0f-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="08c0f-143">Kód spuštění</span><span class="sxs-lookup"><span data-stu-id="08c0f-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="08c0f-144">Chcete-li přidat kód pro spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="08c0f-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="08c0f-145">Nahraďte `Sub Main` v `Module1` modulu ve vašem projektu s následující kód pro spuštění v příkladech v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="08c0f-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="08c0f-146">Stisknutím klávesy F5 spusťte v příkladech.</span><span class="sxs-lookup"><span data-stu-id="08c0f-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c0f-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="08c0f-147">See Also</span></span>  
 [<span data-ttu-id="08c0f-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="08c0f-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="08c0f-149">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08c0f-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="08c0f-150">Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="08c0f-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="08c0f-151">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="08c0f-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="08c0f-152">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="08c0f-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="08c0f-153">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="08c0f-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="08c0f-154">Dotazy</span><span class="sxs-lookup"><span data-stu-id="08c0f-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="08c0f-155">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="08c0f-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
