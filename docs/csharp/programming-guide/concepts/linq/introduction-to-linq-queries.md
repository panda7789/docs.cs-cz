---
title: Úvod do dotazů LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: e3439d2e0e0fb8f3126770ec7922f5ae180f781b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418252"
---
# <a name="introduction-to-linq-queries-c"></a>Úvod do dotazů LINQ (C#)
*Dotaz* je výraz, který načítá data ze zdroje dat. Dotazy jsou obvykle vyjádřeny ve specializovaném dotazovacím jazyce. Různé jazyky byly vyvinuty v průběhu času pro různé typy zdrojů dat, například SQL pro relační databáze a XQuery pro XML. Proto se vývojářům musel naučit nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který musí podporovat. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] tuto situaci zjednodušuje tím, že nabízí jednotný model pro práci s daty napříč různými druhy datových zdrojů a formátů. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]m dotazu vždy pracujete s objekty. Použijete stejné základní vzory kódování pro dotazování a transformaci dat v dokumentech XML, databázích SQL, datových sadách ADO.NET, kolekcích .NET a jakémkoli jiném formátu, pro který je k dispozici poskytovatel [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="three-parts-of-a-query-operation"></a>Tři části operace dotazu  
 Všechny operace [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů se skládají ze tří různých akcí:  
  
1. Získání zdroje dat.  
  
2. Vytvořte dotaz.  
  
3. Spusťte dotaz.  
  
 Následující příklad ukazuje, jak jsou tři části operace dotazu vyjádřeny ve zdrojovém kódu. Příklad používá celočíselné pole jako zdroj dat pro usnadnění práce; stejné koncepty se však vztahují i na jiné zdroje dat. Tento příklad je odkazován v celém zbývající části tohoto tématu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Na následujícím obrázku vidíte kompletní operaci dotazování. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedení dotazu se liší od samotného dotazu; Jinými slovy, nezískali jste žádná data pouhým vytvořením proměnné dotazu.  
  
 ![Diagram úplné operace dotazu LINQ](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Zdroj dat  
 Vzhledem k tomu, že v předchozím příkladu je zdrojem dat pole, implicitně podporuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Tato skutečnost znamená, že se k ní dá dotázat pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Dotaz je spuštěn v příkazu `foreach` a `foreach` vyžaduje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Typy, které podporují <xref:System.Collections.Generic.IEnumerable%601> nebo odvozené rozhraní, jako je obecný <xref:System.Linq.IQueryable%601>, se nazývají *Queryable typy*.  
  
 Typ Queryable nevyžaduje žádnou úpravu ani zvláštní úpravu, aby sloužil jako zdroj dat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Pokud zdrojová data ještě nejsou v paměti jako Queryable typ, poskytovatel [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ho musí reprezentovat jako takový. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] načte dokument XML do typu <xref:System.Xml.Linq.XElement> Queryable:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]nejprve vytvoříte relační mapování objektu v době návrhu buď ručně, nebo pomocí [LINQ to SQL nástrojů v aplikaci Visual](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Studio v aplikaci Visual Studio. Zapisujete dotazy na objekty a v době běhu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává komunikaci s databází. V následujícím příkladu `Customers` představuje konkrétní tabulku v databázi a typ výsledku dotazu, <xref:System.Linq.IQueryable%601>, je odvozen z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Další informace o tom, jak vytvořit konkrétní typy zdrojů dat, najdete v dokumentaci pro různé poskytovatele [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Základní pravidlo je ale velmi jednoduché: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat je libovolný objekt, který podporuje obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601>, nebo rozhraní, které z něj dědí.  
  
> [!NOTE]
> Typy jako <xref:System.Collections.ArrayList> podporující neobecné <xref:System.Collections.IEnumerable> rozhraní lze také použít jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat. Další informace najdete v tématu [Postup: dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="query"></a>Dotaz  
 Dotaz určuje, jaké informace se mají načíst ze zdroje dat nebo zdrojů. V případě potřeby dotaz také určuje, jak se mají tyto informace seřadit, seskupit a tvarovat před tím, než se vrátí. Dotaz je uložen v proměnné dotazu a inicializován pomocí výrazu dotazu. Pro snazší zápis dotazů C# zavedla novou syntaxi dotazu.  
  
 Dotaz v předchozím příkladu vrátí všechna sudá čísla z pole Integer. Výraz dotazu obsahuje tři klauzule: `from`, `where` a `select`. (Pokud znáte SQL, jste si všimli, že řazení klauzulí je obrácené z pořadí v SQL.) Klauzule `from` Určuje zdroj dat, klauzule `where` používá filtr a klauzule `select` určuje typ vrácených prvků. Tyto a další klauzule dotazu jsou podrobněji popsány v části [výrazy dotazů LINQ](../../../linq/index.md) . V současné době je důležité, aby v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]proměnná dotazu sám neprovede žádnou akci a nevrátí žádná data. Pouze ukládá informace, které jsou požadovány k vyprodukování výsledků při spuštění dotazu v pozdějším okamžiku. Další informace o tom, jak jsou dotazy vytvářeny na pozadí, naleznete v tématu [standardní operátoryC#dotazu Overview ()](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Dotazy lze také vyjádřit pomocí syntaxe metody. Další informace naleznete v tématu [syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Jak bylo uvedeno dříve, proměnná dotazu sama ukládá pouze příkazy dotazu. Skutečné provedení dotazu je odloženo, dokud neprovedete iteraci nad proměnnou dotazu v příkazu `foreach`. Tento koncept se označuje jako *odložené provedení* a je znázorněn v následujícím příkladu:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 Příkaz `foreach` je také místo, kde jsou načteny výsledky dotazu. Například v předchozím dotazu proměnná iterace `num` udržuje každou hodnotu (jednu v čase) ve vrácené sekvenci.  
  
 Vzhledem k tomu, že proměnná dotazu sama o sobě nemá výsledky dotazu, můžete ji spustit tak často, jak chcete. Můžete mít například databázi, která je průběžně aktualizována samostatnou aplikací. V aplikaci můžete vytvořit jeden dotaz, který načte nejnovější data, a můžete ho spustit opakovaně v určitém intervalu, abyste pokaždé získali různé výsledky.  
  
### <a name="forcing-immediate-execution"></a>Vynucení okamžitého provedení  
 Dotazy, které provádějí agregační funkce v rozsahu zdrojových elementů, musí nejprve iterovat přes tyto prvky. Příklady takových dotazů jsou `Count`, `Max`, `Average`a `First`. Tyto příkazy jsou spouštěny bez explicitního příkazu `foreach`, protože samotný dotaz musí použít `foreach`, aby mohl vracet výsledek. Všimněte si také, že tyto typy dotazů vrátí jednu hodnotu, nikoli kolekci `IEnumerable`. Následující dotaz vrátí počet sudých čísel ve zdrojovém poli:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Chcete-li vynutit okamžité provedení jakýchkoli dotazů a uložit výsledky do mezipaměti, můžete volat metody <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A>.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Můžete také vynutit provádění vložením `foreach` smyčky hned za výraz dotazu. Nicméně voláním `ToList` nebo `ToArray` ukládáte do mezipaměti také všechna data v jediném objektu kolekce.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce C#](/dotnet/csharp/programming-guide/concepts/linq/)
- [Návod: zápis dotazů vC#](./walkthrough-writing-queries-linq.md)
- [Výrazy dotazů LINQ](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Klíčová slova dotazu (LINQ)](../../../language-reference/keywords/query-keywords.md)
