---
title: Napište svůj první dotaz LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951998"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Napište svůj první dotaz LINQ (Visual Basic)
*Dotaz* je výraz, který načítá data ze zdroje dat. Dotazy jsou vyjádřeny ve vyhrazeném dotazovacím jazyce. V průběhu času byly vyvinuty různé jazyky pro různé typy zdrojů dat, například SQL pro relační databáze a XQuery pro XML. To umožňuje vývojářům aplikací zjistit nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který je podporovaný.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]zjednodušuje situaci tím, že nabízí jednotný model pro práci s daty napříč různými druhy datových zdrojů a formátů. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] V dotazu vždy pracujete s objekty. Použijete stejné základní vzory kódování pro dotazování a transformaci dat v dokumentech XML, databázích SQL, ADO.NET datových sadách a entitách, .NET Framework kolekcích a jakémkoli jiném zdroji nebo formátu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , pro který je poskytovatel k dispozici. Tento dokument popisuje tři fáze vytváření a používání základních [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů.  
  
## <a name="three-stages-of-a-query-operation"></a>Tři fáze operace dotazu  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]operace dotazů se skládají ze tří akcí:  
  
1. Získání zdroje dat nebo zdrojů.  
  
2. Vytvořte dotaz.  
  
3. Spusťte dotaz.  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]nástroji se provedení dotazu liší od vytvoření dotazu. Nenačtete žádná data pouhým vytvořením dotazu. Tento bod je podrobněji popsán dále v tomto tématu.  
  
 Následující příklad znázorňuje tři části operace dotazu. V příkladu se jako vhodný zdroj dat pro demonstrační účely používá pole celých čísel. Stejné koncepty se však vztahují i na jiné zdroje dat.  
  
> [!NOTE]
> Na [stránce kompilovat Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)zajistěte, aby byla **možnost** odvoditelné na hodnotu **zapnuto**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Výstup:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Zdroj dat  
 Vzhledem k tomu, že zdroj dat v předchozím příkladu je pole, implicitně podporuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Je to fakt, který umožňuje použít pole jako zdroj dat pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz. Typy, které <xref:System.Collections.Generic.IEnumerable%601> podporují nebo odvozené rozhraní, jako je například <xref:System.Linq.IQueryable%601> obecné, se nazývají *Queryable typy*.  
  
 Jako implicitně Queryable typ pole nevyžaduje žádné úpravy nebo speciální zacházení, které slouží jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat. Totéž platí pro jakýkoli typ kolekce, který podporuje <xref:System.Collections.Generic.IEnumerable%601>, včetně obecných <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>a dalších tříd v knihovně tříd .NET Framework.  
  
 Pokud zdrojová data ještě nejsou implementovaná <xref:System.Collections.Generic.IEnumerable%601> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , je nutné, aby zprostředkovatel implementoval funkce *standardních operátorů dotazu* pro daný zdroj dat. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zpracovává práci dokumentu XML do typu Queryable <xref:System.Xml.Linq.XElement> , jak je znázorněno v následujícím příkladu. Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Pomocí [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]nástroje nejprve vytvoříte mapování relačních objektů v době návrhu, a to buď ručně, nebo pomocí [LINQ to SQLch nástrojů v aplikaci Visual](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Studio v aplikaci Visual Studio. Zapisujete dotazy na objekty a v době běhu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává komunikaci s databází. V následujícím příkladu `customers` představuje konkrétní tabulku v databázi a <xref:System.Data.Linq.Table%601> podporuje obecné <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Další informace o tom, jak vytvořit konkrétní typy zdrojů dat, najdete v dokumentaci pro různé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele. (Seznam těchto zprostředkovatelů naleznete v tématu [LINQ (jazykově integrovaný dotaz)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Základní pravidlo je jednoduché: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat je libovolný objekt, který podporuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, nebo rozhraní, které z něj dědí.  
  
> [!NOTE]
> Typy, jako je například podpora neobecného <xref:System.Collections.IEnumerable> rozhraní, lze také použít jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroje dat. <xref:System.Collections.ArrayList> Příklad, který používá <xref:System.Collections.ArrayList>, naleznete v tématu [How to: Dotazování objektu ArrayList pomocí LINQ (Visual Basic](how-to-query-an-arraylist-with-linq.md)).  
  
## <a name="the-query"></a>Dotaz  
 V dotazu určíte, jaké informace chcete načíst ze zdroje dat nebo zdrojů. Máte také možnost určit, jak se tyto informace mají seřadit, seskupit nebo strukturovat před tím, než se vrátí. Pokud chcete povolit vytváření dotazů, Visual Basic zahrnul do jazyka novou syntaxi dotazu.  
  
 Při spuštění dotaz v následujícím příkladu vrátí všechna sudá čísla z celočíselného pole, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Výraz dotazu obsahuje tři klauzule: `From`, `Where`a `Select`. Konkrétní funkce a účel každé klauzule dotazového výrazu jsou popsány v tématu [základní operace dotazů (Visual Basic)](basic-query-operations.md). Další informace najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/index.md). Všimněte si, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]že v je definice dotazu často uložená v proměnné a provede se později. Proměnná dotazu, například `evensQuery` v předchozím příkladu, musí být typu Queryable. Typ `evensQuery` je`IEnumerable(Of Integer)`přiřazen kompilátorem pomocí odvození místního typu.  
  
 Je důležité si uvědomit, že proměnná dotazu sám neprovede žádnou akci a nevrátí žádná data. Ukládá pouze definici dotazu. V předchozím příkladu je `For Each` to smyčka, která spouští dotaz.  
  
## <a name="query-execution"></a>Provádění dotazů  
 Provádění dotazů je oddělené od vytvoření dotazu. Vytvoření dotazu definuje dotaz, ale provádění je aktivováno jiným mechanismem. Dotaz může být proveden hned po definování (*okamžité provedení*), nebo může být definice uložena a dotaz může být proveden později (*odložené spuštění*).  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Typický [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz se podobá v předchozím příkladu, ve kterém `evensQuery` je definována. Vytvoří dotaz, ale nespustí ho hned. Místo toho je definice dotazu uložena v proměnné `evensQuery`dotazu. Dotaz spouštíte později, obvykle pomocí `For Each` smyčky, která vrací sekvenci hodnot, nebo použitím standardního operátoru dotazu, `Count` například nebo `Max`. Tento proces se označuje jako *odložené provádění*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 V případě posloupnosti hodnot získáte přístup k načteným datům pomocí proměnné iterace ve `For Each` smyčce (`number` v předchozím příkladu). Vzhledem k tomu, že `evensQuery`proměnná dotazu obsahuje definici dotazu namísto výsledků dotazu, můžete spustit dotaz tak často, jak chcete, pomocí proměnné dotazu více než jednou. Můžete mít například databázi ve vaší aplikaci, která je průběžně aktualizována samostatnou aplikací. Po vytvoření dotazu, který načte data z této databáze, můžete použít `For Each` smyčku a spustit dotaz opakovaně a kdykoli načíst nejnovější data.  
  
 Následující příklad ukazuje, jak odložené provádění funguje. Po `evensQuery2` definování a spuštění `For Each` se smyčkou, jako v předchozích příkladech, se změní některé prvky ve zdroji `numbers` dat. Pak se znovu `For Each` spustí `evensQuery2` druhá smyčka. Výsledky se liší podruhé, protože `For Each` smyčka znovu spustí dotaz pomocí nových hodnot v. `numbers`  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Výstup:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Okamžité provedení  
 V odloženém spuštění dotazů je definice dotazu uložena v proměnné dotazu pro pozdější spuštění. V bezprostředním provádění se dotaz spustí v době jeho definice. Spuštění se aktivuje při použití metody, která vyžaduje přístup k jednotlivým prvkům výsledku dotazu. Okamžité provedení je vynuceno pomocí jednoho ze standardních operátorů dotazu, který vrací jednotlivé hodnoty. Příklady jsou `Count` `Max` ,,a`First`. `Average` Tyto standardní operátory dotazování spustí dotaz hned po použití, aby bylo možné vypočítat a vrátit výsledek typu singleton. Další informace o standardních operátorech dotazu, které vracejí jednotlivé hodnoty, naleznete v tématu [operace agregace](aggregation-operations.md), [operace elementů](element-operations.md)a [kvantifikátory operací](quantifier-operations.md).  
  
 Následující dotaz vrátí počet sudých čísel v poli celých čísel. Definice dotazu není uložena a `numEvens` je jednoduchá. `Integer`  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Stejný výsledek můžete dosáhnout pomocí `Aggregate` metody.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Můžete také vynutit provedení dotazu voláním `ToList` metody nebo `ToArray` na dotaz (bezprostřední) nebo proměnnou dotazu (odloženo), jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 V předchozích příkladech `evensQuery3` je proměnná dotazu, ale `evensList` je to seznam a `evensArray` je pole.  
  
 Použití `ToList` nebo`ToArray` k vynucení okamžitého provedení je zvlášť užitečné ve scénářích, ve kterých chcete spustit dotaz okamžitě, a uložit výsledky do mezipaměti v jediném objektu kolekce. Další informace o těchto metodách naleznete v tématu [Převod datových typů](converting-data-types.md).  
  
 Můžete také způsobit spuštění dotazu pomocí `IEnumerable` metody, jako je <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> například metoda.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme pomocí LINQ v Visual Basic](getting-started-with-linq.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
