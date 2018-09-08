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
ms.openlocfilehash: 4db5d288d79379b677bb19b2eba0d094e0d71bc8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177802"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="01873-102">Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01873-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="01873-103">Visual Basic poskytuje `Join` a `Group Join` klauzulí vám umožní sloučit obsah více kolekcí založených na společné hodnoty mezi kolekcí dotazů.</span><span class="sxs-lookup"><span data-stu-id="01873-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="01873-104">Tyto hodnoty jsou označovány jako *klíč* hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01873-104">These values are known as *key* values.</span></span> <span data-ttu-id="01873-105">Rozpozná vývojářům dobře známé koncepty relační databáze `Join` klauzule jako INNER JOIN a `Group Join` klauzule jako efektivní, LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="01873-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="01873-106">Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data s využitím `Join` a `Group Join` klauzulí dotazů.</span><span class="sxs-lookup"><span data-stu-id="01873-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="01873-107">Vytvoření projektu a přidání ukázkových dat</span><span class="sxs-lookup"><span data-stu-id="01873-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="01873-108">Chcete-li vytvořit projekt, který obsahuje ukázková data a typy</span><span class="sxs-lookup"><span data-stu-id="01873-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="01873-109">Ke spuštění ukázky v tomto tématu, otevřete Visual Studio a přidejte nový projekt konzolové aplikace jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01873-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="01873-110">Poklikejte na soubor Module1.vb vytvořené pomocí jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01873-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="01873-111">Ukázky v tomto tématu `Person` a `Pet` typy a data z následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="01873-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="01873-112">Zkopírujte tento kód do výchozí `Module1` modulu vytvořené pomocí jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01873-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="01873-113">Provádění vnitřního spojení s použitím Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="01873-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="01873-114">INNER JOIN kombinuje data ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="01873-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="01873-115">Položky, které odpovídají zadané hodnoty klíče jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="01873-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="01873-116">Nevylučují se žádné položky z některé kolekce, které nemají odpovídající položku v jiné kolekci.</span><span class="sxs-lookup"><span data-stu-id="01873-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="01873-117">LINQ v jazyce Visual Basic poskytuje dvě možnosti pro provádění vnitřního spojení: implicitní spojení a explicitní spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="01873-118">Implicitní spojení určuje kolekce, který se má spojit `From` klauzule a identifikuje pole odpovídající klíče v `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="01873-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="01873-119">Visual Basic implicitně spojení dvou kolekcí založených na pole zadaného klíče.</span><span class="sxs-lookup"><span data-stu-id="01873-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="01873-120">Můžete zadat explicitní spojení s použitím `Join` klauzuli, pokud chcete mít konkrétní, o který klíč pole použít ve spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="01873-121">V tomto případě `Where` klauzuli můžete stále použít k filtrování výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="01873-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="01873-122">K provedení Inner Join pomocí klauzule Join</span><span class="sxs-lookup"><span data-stu-id="01873-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="01873-123">Přidejte následující kód, který `Module1` modulu ve vašem projektu a podívejte se na příklady obou implicitní a explicitní vnitřního spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="01873-124">Provedení levé vnější spojení pomocí Group Join – klauzule</span><span class="sxs-lookup"><span data-stu-id="01873-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="01873-125">LEFT OUTER JOIN zahrnuje všechny položky z kolekce levé straně, spojení a jenom odpovídající hodnoty z kolekce pravé spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="01873-126">Všechny položky z kolekce pravé spojení, které nemají odpovídající položku v kolekce levé straně jsou vyloučeny z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="01873-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="01873-127">`Group Join` Klauzule provádí v důsledku toho LEFT OUTER JOIN.</span><span class="sxs-lookup"><span data-stu-id="01873-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="01873-128">Rozdíl mezi co se obvykle označuje jako LEFT OUTER JOIN a co `Group Join` klauzule vrací hodnotu, která je `Group Join` klauzule skupiny výsledky z kolekce pravé spojení pro každou položku v kolekce levé straně.</span><span class="sxs-lookup"><span data-stu-id="01873-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="01873-129">V relační databázi LEFT OUTER JOIN vrátí výsledek Neseskupená, ve kterém každé položky v dotazu výsledek obsahuje odpovídající položky z obou kolekcí ve spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="01873-130">V takovém případě položky z kolekce levé straně spojení se opakuje pro každou odpovídající položku z kolekce na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="01873-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="01873-131">Zobrazí se, jak to vypadá po dokončení dalšího postupu.</span><span class="sxs-lookup"><span data-stu-id="01873-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="01873-132">Můžete načíst výsledky `Group Join` dotazu jako výsledek neseskupení rozšířením váš dotaz, který vrací položky pro každý výsledek seskupené dotazu.</span><span class="sxs-lookup"><span data-stu-id="01873-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="01873-133">K tomu budete muset zajistit, že při dotazu na `DefaultIfEmpty` metoda seskupenou kolekci.</span><span class="sxs-lookup"><span data-stu-id="01873-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="01873-134">Tím se zajistí, že položky z kolekce levé straně spojení jsou však stále součástí výsledku dotazu i v případě, že nemají žádné odpovídající výsledky z kolekce na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="01873-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="01873-135">Přidejte kód do dotazu zadat výchozí hodnotu výsledek, pokud neexistuje žádná odpovídající hodnota z kolekce pravé spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="01873-136">K provedení Left Outer Join pomocí klauzule Join skupiny</span><span class="sxs-lookup"><span data-stu-id="01873-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="01873-137">Přidejte následující kód, který `Module1` modulu ve vašem projektu a podívejte se na příklady seskupené levé vnější spojení a Neseskupená levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="01873-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="01873-138">Provést spojení pomocí složených klíče</span><span class="sxs-lookup"><span data-stu-id="01873-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="01873-139">Můžete použít `And` – klíčové slovo v `Join` nebo `Group Join` klauzule k identifikaci více polí klíčů pro použití při kontrole shody hodnoty z kolekce je připojen.</span><span class="sxs-lookup"><span data-stu-id="01873-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="01873-140">`And` – Klíčové slovo určuje, zda všechny zadané klíčové pole musí odpovídat pro položky, které chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="01873-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="01873-141">K provedení spojení pomocí složených klíče</span><span class="sxs-lookup"><span data-stu-id="01873-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="01873-142">Přidejte následující kód, který `Module1` modulu ve vašem projektu a podívejte se na příklady spojení, která používá složený klíč.</span><span class="sxs-lookup"><span data-stu-id="01873-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="01873-143">Spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="01873-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="01873-144">Chcete-li přidat kód pro spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="01873-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="01873-145">Nahradit `Sub Main` v `Module1` modul ve svém projektu následující kód pro spuštění příkladů v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="01873-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="01873-146">Stisknutím klávesy F5 pro spuštění příkladů.</span><span class="sxs-lookup"><span data-stu-id="01873-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01873-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="01873-147">See Also</span></span>  
 [<span data-ttu-id="01873-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="01873-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="01873-149">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01873-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="01873-150">Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="01873-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="01873-151">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="01873-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="01873-152">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="01873-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="01873-153">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="01873-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="01873-154">Dotazy</span><span class="sxs-lookup"><span data-stu-id="01873-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="01873-155">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="01873-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
