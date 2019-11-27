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
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Postupy: Kombinace dat s LINQ pomocí spojení (Visual Basic)
Visual Basic poskytuje klauzule dotazu `Join` a `Group Join`, které vám umožní kombinovat obsah více kolekcí na základě běžných hodnot mezi kolekcemi. Tyto hodnoty se označují jako *klíčové* hodnoty. Vývojáři, kteří jsou obeznámeni s koncepty relačních databází, rozpoznávají klauzuli `Join` jako vnitřní spojení a klauzuli `Group Join` jako efektivní a levé vnější spojení.  
  
 Příklady v tomto tématu ukazují několik způsobů, jak kombinovat data pomocí klauzulí `Join` a `Group Join` dotazů.  
  
## <a name="create-a-project-and-add-sample-data"></a>Vytvoření projektu a Přidání ukázkových dat  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Vytvoření projektu, který obsahuje ukázková data a typy  
  
1. Chcete-li spustit ukázky v tomto tématu, otevřete aplikaci Visual Studio a přidejte nový projekt Visual Basic konzolové aplikace. Dvakrát klikněte na soubor Module1. vb vytvořený pomocí Visual Basic.  
  
2. Ukázky v tomto tématu používají `Person` a `Pet` typy a data z následujícího příkladu kódu. Zkopírujte tento kód do výchozího modulu `Module1` vytvořeného pomocí Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Provedení vnitřního spojení pomocí klauzule JOIN  
 VNITŘNÍ spojení kombinuje data ze dvou kolekcí. Položky, pro které se shodují zadané hodnoty klíčů, jsou zahrnuty. Všechny položky z obou kolekcí, které nemají odpovídající položku v jiné kolekci, jsou vyloučeny.  
  
 V Visual Basic LINQ nabízí dvě možnosti pro provádění vnitřního spojení: implicitní spojení a explicitní spojení.  
  
 Implicitní spojení Určuje kolekce, které mají být spojeny v klauzuli `From` a v klauzuli `Where` identifikuje klíčová pole, která se shodují. Visual Basic implicitně spojí dvě kolekce na základě zadaných klíčových polí.  
  
 Explicitní spojení můžete zadat pomocí klauzule `Join`, pokud chcete mít konkrétní informace o tom, která klíčová pole se mají ve spojení použít. V takovém případě může být k filtrování výsledků dotazu stále používána klauzule `Where`.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Provedení vnitřního spojení pomocí klauzule JOIN  
  
1. Přidejte následující kód do modulu `Module1` v projektu, aby se zobrazily příklady implicitního i explicitního vnitřního spojení.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Provedení levého vnějšího spojení pomocí klauzule Group Join  
 LEVÉ vnější spojení zahrnuje všechny položky z kolekce na levé straně spojení a jenom vyhovující hodnoty z kolekce na pravé straně spojení. Všechny položky z kolekce na pravé straně spojení, které nemají odpovídající položku v kolekci na levé straně, jsou vyloučeny z výsledku dotazu.  
  
 Klauzule `Group Join` provádí v podstatě levé vnější spojení. Rozdíl mezi tím, co se obvykle označuje jako levé vnější spojení a co klauzule `Group Join` vrátí, je, že klauzule `Group Join` seskupí výsledky z kolekce JOIN na pravé straně pro každou položku v kolekci na levé straně. V relační databázi vrátí levé vnější spojení neseskupený výsledek, ve kterém každá položka ve výsledku dotazu obsahuje vyhovující položky z obou kolekcí v rámci spojení. V tomto případě se položky z kolekce na levé straně spojení opakují pro každou vyhovující položku z kolekce na pravé straně. Zobrazí se to, co vypadá po dokončení dalšího postupu.  
  
 Výsledky `Group Join`ho dotazu můžete načíst jako neseskupený výsledek rozšířením dotazu tak, aby vracel položku pro každý výsledek seskupeného dotazu. Chcete-li to provést, musíte se ujistit, že je nutné zadat dotaz na metodu `DefaultIfEmpty` seskupené kolekce. Tím zajistíte, že položky z kolekce na levé straně spojení budou zahrnuty do výsledku dotazu i v případě, že nemají odpovídající výsledky z kolekce na pravé straně. Do dotazu můžete přidat kód pro zadání výchozí hodnoty výsledku v případě, že není k dispozici žádná shodná hodnota z kolekce na pravé straně spojení.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Provedení levého vnějšího spojení pomocí klauzule Group Join  
  
1. Přidejte následující kód do modulu `Module1` v projektu, abyste viděli příklady seskupeného levého vnějšího spojení a neseskupené levé vnější spojení.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Provedení spojení pomocí složeného klíče  
 Klíčové slovo `And` v klauzuli `Join` nebo `Group Join` můžete použít k identifikaci více klíčových polí, která se mají použít, když se shodují hodnoty z kolekce, které jsou spojeny. Klíčové slovo `And` určuje, že všechna zadaná klíčová pole se musí shodovat s položkami, které mají být spojeny.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Provedení spojení pomocí složeného klíče  
  
1. Přidejte následující kód do modulu `Module1` v projektu, aby se zobrazily příklady spojení, které používá složený klíč.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Spustit kód  
  
#### <a name="to-add-code-to-run-the-examples"></a>Přidání kódu pro spuštění příkladů  
  
1. Nahraďte `Sub Main` v modulu `Module1` ve vašem projektu následujícím kódem pro spuštění příkladů v tomto tématu.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Příklady spustíte stisknutím klávesy F5.  
  
## <a name="see-also"></a>Viz také:

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Klauzule Join](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Klauzule Group Join](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Klauzule From](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Where](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
- [Transformace dat pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
