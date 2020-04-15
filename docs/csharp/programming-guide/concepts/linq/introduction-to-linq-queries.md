---
title: Úvod do dotazů LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 5a9d97ff14f087ddfc55986bf77f18492cbf8a04
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389581"
---
# <a name="introduction-to-linq-queries-c"></a>Úvod do dotazů LINQ (C#)
Dotaz *query* je výraz, který načítá data ze zdroje dat. Dotazy jsou obvykle vyjádřeny ve specializovaném dotazovacím jazyce. Pro různé typy zdrojů dat byly v průběhu času vyvinuty různé jazyky, například SQL pro relační databáze a XQuery pro XML. Proto vývojáři museli naučit nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, které musí podporovat. LINQ zjednodušuje tuto situaci tím, že nabízí konzistentní model pro práci s daty napříč různými druhy zdrojů dat a formátů. V dotazu LINQ vždy pracujete s objekty. Stejné základní vzorky kódování se používají k dotazování a transformaci dat v dokumentech XML, databázích SQL, ADO.NET datových sadách, kolekcích .NET a jakémkoli jiném formátu, pro který je k dispozici zprostředkovatel LINQ.  
  
## <a name="three-parts-of-a-query-operation"></a>Tři části operace dotazu  
 Všechny operace dotazu LINQ se skládají ze tří různých akcí:  
  
1. Získejte zdroj dat.  
  
2. Vytvořte dotaz.  
  
3. Spusťte dotaz.  
  
 Následující příklad ukazuje, jak jsou tři části operace dotazu vyjádřeny ve zdrojovém kódu. Příklad používá celé pole jako zdroj dat pro pohodlí; stejné koncepty však platí i pro jiné zdroje dat. Tento příklad je uveden v celém zbytku tohoto tématu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Následující obrázek znázorňuje celou operaci dotazu. V LINQ provádění dotazu se liší od samotného dotazu. Jinými slovy jste nenačetli žádná data pouze vytvořením proměnné dotazu.  
  
 ![Diagram dokončení operace dotazu LINQ.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Zdroj dat  
 V předchozím příkladu, protože zdroj dat je pole, <xref:System.Collections.Generic.IEnumerable%601> implicitně podporuje obecné rozhraní. Tato skutečnost znamená, že může být dotazován s LINQ. Dotaz je spuštěn v `foreach` příkazu `foreach` <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601>vyžaduje nebo . Typy, <xref:System.Collections.Generic.IEnumerable%601> které podporují nebo odvozené <xref:System.Linq.IQueryable%601> rozhraní, jako je například obecné, se nazývají *dotazovatelné typy*.  
  
 Dotazovatelný typ nevyžaduje žádné změny nebo zvláštní zpracování sloužit jako zdroj dat LINQ. Pokud zdrojová data již není v paměti jako dotazovatelný typ, musí zprostředkovatel LINQ reprezentovat jako takové. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načte dokument XML do <xref:System.Xml.Linq.XElement> dotazovatelného typu:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Pomocí [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]aplikace nejprve vytvoříte mapování vztahů s objekty v době návrhu ručně nebo pomocí [nástrojů LINQ to SQL Tools v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2). Napíšete dotazy proti objekty a za [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] běhu zpracovává komunikaci s databází. V následujícím příkladu `Customers` představuje konkrétní tabulku v databázi a typ <xref:System.Linq.IQueryable%601>výsledku <xref:System.Collections.Generic.IEnumerable%601>dotazu , odvozuje od .  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Další informace o tom, jak vytvořit konkrétní typy zdrojů dat, naleznete v dokumentaci pro různé zprostředkovatele LINQ. Základní pravidlo je však velmi jednoduché: linq zdroj dat <xref:System.Collections.Generic.IEnumerable%601> je libovolný objekt, který podporuje obecné rozhraní nebo rozhraní, které dědí z něj.  
  
> [!NOTE]
> Typy, <xref:System.Collections.ArrayList> jako je například, které podporují neobecné <xref:System.Collections.IEnumerable> rozhraní lze také použít jako zdroj dat LINQ. Další informace naleznete v [tématu Jak dotaz ArrayList s LINQ (C#)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a><a name="query"></a>Dotaz  
 Dotaz určuje, jaké informace se mají načíst ze zdroje dat nebo zdrojů. Volitelně dotaz také určuje, jak by měly být tyto informace seřazeny, seskupeny a tvarovány před vrácením. Dotaz je uložen v proměnné dotazu a inicializován s výrazem dotazu. Chcete-li usnadnit psaní dotazů, C# zavedla novou syntaxi dotazu.  
  
 Dotaz v předchozím příkladu vrátí všechna sudá čísla z celočíselné pole. Výraz dotazu obsahuje tři `from` `where` klauzule: , a `select`. (Pokud jste obeznámeni s SQL, budete si všimli, že řazení klauzulí je obráceno z pořadí v SQL.) Klauzule `from` určuje zdroj dat, `where` klauzule použije filtr `select` a klauzule určuje typ vrácených prvků. Tyto a další klauzule dotazu jsou podrobně popsány v části [Jazyk integrovaný dotaz (LINQ).](../../../linq/index.md) Pro tuto chvíli je důležité, že v LINQ proměnné dotazu sám neprovede žádnou akci a vrátí žádná data. Pouze ukládá informace, které je nutné k vytvoření výsledků při spuštění dotazu v určitém pozdějším okamžiku. Další informace o tom, jak jsou dotazy vytvářeny na pozadí, naleznete v [tématu Přehled standardních operátorů dotazů (C#).](./standard-query-operators-overview.md)  
  
> [!NOTE]
> Dotazy lze také vyjádřit pomocí syntaxe metody. Další informace naleznete [v tématu Syntaxe dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Jak již bylo uvedeno dříve, samotná proměnná dotazu ukládá pouze příkazy dotazu. Skutečné spuštění dotazu je odloženo, dokud iterate přes `foreach` proměnnou dotazu v příkazu. Tento koncept se označuje jako *odložené spuštění* a je demonstrován v následujícím příkladu:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 Příkaz `foreach` je také kde jsou načteny výsledky dotazu. Například v předchozím dotazu iterace proměnná `num` obsahuje každou hodnotu (jeden po druhém) ve vrácené sekvenci.  
  
 Vzhledem k tomu, že samotná proměnná dotazu nikdy neobsahuje výsledky dotazu, můžete ji spustit tak často, jak chcete. Můžete mít například databázi, která je průběžně aktualizována samostatnou aplikací. V aplikaci můžete vytvořit jeden dotaz, který načte nejnovější data a můžete jej spustit opakovaně v určitém intervalu k načtení různých výsledků pokaždé.  
  
### <a name="forcing-immediate-execution"></a>Vynucení okamžitého provedení  
 Dotazy, které provádějí agregační funkce přes rozsah zdrojových prvků, musí nejprve iterate přes tyto prvky. Příklady takových dotazů `Count` `Max`jsou `Average`, `First`, a . Tyto spustit bez `foreach` explicitní příkaz, protože `foreach` dotaz sám musí použít k vrácení výsledku. Všimněte si také, že tyto typy dotazů vrátit jednu hodnotu, `IEnumerable` nikoli kolekce. Následující dotaz vrátí počet sudých čísel ve zdrojovém poli:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Chcete-li vynutit okamžité spuštění libovolného dotazu a ukládat jeho výsledky do mezipaměti, <xref:System.Linq.Enumerable.ToList%2A> můžete volat metody or. <xref:System.Linq.Enumerable.ToArray%2A>  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Spuštění můžete také vynutit vložením `foreach` smyčky bezprostředně za výraz dotazu. Voláním `ToList` nebo `ToArray` také mezipaměti všechna data v jednom objektu kolekce.  
  
## <a name="see-also"></a>Viz také

- [Začínáme s dotazy LINQ v jazyce C#](index.md)
- [Návod: Psaní dotazů v C #](./walkthrough-writing-queries-linq.md)
- [LINQ (Language Integrated Query)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Klíčová slova dotazu (LINQ)](../../../language-reference/keywords/query-keywords.md)
