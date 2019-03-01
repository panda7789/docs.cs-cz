---
title: Úvod do dotazů LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 73b7f8b8460e4cdfad5e1dbc669447ec6fe01b8f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969502"
---
# <a name="introduction-to-linq-queries-c"></a>Úvod do dotazů LINQ (C#)
A *dotazu* je výraz, který načte data z datového zdroje. Dotazy jsou obvykle vyjádřeny v specializovaném dotazovacím jazyce. Různé jazyky byly vyvinuty v průběhu času pro různé typy zdrojů dat, například SQL pro relační databáze a XQuery pro XML. Proto vývojáři měli získat nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který musí podporovat. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Tuto situaci zjednodušuje tím, že nabízí konzistentní model pro práci s daty napříč různými druhy datových zdrojů a formátů. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, které jsou vždy práce s objekty. Použijte stejné základní vzorce kódování pro dotazování a transformaci dat v dokumentech XML, databázích SQL [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové sady, kolekcích .NET a jakémkoli jiném formátu, pro kterou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele je k dispozici.  
  
## <a name="three-parts-of-a-query-operation"></a>Tři části operace dotazu  
 Všechny [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu operace se skládají ze tří různých akcí:  
  
1.  Získáte zdroje dat.  
  
2.  Vytvořte dotaz.  
  
3.  Spusťte dotaz.  
  
 Následující příklad ukazuje, jak tyto tři části operace dotazu jsou vyjádřeny ve zdrojovém kódu. V příkladu používá celočíselné pole jako zdroj dat ke zvýšení pohodlí; ale stejné koncepty platí i pro jiné zdroje dat také. V tomto příkladu se odkazuje ve zbývající části tohoto tématu.  
  
 [!code-csharp[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 Následující ilustrace znázorňuje operaci úplného dotazu. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provádění dotazu se liší od samotného dotazu; jinými slovy nebyla načtena žádná data pouhým vytvořením proměnné dotazu.  
  
 ![Dokončení operace dotazů LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ_Query")  
  
## <a name="the-data-source"></a>Zdroj dat  
 V předchozím příkladu, protože zdroj dat je pole, implicitně podporuje Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Tato skutečnost znamená, že může být dotázán pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Dotaz je proveden v `foreach` příkaz, a `foreach` vyžaduje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Typy, které podporují <xref:System.Collections.Generic.IEnumerable%601> nebo odvozené rozhraní, jako je obecný <xref:System.Linq.IQueryable%601> se nazývají *dotazovatelné typy*.  
  
 Dotazovatelný typ vyžaduje žádné změny nebo zvláštní zacházení jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj. Pokud zdroj dat již není v paměti jako dotazovatelný typ, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele ho musí představovat jako takový. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načte dokument XML do dotazovatelného <xref:System.Xml.Linq.XElement> typu:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 S [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], nejprve vytvoříte objektově relační mapování v době návrhu ručně nebo pomocí [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) v sadě Visual Studio. Psát dotazy proti objektům a v době běhu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává vnitřní komunikaci s databází. V následujícím příkladu `Customers` představuje určité tabulky v databázi a typ výsledku dotazu <xref:System.Linq.IQueryable%601>, je odvozena z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Další informace o tom, jak vytváření určitých typů zdrojů dat, najdete v dokumentaci pro různé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelů. Základní pravidlo je však velmi jednoduché: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat je libovolný objekt, který podporuje Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo rozhraní, které z něj dědí.  
  
> [!NOTE]
>  Typy, jako <xref:System.Collections.ArrayList> podporující neobecné <xref:System.Collections.IEnumerable> rozhraní může také sloužit jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj. Další informace najdete v tématu [jak: Vytvoření dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
##  <a name="query"></a> Dotaz  
 Dotaz Určuje, jaké informace se mají načíst z datového zdroje nebo zdrojů. V případě potřeby dotaz také určuje, jak tyto informace by měl být seřazeny, seskupeny a tvarovány dříve, než se vrátí. Dotaz je uložen v proměnné dotazu a inicializován pomocí výrazu dotazu. Chcete-li usnadnit psaní dotazů, jazyk C# zavedl novou syntaxi dotazu.  
  
 Dotaz v předchozím příkladu vrátí všechna sudá čísla z pole celých čísel. Výraz dotazu obsahuje tři věty: `from`, `where` a `select`. (Pokud jste obeznámeni s SQL, všimnete si, že pořadí klauzulí je obrácené pořadí, v SQL.) `from` Klauzule určuje zdroje dat `where` klauzule aplikuje filtr a `select` klauzule určuje typ vrácených prvků. Tyto a další klauzule dotazu jsou podrobně popsány v [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md) oddílu. Prozatím je důležité, že v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], proměnná dotazu sama neprovede žádnou akci a nevrátí žádná data. Ukládá pouze informace potřebné k vytvoření výsledku při spuštění dotazu někdy později. Další informace o tom, jak jsou dotazy konstruovány na pozadí, naleznete v tématu [přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Dotazy lze také vyjádřit pomocí syntaxe metody. Další informace najdete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Jak bylo uvedeno dříve, proměnná dotazu sama ukládá pouze příkazy dotazu. Aktuální provádění dotazu je odloženo, dokud neprovedete iteraci v proměnné dotazu v `foreach` příkazu. Tento koncept se označuje jako *odložené provedení* a je znázorněn v následujícím příkladu:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach` Příkaz je také, kde jsou získávány výsledky dotazu. Například v předchozím dotazu, iterační proměnná `num` obsahuje všechny hodnoty (postupně po jednom) ve vrácené posloupnosti.  
  
 Vzhledem k tomu, že proměnné dotazu samy nikdy neobsahují výsledky dotazu, můžete spustit tak často, jak potřebujete. Například může mít databázi, která se průběžně aktualizuje pomocí samostatné aplikace. Ve vaší aplikaci můžete vytvořit jeden dotaz, který načítá aktuální data a je třeba spustit opakovaně v některých intervalech načíst pokaždé, když různé výsledky.  
  
### <a name="forcing-immediate-execution"></a>Vynucení okamžitého provedení  
 Dotazy, které provádějí funkce agregace v rozsahu prvků zdroje musí nejprve iteraci přes tyto elementy. Příklady takových dotazů jsou `Count`, `Max`, `Average`, a `First`. Provádějí se bez explicitního `foreach` příkaz protože samotný dotaz musí používat `foreach` k vrácení výsledku. Všimněte si také, že tyto typy dotazů vrací jedinou hodnotu, není `IEnumerable` kolekce. Následující dotaz vrátí počet sudých čísel ve zdrojovém poli:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Chcete-li vynutit okamžité spuštění libovolného dotazu a výsledky do mezipaměti, můžete volat <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> metody.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Můžete také vynutit spuštění vložením `foreach` smyčky ihned za výraz dotazu. Však voláním `ToList` nebo `ToArray` také mezipaměti všech dat v jednoho objektu kolekce.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Návod: Zápis dotazů vC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Návod: Zápis dotazů vC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [foreach, in](../../../../csharp/language-reference/keywords/foreach-in.md)
- [Klíčová slova dotazu (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
