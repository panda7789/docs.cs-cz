---
title: "Úvod do dotazů LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae7a2d03859e95d939ff4c62fa33e07917a873a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-linq-queries-c"></a>Úvod do dotazů LINQ (C#)
A *dotazu* je výraz, který načte data z datového zdroje. Dotazy jsou obvykle vyjádřeny v specializované dotazovací jazyk. V čase pro různé typy datových zdrojů, například SQL pro relační databáze a XQuery pro formát XML bylo vyvinuto různé jazyky. Vývojáři mají proto byl Další informace o nový jazyk dotazu pro každý typ zdroje dat nebo formát dat, který musí podporovat. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Tuto situaci zjednodušuje tím, že nabízí konzistentní model pro práci s daty mezi různé druhy zdrojů dat a formáty. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, které jsou vždy práce s objekty. Použijte stejný základní kódování vzory pro dotazování a transformace dat v dokumentech XML, databáze SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové sady, kolekcí .NET a dalších formát, pro který [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele je k dispozici.  
  
## <a name="three-parts-of-a-query-operation"></a>Tři části operace dotazu  
 Všechny [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu operations obsahovat tři odlišné akce:  
  
1.  Zdroj dat získáte.  
  
2.  Vytvořte dotaz.  
  
3.  Provedení dotazu.  
  
 Následující příklad ukazuje, jak jsou tyto tři části operace dotazů vyjádřeny ve zdrojovém kódu. Tento příklad používá celočíselné pole jako zdroj dat pro usnadnění práce; ale koncepty týkají jiných zdrojů dat také. V tomto příkladu je uvedené v celé zbývající část tohoto tématu.  
  
 [!code-csharp[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 Následující obrázek znázorňuje operaci dokončení dotazu. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provádění dotazu se liší od samotný dotaz, jinými slovy nebyly načíst všechna data stejně tak, že vytvoříte proměnné dotazu.  
  
 ![Dokončení operace dotazů LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ_Query")  
  
## <a name="the-data-source"></a>Zdroj dat  
 V předchozím příkladu, protože zdroj dat je pole, implicitně podporuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Tato skutečnost znamená, může být dotazován s [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Je dotaz proveden v `foreach` příkaz, a `foreach` vyžaduje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Typy podporující <xref:System.Collections.Generic.IEnumerable%601> nebo odvozené rozhraní, jako je například obecná <xref:System.Linq.IQueryable%601> se nazývají *dotazovatelné typy*.  
  
 Dotazovatelný typ nevyžaduje žádné úpravy ani zvláštní zacházení, která bude sloužit jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat. Pokud zdroj dat není v paměti jako dotazovatelný typ už [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele musí představovat ho jako takový. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načtení dokumentu XML do dotazovatelné <xref:System.Xml.Linq.XElement> typu:  
  
 [!code-csharp[CsLINQGettingStarted#2](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_2.cs)]  
  
 S [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], je nejprve vytvořit k objektu relační mapování v době návrhu buď ručně, nebo pomocí [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) v sadě Visual Studio. Zápis dotazů u těchto objektů a při spuštění [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává komunikaci s databází. V následujícím příkladu `Customers` představuje určité tabulky v databázi a typ výsledku dotazu <xref:System.Linq.IQueryable%601>, je odvozena z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Další informace o tom, jak vytvořit konkrétní typy zdrojů dat naleznete v dokumentaci pro různé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele. Ale je velmi jednoduchý základní pravidlo: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat je libovolný objekt, který podporuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo rozhraní, které dědí z něj.  
  
> [!NOTE]
>  Typy, jako <xref:System.Collections.ArrayList> podporující neobecnou <xref:System.Collections.IEnumerable> rozhraní lze také jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat. Další informace najdete v tématu [postup: dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
##  <a name="query"></a>Dotaz  
 Dotaz Určuje, jaké informace načíst ze zdroje dat nebo zdroje. Volitelně dotazu také určuje, jak tyto informace by měl být seřazeny, seskupené a ve tvaru před vrácením. Dotaz je uložené v proměnné dotazu a inicializovat pomocí výrazu dotazu. Chcete-li psát dotazy, C# obsahuje zavedla nové syntaxe dotazu.  
  
 Dotaz v předchozím příkladu vrátí sudá čísla z pole celé číslo. Výraz dotazu obsahuje tři klauzule: `from`, `where` a `select`. (Pokud jste obeznámeni s SQL, bude jste si všimli, že řazení klauzulích je obrácený od pořadí v systému SQL.) `from` Klauzuli určuje zdroje dat, `where` klauzule použije filtr a `select` klauzuli Určuje typ vrácený elementů. Tyto a další klauzule dotazu jsou podrobněji v [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md) části. Teď, důležité je, že v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], proměnné v dotazu samotné neprovede žádnou akci a vrátí žádná data. Ukládá jenom informace, které je potřeba mít výsledky, pokud je dotaz proveden v určitém okamžiku novější. Další informace o tom, jak se vytvářejí dotazy na pozadí najdete v tématu [standardní přehled operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Dotazy lze také vyjádřit pomocí syntaxe využívající metody. Další informace najdete v tématu [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Jak jsme uvedli dříve, proměnné v dotazu samotné ukládá jenom příkazy dotazu. Skutečné provádění dotazu je odložení, dokud iterace v proměnné dotazu v `foreach` příkaz. Tento koncept se označuje jako *odložené spouštění* a je znázorněn v následujícím příkladu:  
  
 [!code-csharp[csLinqGettingStarted#4](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_3.cs)]  
  
 `foreach` Příkaz je také, kde jsou načteny výsledky dotazu. Například v předchozího dotazu, proměnné iterace `num` obsahuje každou hodnotu (po jednom) vrácená postupně.  
  
 Protože proměnné v dotazu samotné nikdy obsahuje výsledky dotazu, můžete provést tak často, jak se vám líbí. Například můžete mít databázi, která se právě aktualizuje průběžně samostatné aplikace. V aplikaci můžete vytvořit jeden dotaz, který načte nejnovější data a ho mohl spustit opakovaně v některé intervalu načíst pokaždé, když odlišné výsledky.  
  
### <a name="forcing-immediate-execution"></a>Vynucení okamžitého provedení  
 Dotazy, které provádět agregačními funkcemi nad rozsah zdrojových elementů musí nejprve iterace v těchto elementů. Příkladem takové dotazy jsou `Count`, `Max`, `Average`, a `First`. To provést bez explicitního `foreach` příkaz protože samotný dotaz musí používat `foreach` cílem vrátit výsledek. Všimněte si také, že tyto typy dotazů vrátit jednu hodnotu, není `IEnumerable` kolekce. Následující dotaz vrací počet sudým číslům ve zdrojové pole:  
  
 [!code-csharp[csLinqGettingStarted#5](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_4.cs)]  
  
 Chcete-li vynutit okamžité spuštění jakékoli dotazu a její výsledky do mezipaměti, můžete zavolat <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> metody.  
  
 [!code-csharp[csLinqGettingStarted#6](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_5.cs)]  
  
 Můžete taky přinutit, provádění umístěním `foreach` smyčky ihned po výrazu dotazu. Ale voláním `ToList` nebo `ToArray` také mezipaměti všechna data v objektu jedinou kolekci.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Návod: Zápis dotazů v C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Návod: Zápis dotazů v C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [foreach v](../../../../csharp/language-reference/keywords/foreach-in.md)  
 [Klíčová slova dotazu (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
