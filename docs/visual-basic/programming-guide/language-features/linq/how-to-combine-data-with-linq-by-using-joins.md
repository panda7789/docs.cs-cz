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
ms.openlocfilehash: 127e1afa7707f31584e93f3d4b08e865d7fcedf6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319596"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)
Visual Basic poskytuje `Join` a `Group Join` klauzulí vám umožní sloučit obsah více kolekcí založených na společné hodnoty mezi kolekcí dotazů. Tyto hodnoty jsou označovány jako *klíč* hodnoty. Rozpozná vývojářům dobře známé koncepty relační databáze `Join` klauzule jako INNER JOIN a `Group Join` klauzule jako efektivní, LEFT OUTER JOIN.  
  
 Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data s využitím `Join` a `Group Join` klauzulí dotazů.  
  
## <a name="create-a-project-and-add-sample-data"></a>Vytvoření projektu a přidání ukázkových dat  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Chcete-li vytvořit projekt, který obsahuje ukázková data a typy  
  
1. Ke spuštění ukázky v tomto tématu, otevřete Visual Studio a přidejte nový projekt konzolové aplikace jazyka Visual Basic. Poklikejte na soubor Module1.vb vytvořené pomocí jazyka Visual Basic.  
  
2. Ukázky v tomto tématu `Person` a `Pet` typy a data z následující příklad kódu. Zkopírujte tento kód do výchozí `Module1` modulu vytvořené pomocí jazyka Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Provádění vnitřního spojení s použitím Join – klauzule  
 INNER JOIN kombinuje data ze dvou kolekcí. Položky, které odpovídají zadané hodnoty klíče jsou zahrnuty. Nevylučují se žádné položky z některé kolekce, které nemají odpovídající položku v jiné kolekci.  
  
 LINQ v jazyce Visual Basic poskytuje dvě možnosti pro provádění vnitřního spojení: implicitní spojení a explicitní spojení.  
  
 Implicitní spojení určuje kolekce, který se má spojit `From` klauzule a identifikuje pole odpovídající klíče v `Where` klauzuli. Visual Basic implicitně spojení dvou kolekcí založených na pole zadaného klíče.  
  
 Můžete zadat explicitní spojení s použitím `Join` klauzuli, pokud chcete mít konkrétní, o který klíč pole použít ve spojení. V tomto případě `Where` klauzuli můžete stále použít k filtrování výsledků dotazu.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>K provedení Inner Join pomocí klauzule Join  
  
1. Přidejte následující kód, který `Module1` modulu ve vašem projektu a podívejte se na příklady obou implicitní a explicitní vnitřního spojení.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Provedení levé vnější spojení pomocí Group Join – klauzule  
 LEFT OUTER JOIN zahrnuje všechny položky z kolekce levé straně, spojení a jenom odpovídající hodnoty z kolekce pravé spojení. Všechny položky z kolekce pravé spojení, které nemají odpovídající položku v kolekce levé straně jsou vyloučeny z výsledku dotazu.  
  
 `Group Join` Klauzule provádí v důsledku toho LEFT OUTER JOIN. Rozdíl mezi co se obvykle označuje jako LEFT OUTER JOIN a co `Group Join` klauzule vrací hodnotu, která je `Group Join` klauzule skupiny výsledky z kolekce pravé spojení pro každou položku v kolekce levé straně. V relační databázi LEFT OUTER JOIN vrátí výsledek Neseskupená, ve kterém každé položky v dotazu výsledek obsahuje odpovídající položky z obou kolekcí ve spojení. V takovém případě položky z kolekce levé straně spojení se opakuje pro každou odpovídající položku z kolekce na pravé straně. Zobrazí se, jak to vypadá po dokončení dalšího postupu.  
  
 Můžete načíst výsledky `Group Join` dotazu jako výsledek neseskupení rozšířením váš dotaz, který vrací položky pro každý výsledek seskupené dotazu. K tomu budete muset zajistit, že při dotazu na `DefaultIfEmpty` metoda seskupenou kolekci. Tím se zajistí, že položky z kolekce levé straně spojení jsou však stále součástí výsledku dotazu i v případě, že nemají žádné odpovídající výsledky z kolekce na pravé straně. Přidejte kód do dotazu zadat výchozí hodnotu výsledek, pokud neexistuje žádná odpovídající hodnota z kolekce pravé spojení.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>K provedení Left Outer Join pomocí klauzule Join skupiny  
  
1. Přidejte následující kód, který `Module1` modulu ve vašem projektu a podívejte se na příklady seskupené levé vnější spojení a Neseskupená levé vnější spojení.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Provést spojení pomocí složených klíče  
 Můžete použít `And` – klíčové slovo v `Join` nebo `Group Join` klauzule k identifikaci více polí klíčů pro použití při kontrole shody hodnoty z kolekce je připojen. `And` – Klíčové slovo určuje, zda všechny zadané klíčové pole musí odpovídat pro položky, které chcete připojit.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>K provedení spojení pomocí složených klíče  
  
1. Přidejte následující kód, který `Module1` modulu ve vašem projektu a podívejte se na příklady spojení, která používá složený klíč.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Spuštění kódu  
  
#### <a name="to-add-code-to-run-the-examples"></a>Chcete-li přidat kód pro spuštění příkladů  
  
1. Nahradit `Sub Main` v `Module1` modul ve svém projektu následující kód pro spuštění příkladů v tomto tématu.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Stisknutím klávesy F5 pro spuštění příkladů.  
  
## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Představení technologie LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join – klauzule](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join – klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From – klauzule](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where – klauzule](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [Transformace dat pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
