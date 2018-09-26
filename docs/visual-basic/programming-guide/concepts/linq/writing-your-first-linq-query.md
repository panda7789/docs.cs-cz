---
title: Napište svůj první dotaz LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 4c04c00c5392d8ba363346b06c806ec79041c439
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109089"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Napište svůj první dotaz LINQ (Visual Basic)
A *dotazu* je výraz, který načte data z datového zdroje. Dotazy jsou vyjádřeny v vyhrazené dotazovací jazyk. V průběhu času různé jazyky byly vyvinuty pro různé typy zdrojů dat, například SQL pro relační databáze a XQuery pro XML. Díky tomu je nezbytné pro vývojáře aplikací získat nový dotazovací jazyk pro každý typ zdroje dat nebo formát dat, která je podporována.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] situaci zjednodušuje tím, že nabízí konzistentní model pro práci s daty napříč různými druhy datových zdrojů a formátů. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, které jsou vždy práce s objekty. Stejné základní vzorce kódování používáte k dotazování a transformaci dat v dokumentech XML, databází SQL, datovými sadami ADO.NET a entity, kolekcemi rozhraní .NET Framework a všechny ostatní zdroje nebo formátu pro kterou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele je k dispozici. Tento dokument popisuje tři fáze vytváření a využívání basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy.  
  
## <a name="three-stages-of-a-query-operation"></a>Tři fáze operace dotazu  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operace dotazování se skládá ze tří akcí:  
  
1.  Získání datového zdroje nebo zdrojů.  
  
2.  Vytvořte dotaz.  
  
3.  Spusťte dotaz.  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], provádění dotazu se liší od vytvoření dotazu. Není načíst žádná data pouhým vytvořením dotazu. Tento bod je podrobněji popsány dále v tomto tématu.  
  
 Následující příklad ukazuje tři části operace dotazu. V příkladu používá pole celých čísel jako zdroj dat praktické pro demonstrační účely. Ale stejné koncepty platí také pro jiné zdroje dat.  
  
> [!NOTE]
>  Na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ujistěte se, že **Option infer** je nastavena na **na**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Výstup:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Zdroj dat  
 Protože zdroj dat v předchozím příkladu je pole, implicitně podporuje Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Je tato skutečnost, že vám umožní použít jako zdroj dat pro pole [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Typy, které podporují <xref:System.Collections.Generic.IEnumerable%601> nebo odvozené rozhraní, jako je obecný <xref:System.Linq.IQueryable%601> se nazývají *dotazovatelné typy*.  
  
 Jako typ implicitně dotazovatelné pole vyžaduje žádné změny nebo zvláštní zacházení jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj. Totéž platí pro jakýkoli typ kolekce, která podporuje <xref:System.Collections.Generic.IEnumerable%601>, včetně Obecné <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>a jiných tříd v knihovně tříd rozhraní .NET Framework.  
  
 Pokud zdroj dat již neimplementuje <xref:System.Collections.Generic.IEnumerable%601>, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatele, je potřeba implementovat funkci *standardních operátorů pro dotazování* pro tento zdroj dat. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zpracovává práci při načítání dokumentu XML do dotazovatelného <xref:System.Xml.Linq.XElement> zadejte, jak je znázorněno v následujícím příkladu. Další informace o standardních operátorů pro dotazování, naleznete v tématu [přehled operátory standardního dotazu (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 S [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], nejprve vytvoříte objektově relační mapování v době návrhu ručně nebo pomocí [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) v sadě Visual Studio. Psát dotazy proti objektům a v době běhu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává vnitřní komunikaci s databází. V následujícím příkladu `customers` představuje určité tabulky v databázi, a <xref:System.Data.Linq.Table%601> podporuje Obecné <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Další informace o tom, jak vytváření určitých typů zdrojů dat, najdete v dokumentaci pro různé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelů. (Seznam z těchto zprostředkovatelů najdete v tématu [LINQ (Language-Integrated Query)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Základní pravidlo je jednoduchý: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat je libovolný objekt, který podporuje Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo rozhraní, které z něj dědí.  
  
> [!NOTE]
>  Typy, jako <xref:System.Collections.ArrayList> podporující neobecné <xref:System.Collections.IEnumerable> rozhraní může také sloužit jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdrojů. Příklad, který se používá <xref:System.Collections.ArrayList>, naleznete v tématu [postupy: vytvoření dotazu na ArrayList pomocí LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Dotaz  
 V dotazu určete, jaké informace, které chcete načíst ze zdroje dat nebo zdroje. Máte také možnost určení, jak tyto informace by měl být seřazeny, seskupeny nebo strukturované před vrácením. Pokud chcete povolit vytvoření dotazu, Visual Basic má součástí novou syntaxi dotazu jazyka.  
  
 Po spuštění, v následujícím příkladu dotaz vrátí všechna sudá čísla z celočíselné pole, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Výraz dotazu obsahuje tři věty: `From`, `Where`, a `Select`. Konkrétní funkci a účel každé klauzuli dotazu výrazu je podrobněji popsána [základní operace dotazů (Visual Basic)](basic-query-operations.md). Další informace najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/index.md). Všimněte si, že v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], definice dotazu často je uložen v proměnné a proveden později. Dotaz proměnných, například `evensQuery` v předchozím příkladu, musí být dotazovatelného typu. Typ `evensQuery` je `IEnumerable(Of Integer)`, přiřazené kompilátorem použití odvození místního typu.  
  
 Je dobré si uvědomit, že proměnná dotazu sama neprovede žádnou akci a nevrátí žádná data. Ukládá jenom definice dotazu. V předchozím příkladu je `For Each` smyčku, která spustí dotaz.  
  
## <a name="query-execution"></a>Provádění dotazů  
 Provedení dotazu se liší od vytvoření dotazu. Vytvoření dotazu definuje dotaz, ale provedení se aktivuje jiným způsobem. Dotaz může proveden, jakmile je definován (*okamžité spuštění*), nebo může být definice uložena a dotaz může být proveden později (*odložené provedení*).  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Typické [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu vypadá podobně jako v předchozím příkladu, ve kterém `evensQuery` je definována. Vytvoří dotaz, ale nespustí se okamžitě. Místo toho je definice dotazu uložena v proměnné dotazu `evensQuery`. Spustit dotaz později, obvykle pomocí `For Each` smyčku, která vrátí sekvenci hodnot nebo použitím operátoru standardního dotazu, jako například `Count` nebo `Max`. Tento proces se označuje jako *odložené provedení*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Pro sekvenci hodnot, získáte přístup k načtená data pomocí proměnné iterace ve `For Each` smyčky (`number` v předchozím příkladu). Protože proměnné dotazu `evensQuery`, udržuje definice dotazu spíše než výsledky dotazu dotaz můžete spustit tak často, jak chcete, aby pomocí proměnné dotazu víc než jednou. Například může mít databázi v aplikaci, která se průběžně aktualizuje pomocí samostatné aplikace. Jakmile vytvoříte dotaz, který načítá data z této databáze, můžete použít `For Each` smyčky k provedení dotazu opakovaně, pokaždé, když se načítají nejnovější data.  
  
 Následující příklad ukazuje, jak odložené provedení funguje. Po `evensQuery2` je definována a spuštěn `For Each` smyčky, stejně jako v předchozích příkladech můžou některé prvky ve zdroji dat `numbers` se změní. Potom sekundy `For Each` smyčka spuštěna `evensQuery2` znovu. Výsledky se liší podruhé, protože `For Each` cyklus se opakuje, dotaz znovu pomocí nové hodnoty v `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Výstup:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Okamžité provedení  
 V odložené provedení dotazů je definice dotazu uložena v proměnné dotazu pro pozdější provedení. V okamžité provedení spuštění dotazu v době jeho definici. Provedení se aktivuje, když použijete metodu, která vyžaduje přístup k jednotlivým elementům výsledku dotazu. Okamžité spuštění často musí pomocí jedné z standardních operátorů pro dotazování, které vrátí jednu hodnotu. Mezi příklady patří `Count`, `Max`, `Average`, a `First`. Tyto operátory standardního dotazu spusťte dotaz, jakmile se uplatní, pokud chcete vypočítat a vrátit výsledek typu singleton. Další informace o standardních operátorů dotazu, které vrací jednotlivé hodnoty, najdete v části [agregační operace](aggregation-operations.md), [operace s elementy](element-operations.md), a [operace kvantifikátoru](quantifier-operations.md).  
  
 Následující dotaz vrátí počet sudých čísel v poli celých čísel. Definice dotazů se neuloží, a `numEvens` je jednoduchý `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Můžete stejného výsledku dosáhnout pomocí `Aggregate` metody.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Můžete také vynutit spuštění dotazu pomocí volání `ToList` nebo `ToArray` metodu dotazu (okamžité) nebo proměnné dotazu (odložené), jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 V předchozích příkladech `evensQuery3` je dotaz proměnné, ale `evensList` je seznam a `evensArray` je pole.  
  
 Pomocí `ToList` nebo `ToArray` vynutit okamžité spuštění je zvláště užitečná v situacích, ve kterých chcete okamžitě spustit dotaz a ukládat do mezipaměti výsledky do jednoho objektu kolekce. Další informace o těchto metodách v tématu [převádění datových typů](converting-data-types.md).  
  
 Může také způsobit dotazu má být spuštěn s použitím `IEnumerable` metody, jako <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> metoda.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce Visual Basic](getting-started-with-linq.md)  
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
- [Přehled standardních operátorů dotazu (Visual Basic)](standard-query-operators-overview.md)  
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
- [Dotazy](../../../../visual-basic/language-reference/queries/index.md)
