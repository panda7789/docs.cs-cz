---
title: Vytvoření prvního dotazu v jazyce LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: addf35afa2a4c88faf73ebc3d60fbcf9c4db1518
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636702"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Napište svůj první dotaz LINQ (Visual Basic)
*Dotaz* je výraz, který načítá data ze zdroje dat. Dotazy jsou vyjádřeny ve vyhrazeném dotazovacím jazyce. V průběhu času byly vyvinuty různé jazyky pro různé typy zdrojů dat, například SQL pro relační databáze a XQuery pro XML. To umožňuje vývojářům aplikací zjistit nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který je podporovaný.  
  
 LINQ (Language-Integrated Query) zjednodušuje situaci tím, že nabízí jednotný model pro práci s daty napříč různými druhy datových zdrojů a formátů. V dotazu LINQ budete vždy pracovat s objekty. Použijete stejné základní vzory kódování pro dotazování a transformaci dat v dokumentech XML, databázích SQL, ADO.NET datových sadách a entitách, .NET Framework kolekcích a jakémkoli jiném zdroji nebo formátu, pro který je poskytovatel LINQ k dispozici. Tento dokument popisuje tři fáze vytváření a používání základních dotazů LINQ.  
  
## <a name="three-stages-of-a-query-operation"></a>Tři fáze operace dotazu  
 Operace dotazů LINQ se skládají ze tří akcí:  
  
1. Získání zdroje dat nebo zdrojů.  
  
2. Vytvořte dotaz.  
  
3. Spusťte dotaz.  
  
 V LINQ je spuštění dotazu odlišné od vytvoření dotazu. Nenačtete žádná data pouhým vytvořením dotazu. Tento bod je podrobněji popsán dále v tomto tématu.  
  
 Následující příklad znázorňuje tři části operace dotazu. V příkladu se jako vhodný zdroj dat pro demonstrační účely používá pole celých čísel. Stejné koncepty se však vztahují i na jiné zdroje dat.  
  
> [!NOTE]
> Na [stránce kompilovat Návrháře projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)zajistěte, aby byla **možnost odvoditelné** na hodnotu **zapnuto**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Výstup:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Zdroj dat  
 Vzhledem k tomu, že zdroj dat v předchozím příkladu je pole, implicitně podporuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Je to fakt, který umožňuje použít pole jako zdroj dat pro dotaz LINQ. Typy, které podporují <xref:System.Collections.Generic.IEnumerable%601> nebo odvozené rozhraní, jako je obecný <xref:System.Linq.IQueryable%601>, se nazývají *Queryable typy*.  
  
 Jako implicitně Queryable typ pole nevyžaduje žádné úpravy nebo speciální zacházení, které slouží jako zdroj dat LINQ. Totéž platí pro jakýkoli typ kolekce, který podporuje <xref:System.Collections.Generic.IEnumerable%601>, včetně obecných <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>a dalších tříd v knihovně tříd .NET Framework.  
  
 Pokud zdrojová data ještě <xref:System.Collections.Generic.IEnumerable%601>neimplementují, je k implementaci funkcí *standardních operátorů dotazu* pro daný zdroj dat nutný poskytovatel LINQ. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zpracovává práci dokumentu XML do Queryable <xref:System.Xml.Linq.XElement> typu, jak je znázorněno v následujícím příkladu. Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]nejprve vytvoříte mapování relačních objektů v době návrhu, a to buď ručně, nebo pomocí [LINQ to SQL nástrojů v aplikaci Visual](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Studio v aplikaci Visual Studio. Zapisujete dotazy na objekty a v době běhu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává komunikaci s databází. V následujícím příkladu `customers` představuje konkrétní tabulku v databázi a <xref:System.Data.Linq.Table%601> podporuje obecné <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Další informace o tom, jak vytvořit konkrétní typy zdrojů dat, naleznete v dokumentaci pro různé zprostředkovatele LINQ. (Seznam těchto zprostředkovatelů naleznete v tématu [LINQ (jazykově integrovaný dotaz)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Základní pravidlo je jednoduché: zdroj dat LINQ je libovolný objekt, který podporuje obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601>, nebo rozhraní, které z něj dědí.  
  
> [!NOTE]
> Typy jako <xref:System.Collections.ArrayList> podporující neobecné <xref:System.Collections.IEnumerable> rozhraní lze také použít jako zdroje dat LINQ. Příklad, který používá <xref:System.Collections.ArrayList>, naleznete v tématu [How to: Query objektu ArrayList with LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Dotaz  
 V dotazu určíte, jaké informace chcete načíst ze zdroje dat nebo zdrojů. Máte také možnost určit, jak se tyto informace mají seřadit, seskupit nebo strukturovat před tím, než se vrátí. Pokud chcete povolit vytváření dotazů, Visual Basic zahrnul do jazyka novou syntaxi dotazu.  
  
 Při spuštění dotaz v následujícím příkladu vrátí všechna sudá čísla z pole typu Integer, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Výraz dotazu obsahuje tři klauzule: `From`, `Where`a `Select`. Konkrétní funkce a účel každé klauzule dotazového výrazu jsou popsány v tématu [základní operace dotazů (Visual Basic)](basic-query-operations.md). Další informace najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/index.md). Všimněte si, že v LINQ je definice dotazu často uložená v proměnné a provede se později. Proměnná dotazu, například `evensQuery` v předchozím příkladu, musí být typu Queryable. Typ `evensQuery` je `IEnumerable(Of Integer)`přiřazený kompilátorem pomocí odvození místního typu.  
  
 Je důležité si uvědomit, že proměnná dotazu sám neprovede žádnou akci a nevrátí žádná data. Ukládá pouze definici dotazu. V předchozím příkladu je to smyčka `For Each`, která spouští dotaz.  
  
## <a name="query-execution"></a>Provádění dotazů  
 Provádění dotazů je oddělené od vytvoření dotazu. Vytvoření dotazu definuje dotaz, ale provádění je aktivováno jiným mechanismem. Dotaz může být proveden hned po definování (*okamžité provedení*), nebo může být definice uložena a dotaz může být proveden později (*odložené spuštění*).  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Typický dotaz LINQ se podobá v předchozím příkladu, ve kterém je definována `evensQuery`. Vytvoří dotaz, ale nespustí ho hned. Místo toho je definice dotazu uložena v proměnné dotazu `evensQuery`. Dotaz spouštíte později, obvykle pomocí `For Each` smyčky, která vrací sekvenci hodnot, nebo použitím standardního operátoru dotazu, jako je například `Count` nebo `Max`. Tento proces se označuje jako *odložené provádění*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 V případě posloupnosti hodnot získáte přístup k načteným datům pomocí proměnné iterace ve smyčce `For Each` (`number` v předchozím příkladu). Vzhledem k tomu, že proměnná dotazu `evensQuery`obsahuje definici dotazu namísto výsledků dotazu, můžete spustit dotaz tak často, jak chcete, pomocí proměnné dotazu více než jednou. Můžete mít například databázi ve vaší aplikaci, která je průběžně aktualizována samostatnou aplikací. Po vytvoření dotazu, který načte data z této databáze, můžete pomocí smyčky `For Each` spustit dotaz opakovaně a kdykoli načíst nejnovější data.  
  
 Následující příklad ukazuje, jak odložené provádění funguje. Po definování a provedení `evensQuery2` se smyčkou `For Each`, jako v předchozích příkladech se změnily některé prvky ve zdroji dat `numbers`. Pak se druhá `For Each`ová smyčka spustí znovu `evensQuery2`. Výsledky se liší podruhé, protože smyčka `For Each` znovu spustí dotaz pomocí nových hodnot v `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Výstup:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Okamžité provedení  
 V odloženém spuštění dotazů je definice dotazu uložena v proměnné dotazu pro pozdější spuštění. V bezprostředním provádění se dotaz spustí v době jeho definice. Spuštění se aktivuje při použití metody, která vyžaduje přístup k jednotlivým prvkům výsledku dotazu. Okamžité provedení je vynuceno pomocí jednoho ze standardních operátorů dotazu, který vrací jednotlivé hodnoty. Příklady jsou `Count`, `Max`, `Average`a `First`. Tyto standardní operátory dotazování spustí dotaz hned po použití, aby bylo možné vypočítat a vrátit výsledek typu singleton. Další informace o standardních operátorech dotazu, které vracejí jednotlivé hodnoty, naleznete v tématu [operace agregace](aggregation-operations.md), [operace elementů](element-operations.md)a [kvantifikátory operací](quantifier-operations.md).  
  
 Následující dotaz vrátí počet sudých čísel v poli celých čísel. Definice dotazu není uložena a `numEvens` je jednoduchý `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Stejný výsledek můžete dosáhnout pomocí metody `Aggregate`.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Můžete také vynutit provedení dotazu voláním metody `ToList` nebo `ToArray` na dotaz (bezprostřední) nebo v proměnné dotazu (odloženo), jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 V předchozích příkladech je `evensQuery3` proměnnou dotazu, ale `evensList` je seznam a `evensArray` je pole.  
  
 Použití `ToList` nebo `ToArray` k vynucení okamžitého provedení je zvlášť užitečné ve scénářích, ve kterých chcete spustit dotaz okamžitě, a uložit výsledky do mezipaměti v jediném objektu kolekce. Další informace o těchto metodách naleznete v tématu [Převod datových typů](converting-data-types.md).  
  
 Můžete také způsobit provedení dotazu pomocí `IEnumerable` metody, jako je například metoda <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme pomocí LINQ v Visual Basic](getting-started-with-linq.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
