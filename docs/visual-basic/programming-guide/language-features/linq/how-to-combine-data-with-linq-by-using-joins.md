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
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)
Visual Basic poskytuje `Join` a `Group Join` dotaz klauzule k vám umožní sloučit obsah na základě běžných hodnot mezi kolekce více kolekcí. Tyto hodnoty se označují jako *klíč* hodnoty. Vývojáři, kteří znají relační databáze koncepty rozpozná `Join` klauzule jako vnitřního spojení a `Group Join` klauzule jako prakticky LEFT OUTER JOIN.  
  
 Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data pomocí `Join` a `Group Join` dotaz klauzule.  
  
## <a name="create-a-project-and-add-sample-data"></a>Vytvořte projekt a přidání ukázkových dat  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Chcete-li vytvořit projekt, který obsahuje ukázková data a typy  
  
1.  Ke spuštění ukázky v tomto tématu, otevřete Visual Studio a přidat nový projekt konzolové aplikace jazyka Visual Basic. Poklikejte na soubor Module1.vb vytvořené jazyka Visual Basic.  
  
2.  Ukázky v tomto tématu `Person` a `Pet` typy a data z následující příklad kódu. Zkopírujte tento kód do výchozí `Module1` modulu vytvořené jazyka Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Provést vnitřní spojení pomocí klauzuli Join  
 INNER JOIN kombinuje data z dvě kolekce. Položky, pro které zadané klíčové hodnoty shodují jsou zahrnuty. Všechny položky z buď kolekce, které nemají odpovídající položku v jiné kolekci jsou vyloučeny.  
  
 V jazyce Visual Basic LINQ nabízí dvě možnosti pro provádění vnitřní spojení: implicitní spojení a explicitní spojení.  
  
 Implicitní spojení určuje kolekce, který se má spojit `From` klauzule a identifikuje odpovídající klíčová pole v `Where` klauzule. Visual Basic implicitně spojí dvě kolekce na základě zadaného klíče polí.  
  
 Můžete zadat explicitní spojení pomocí `Join` klauzuli, pokud chcete mít konkrétní, o který klíč pole použít ve spojení. V takovém případě `Where` klauzule pořád můžou použít pro filtrování výsledků dotazu.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>K provedení operace Inner Join pomocí klauzuli Join  
  
1.  Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady obou implicitní a explicitní vnitřní spojení.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Levé vnější spojení provádět pomocí Group Join – klauzule  
 LEFT OUTER JOIN zahrnuje všechny položky z kolekce levé spojení a jenom odpovídající hodnoty z kolekce pravé spojení. Všechny položky z kolekce pravé spojení, které nemají odpovídající položku v kolekci levé straně jsou vyloučeny z výsledku dotazu.  
  
 `Group Join` Klauzule provádí ve skutečnosti LEFT OUTER JOIN. Rozdíl mezi co se obvykle označuje jako LEFT OUTER JOIN a co `Group Join` klauzule vrací je, že `Group Join` klauzule skupiny výsledky z kolekce pravé spojení pro každou položku v kolekci levé straně. V relační databázi LEFT OUTER JOIN vrátí výsledek Neseskupená, ve kterém každá položka v dotazu způsobit obsahuje odpovídající položky z obou kolekcí ve spojení. V takovém případě jsou položky z kolekce levé straně připojení k opakuje pro každý odpovídající položku z kolekce pravé straně. Zobrazí se, jak to vypadá po dokončení dalšího postupu.  
  
 Můžete načíst výsledky `Group Join` dotazu jako výsledek Neseskupená tím, že rozšíří dotaz vrátit položky pro každý výsledek seskupené dotazu. K tomu, musíte zkontrolovat, zadat dotaz na `DefaultIfEmpty` metoda seskupené kolekce. Tím se zajistí, že položky z kolekce levé straně připojení k jsou stále zahrnuté ve výsledku dotazu i v případě, že mají žádné odpovídající výsledky z kolekce pravé straně. Kód můžete přidat do dotazu k poskytnutí výchozí hodnotu výsledek při neexistuje žádná odpovídající hodnota z kolekce pravé spojení.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>K provedení Left Outer Join pomocí klauzuli Join skupiny  
  
1.  Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady seskupené levé vnější spojení a Neseskupená levé vnější spojení.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Provést spojení pomocí složených klíče  
 Můžete použít `And` – klíčové slovo v `Join` nebo `Group Join` klauzule k identifikaci více klíčová pole k použití při kontrole shody hodnoty z kolekce se připojený. `And` – Klíčové slovo určuje, zda všechny zadané klíčová pole musí odpovídat položek, který se má spojit.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>K provedení spojení pomocí složeného klíče  
  
1.  Přidejte následující kód, který `Module1` modulu ve vašem projektu a příklady spojení, které používá složený klíč.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Kód spuštění  
  
#### <a name="to-add-code-to-run-the-examples"></a>Chcete-li přidat kód pro spuštění příkladů  
  
1.  Nahraďte `Sub Main` v `Module1` modulu ve vašem projektu s následující kód pro spuštění v příkladech v tomto tématu.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Stisknutím klávesy F5 spusťte v příkladech.  
  
## <a name="see-also"></a>Viz také  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [JOIN – klauzule](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join – klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [From – klauzule](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Kde – klauzule](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)  
 [Transformace dat pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
