---
title: Napište svůj první dotaz LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: f426aac5358837563081d2bf9783f6d4fe04d853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Napište svůj první dotaz LINQ (Visual Basic)
A *dotazu* je výraz, který načte data z datového zdroje. Dotazy jsou vyjádřeny v jazyce vyhrazené dotazu. V průběhu času různé jazyky byly vyvinuty pro různé typy datových zdrojů, například SQL pro relační databáze a XQuery pro formát XML. Díky tomu je nezbytné pro vývojáře aplikace Další informace o nový jazyk dotazu pro každý typ zdroje dat nebo formát dat, která je podporována.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] zjednodušuje situaci prostřednictvím nabídky konzistentní model pro práci s daty mezi různé druhy zdrojů dat a formáty. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, které jsou vždy práce s objekty. Použijte stejný základní kódování vzory pro dotazování a transformovat data v dokumentů XML, databáze SQL, datové sady ADO.NET a entity, rozhraní .NET Framework kolekce a všechny další zdroje nebo formátu pro kterou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele je k dispozici. Tento dokument popisuje tři fáze vytváření a používání basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy.  
  
## <a name="three-stages-of-a-query-operation"></a>Tři fáze operace dotazu  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operace dotazů se skládá ze tří akcí:  
  
1.  Získáte zdroj dat nebo zdroje.  
  
2.  Vytvořte dotaz.  
  
3.  Provedení dotazu.  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], provádění dotazu se liší od vytvoření dotazu. Žádná data načíst není právě vytvořením dotazu. Tento bod je podrobněji popsána dále v tomto tématu.  
  
 Následující příklad ukazuje tři části operaci dotazu. V příkladu pole celých čísel jako zdroj dat vhodné pro demonstrační účely. Koncepty však také použít na jiné zdroje dat.  
  
> [!NOTE]
>  Na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ujistěte se, že **Option infer –** je nastaven na **na**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Výstup:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Zdroj dat  
 Protože zdroj dat v předchozím příkladu je pole, implicitně podporuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Je tato skutečnost, že vám umožní použít jako zdroj dat pro pole [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu. Typy podporující <xref:System.Collections.Generic.IEnumerable%601> nebo odvozené rozhraní, jako je například obecná <xref:System.Linq.IQueryable%601> se nazývají *dotazovatelné typy*.  
  
 Jako typ implicitně dotazovatelný pole nevyžaduje žádné úpravy ani zvláštní zacházení, která bude sloužit jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat. Totéž platí pro jakýkoli typ kolekce, která podporuje <xref:System.Collections.Generic.IEnumerable%601>, včetně obecná <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>a jiné třídy v knihovně tříd rozhraní .NET Framework.  
  
 Pokud zdrojová data již neimplementuje <xref:System.Collections.Generic.IEnumerable%601>, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele je nutná k implementaci funkce *standardní operátory dotazu* pro tento zdroj dat. Například [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zpracovává práci při načítání dokumentu XML do dotazovatelné <xref:System.Xml.Linq.XElement> zadejte, jak je znázorněno v následujícím příkladu. Další informace o standardních operátorů dotazu najdete v tématu [standardní dotaz přehled operátory (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 S [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], je nejprve vytvořit k objektu relační mapování v době návrhu, buď ručně, nebo pomocí [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) v sadě Visual Studio. Zápis dotazů u těchto objektů a při spuštění [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zpracovává komunikaci s databází. V následujícím příkladu `customers` představuje určité tabulky v databázi, a <xref:System.Data.Linq.Table%601> podporuje obecného <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Další informace o tom, jak vytvořit konkrétní typy zdrojů dat naleznete v dokumentaci pro různé [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatele. (Seznam těchto poskytovatelů najdete v tématu [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) Základní pravidlo je jednoduchý: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zdroj dat je libovolný objekt, který podporuje obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo rozhraní, které dědí z něj.  
  
> [!NOTE]
>  Typy, jako <xref:System.Collections.ArrayList> podporující neobecnou <xref:System.Collections.IEnumerable> rozhraní lze také jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] datové zdroje. Pro příklad, který se používá <xref:System.Collections.ArrayList>, najdete v části [postup: dotazu na ArrayList pomocí LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Dotaz  
 V dotazu určete, jaké informace můžete obnovit ze zdroje dat nebo zdroje. Máte také možnost určení, jak tyto informace by měla být seřazen, seskupené nebo strukturovaná před vrácením. Umožnit vytvoření dotazu jazyka Visual Basic má součástí nové syntaxe dotazu jazyka.  
  
 Při spuštění, dotaz v následujícím příkladu vrací sudá čísla z pole celé číslo, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Výraz dotazu obsahuje tři klauzule: `From`, `Where`, a `Select`. Konkrétní funkci a účel jednotlivých klauzule výraz dotazu je popsána v [základní operace dotazů (Visual Basic)](basic-query-operations.md). Další informace najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/queries.md). Všimněte si, že v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], definice dotazu často je uložené v proměnné a provést později. Dotaz proměnných, například `evensQuery` v předchozím příkladu, musí být typu dotazovatelnosti. Typ `evensQuery` je `IEnumerable(Of Integer)`, přiřazené kompilátorem pomocí odvození místního typu.  
  
 Je důležité si pamatovat, proměnné v dotazu samotné neprovede žádnou akci a vrátí žádná data. Ukládá jenom definice dotazu. V předchozím příkladu je `For Each` smyčky, který provede daný dotaz.  
  
## <a name="query-execution"></a>Provádění dotazů  
 Při provádění dotazu je oddělené od vytvoření dotazu. Vytváření dotazu definuje dotaz, ale provedení se aktivuje jiný mechanismus. Dotaz mohou být provedeny, jakmile je definována (*okamžité spuštění*), nebo mohou být uloženy definice a dotaz můžete spustit později (*odložené spouštění*).  
  
### <a name="deferred-execution"></a>Odložené provedení  
 Typické [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu podobá v předchozím příkladu, ve kterém `evensQuery` je definována. Vytvoří dotaz, ale nepracuje se okamžitě. Místo toho je definice dotazu uložené v proměnné dotazu `evensQuery`. Provést dotaz později, obvykle pomocí `For Each` smyčky, která vrátí hodnotu pořadí hodnot nebo použitím operátoru standardní dotazu, jako například `Count` nebo `Max`. Tento proces se označuje jako *odložené spouštění*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Pořadí hodnot, máte přístup k načtená data pomocí proměnné iterace ve `For Each` smyčky (`number` v předchozím příkladu). Protože proměnnou dotazu `evensQuery`, obsahuje definice dotazu a nikoli výsledky dotazu, můžete spustit dotaz tak často, jak chcete, aby pomocí proměnné dotazu více než jednou. Například může mít databázi ve vaší aplikaci, který se právě aktualizuje průběžně samostatné aplikace. Poté, co jste vytvořili dotaz, který načte data z této databáze, můžete použít `For Each` cykly opakovaného provést dotaz, načítání pokaždé, když nejnovější data.  
  
 Následující příklad ukazuje, jak odložené provedení funguje. Po `evensQuery2` je definovaný a provést s `For Each` cykly některé prvky ve zdroji dat jako v předchozích příkladech `numbers` došlo ke změně. Potom druhý `For Each` smyčka spuštěna `evensQuery2` znovu. Výsledky se liší podruhé, protože `For Each` smyčky provede daný dotaz znovu pomocí nových hodnot v `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Výstup:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Okamžité provedení  
 V odložené provedení dotazů definice dotazu je uložené v proměnné dotazu na pozdější dobu. V okamžité spuštění je dotaz proveden v době jeho definice. Provedení se aktivuje, když použijete metodu, která vyžaduje přístup na jednotlivé prvky výsledku dotazu. Často okamžité spuštění je nucen pomocí jedné z operátory standardní dotazu, které vracejí jedné hodnoty. Příklady `Count`, `Max`, `Average`, a `First`. Tyto standardní operátory dotazu spustit dotaz, jakmile budou použity k výpočtu a vrácení výsledku typu singleton. Další informace o standardních operátorů dotazu vracející jedné hodnoty, najdete v části [agregační operace](aggregation-operations.md), [operace s elementy](element-operations.md), a [operace kvantifikátoru](quantifier-operations.md).  
  
 Následující dotaz vrací počet sudým číslům v poli celých čísel. Definice dotazu se neuloží, a `numEvens` je jednoduchý `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Stejného výsledku můžete dosáhnout pomocí `Aggregate` metoda.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Můžete taky přinutit, provádění dotazu voláním `ToList` nebo `ToArray` metoda v dotazu (okamžitou) nebo proměnné dotazu (odložené), jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 V předchozích příkladech `evensQuery3` je dotaz proměnné, ale `evensList` je seznam a `evensArray` je pole.  
  
 Pomocí `ToList` nebo `ToArray` Pokud chcete vynutit okamžitou spuštění je obzvláště užitečná v případech, ve kterých chcete provést dotaz okamžitě a výsledky v objektu jedinou kolekci do mezipaměti. Další informace o těchto metodách v tématu [převádění datových typů](converting-data-types.md).  
  
 Může také způsobit dotaz, který provést pomocí `IEnumerable` metoda, jako <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> metoda.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](getting-started-with-linq.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Přehled standardních operátorů dotazu (Visual Basic)](standard-query-operators-overview.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Dotazy](../../../../visual-basic/language-reference/queries/queries.md)
