---
title: 'Postupy: kombinování dat pomocí jazyka LINQ pomocí spojení'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345006"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="ddc56-102">Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddc56-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="ddc56-103">Visual Basic poskytuje klauzule dotazu `Join` a `Group Join`, které vám umožní kombinovat obsah více kolekcí na základě běžných hodnot mezi kolekcemi.</span><span class="sxs-lookup"><span data-stu-id="ddc56-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="ddc56-104">Tyto hodnoty se označují jako *klíčové* hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ddc56-104">These values are known as *key* values.</span></span> <span data-ttu-id="ddc56-105">Vývojáři, kteří jsou obeznámeni s koncepty relačních databází, rozpoznávají klauzuli `Join` jako vnitřní spojení a klauzuli `Group Join` jako efektivní a levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="ddc56-106">Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data pomocí klauzulí `Join` a `Group Join` dotazů.</span><span class="sxs-lookup"><span data-stu-id="ddc56-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="ddc56-107">Vytvoření projektu a Přidání ukázkových dat</span><span class="sxs-lookup"><span data-stu-id="ddc56-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="ddc56-108">Vytvoření projektu, který obsahuje ukázková data a typy</span><span class="sxs-lookup"><span data-stu-id="ddc56-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="ddc56-109">Chcete-li spustit ukázky v tomto tématu, otevřete aplikaci Visual Studio a přidejte nový projekt Visual Basic konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddc56-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="ddc56-110">Dvakrát klikněte na soubor Module1. vb vytvořený pomocí Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ddc56-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="ddc56-111">Ukázky v tomto tématu používají `Person` a `Pet` typy a data z následujícího příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ddc56-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="ddc56-112">Zkopírujte tento kód do výchozího modulu `Module1` vytvořeného pomocí Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ddc56-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="ddc56-113">Provedení vnitřního spojení pomocí klauzule JOIN</span><span class="sxs-lookup"><span data-stu-id="ddc56-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="ddc56-114">VNITŘNÍ spojení kombinuje data ze dvou kolekcí.</span><span class="sxs-lookup"><span data-stu-id="ddc56-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="ddc56-115">Položky, pro které se shodují zadané hodnoty klíčů, jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="ddc56-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="ddc56-116">Všechny položky z obou kolekcí, které nemají odpovídající položku v jiné kolekci, jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="ddc56-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="ddc56-117">V Visual Basic LINQ nabízí dvě možnosti pro provádění vnitřního spojení: implicitní spojení a explicitní spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="ddc56-118">Implicitní spojení Určuje kolekce, které mají být spojeny v klauzuli `From` a v klauzuli `Where` identifikuje klíčová pole, která se shodují.</span><span class="sxs-lookup"><span data-stu-id="ddc56-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="ddc56-119">Visual Basic implicitně spojí dvě kolekce na základě zadaných klíčových polí.</span><span class="sxs-lookup"><span data-stu-id="ddc56-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="ddc56-120">Explicitní spojení můžete zadat pomocí klauzule `Join`, pokud chcete mít konkrétní informace o tom, která klíčová pole se mají ve spojení použít.</span><span class="sxs-lookup"><span data-stu-id="ddc56-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="ddc56-121">V takovém případě může být k filtrování výsledků dotazu stále používána klauzule `Where`.</span><span class="sxs-lookup"><span data-stu-id="ddc56-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="ddc56-122">Provedení vnitřního spojení pomocí klauzule JOIN</span><span class="sxs-lookup"><span data-stu-id="ddc56-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="ddc56-123">Přidejte následující kód do modulu `Module1` v projektu, aby se zobrazily příklady implicitního i explicitního vnitřního spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="ddc56-124">Provedení levého vnějšího spojení pomocí klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="ddc56-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="ddc56-125">LEVÉ vnější spojení zahrnuje všechny položky z kolekce na levé straně spojení a jenom vyhovující hodnoty z kolekce na pravé straně spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="ddc56-126">Všechny položky z kolekce na pravé straně spojení, které nemají odpovídající položku v kolekci na levé straně, jsou vyloučeny z výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="ddc56-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="ddc56-127">Klauzule `Group Join` provádí v podstatě levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="ddc56-128">Rozdíl mezi tím, co se obvykle označuje jako levé vnější spojení a co klauzule `Group Join` vrátí, je, že klauzule `Group Join` seskupí výsledky z kolekce JOIN na pravé straně pro každou položku v kolekci na levé straně.</span><span class="sxs-lookup"><span data-stu-id="ddc56-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="ddc56-129">V relační databázi vrátí levé vnější spojení neseskupený výsledek, ve kterém každá položka ve výsledku dotazu obsahuje vyhovující položky z obou kolekcí v rámci spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="ddc56-130">V tomto případě se položky z kolekce na levé straně spojení opakují pro každou vyhovující položku z kolekce na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="ddc56-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="ddc56-131">Zobrazí se to, co vypadá po dokončení dalšího postupu.</span><span class="sxs-lookup"><span data-stu-id="ddc56-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="ddc56-132">Výsledky `Group Join`ho dotazu můžete načíst jako neseskupený výsledek rozšířením dotazu tak, aby vracel položku pro každý výsledek seskupeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="ddc56-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="ddc56-133">Chcete-li to provést, musíte se ujistit, že je nutné zadat dotaz na metodu `DefaultIfEmpty` seskupené kolekce.</span><span class="sxs-lookup"><span data-stu-id="ddc56-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="ddc56-134">Tím zajistíte, že položky z kolekce na levé straně spojení budou zahrnuty do výsledku dotazu i v případě, že nemají odpovídající výsledky z kolekce na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="ddc56-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="ddc56-135">Do dotazu můžete přidat kód pro zadání výchozí hodnoty výsledku v případě, že není k dispozici žádná shodná hodnota z kolekce na pravé straně spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="ddc56-136">Provedení levého vnějšího spojení pomocí klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="ddc56-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="ddc56-137">Přidejte následující kód do modulu `Module1` v projektu, abyste viděli příklady seskupeného levého vnějšího spojení a neseskupené levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="ddc56-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="ddc56-138">Provedení spojení pomocí složeného klíče</span><span class="sxs-lookup"><span data-stu-id="ddc56-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="ddc56-139">Klíčové slovo `And` v klauzuli `Join` nebo `Group Join` můžete použít k identifikaci více klíčových polí, která se mají použít, když se shodují hodnoty z kolekce, které jsou spojeny.</span><span class="sxs-lookup"><span data-stu-id="ddc56-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="ddc56-140">Klíčové slovo `And` určuje, že všechna zadaná klíčová pole se musí shodovat s položkami, které mají být spojeny.</span><span class="sxs-lookup"><span data-stu-id="ddc56-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="ddc56-141">Provedení spojení pomocí složeného klíče</span><span class="sxs-lookup"><span data-stu-id="ddc56-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="ddc56-142">Přidejte následující kód do modulu `Module1` v projektu, aby se zobrazily příklady spojení, které používá složený klíč.</span><span class="sxs-lookup"><span data-stu-id="ddc56-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="ddc56-143">Spustit kód</span><span class="sxs-lookup"><span data-stu-id="ddc56-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="ddc56-144">Přidání kódu pro spuštění příkladů</span><span class="sxs-lookup"><span data-stu-id="ddc56-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="ddc56-145">Nahraďte `Sub Main` v modulu `Module1` ve vašem projektu následujícím kódem pro spuštění příkladů v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="ddc56-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="ddc56-146">Příklady spustíte stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="ddc56-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc56-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddc56-147">See also</span></span>

- [<span data-ttu-id="ddc56-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="ddc56-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="ddc56-149">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddc56-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ddc56-150">Klauzule Join</span><span class="sxs-lookup"><span data-stu-id="ddc56-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="ddc56-151">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="ddc56-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="ddc56-152">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="ddc56-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ddc56-153">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="ddc56-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="ddc56-154">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ddc56-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ddc56-155">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ddc56-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
