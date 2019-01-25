---
title: Představení technologie LINQ v jazyce Visual Basic
ms.date: 08/28/2018
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
ms.openlocfilehash: 0642a67a6550109ffe1068e6c6ce4605b14c25af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524050"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Představení technologie LINQ v jazyce Visual Basic
Language Integrated Query (LINQ) přidává funkce dotazu do jazyka Visual Basic a při práci se všemi druhy dat poskytuje jednoduché a výkonné možnosti. Místo odeslání dotazu do databáze ke zpracování nebo práce s různou syntaxí dotazu pro každý typ hledaných dat, kterou hledáte, představuje LINQ dotazy jako součást jazyka Visual Basic. Používá jednotný syntax bez ohledu na typ data.  
  
 LINQ umožňuje dotazování na data z databáze serveru SQL Server, XML, polí v paměti a kolekcí, datovými sadami ADO.NET nebo kterýkoli jiný zdroj dat. vzdálené nebo místní, podporující LINQ. Provedete to všechno s společné prvky jazyka Visual Basic. Vzhledem k tomu, že jsou vaše dotazy napsány v jazyce Visual Basic, jsou vráceny výsledky dotazu jako silně typované objekty. Tyto objekty podporují technologii IntelliSense, která umožňuje psát kód rychleji a zachytit chyby v dotazech v době kompilace místo v době běhu. Dotazy LINQ lze použít jako zdroj dalších dotazů pro upřesnění výsledků. Mohou také být vázány na ovládací prvky tak, aby uživatelé mohou snadno zobrazit a upravit výsledky dotazu.  
  
 Například následující příklad kódu ukazuje dotaz LINQ, který vrátí seznam zákazníků z kolekce a skupiny, které je založené na jejich umístění.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Pro spuštění příkladů v úvodu a v [struktura dotazu LINQ](#structure-of-a-linq-query) oddílu, zahrňte následující kód, který vrátí seznam zákazníků a objednávek.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
## <a name="linq-providers"></a>Zprostředkovatelé dotazů LINQ  
 A *zprostředkovatele LINQ* dotazů LINQ jazyka Visual Basic se mapuje na zdroj dat, která je dotazována. Při psaní dotazu LINQ poskytovatel přebírá tento dotaz a přeloží ho do příkazů, které zdroje dat budou moci být prováděny. Poskytovatel také převádí data ze zdroje na objekty, které tvoří výsledek dotazu. Nakonec převede objekty na data při odeslání aktualizací do zdroje dat.  
  
 Visual Basic obsahuje následující poskytovatele LINQ.  
  
|Poskytovatel|Popis|  
|---|---|  
|LINQ na objekty|Poskytovateli LINQ to Objects umožňuje dotazování kolekce v paměti a pole. Pokud objekt podporuje buď <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní, poskytovatel LINQ to Objects umožňuje dotazování ho.<br /><br /> Můžete povolit poskytovateli LINQ to Objects pomocí importu <xref:System.Linq> obor názvů, která je importována ve výchozím nastavení pro všechny projekty jazyka Visual Basic.<br /><br /> Další informace o poskytovateli LINQ to Objects naleznete v tématu [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|Technologie LINQ to SQL|Poskytovateli LINQ to SQL umožňuje dotazování a modifikaci dat v databázi serveru SQL Server. To usnadňuje mapování modelu objektu pro aplikaci tabulek a objektů v databázi.<br /><br /> Visual Basic usnadňuje práci s LINQ to SQL a to včetně Návrháře relací objektů (O/R Designer). Tento návrhář slouží k vytvoření objektového modelu v aplikaci, která mapuje pro objekty v databázi. O/R Designer také přiřazuje funkce mapě uložených procedur a funkcí <xref:System.Data.Linq.DataContext> objektu, který skladuje komunikaci s databází a ukládá stav kontroly optimistické souběžnosti.<br /><br /> Další informace o technologii LINQ to SQL poskytovatele najdete v tématu [technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Další informace o Návrháři relací objektů naleznete v tématu [LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|Technologie LINQ to XML|LINQ to XML zprostředkovatele umožňuje dotazování a modifikaci XML. Můžete změnit paměť XML nebo je můžete načíst z XML a uložit XML do souboru.<br /><br /> Poskytovateli LINQ to XML navíc umožňuje literály XML a vlastnosti OS XML, které umožňují zapisovat XML přímo v kódu jazyka Visual Basic. Další informace najdete v tématu [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ na DataSet|Poskytovatel LINQ to DataSet umožňuje dotazování a aktualizace dat v [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové sady. Můžete přidat sílu LINQ pro aplikace, které používají datové sady, abyste zjednodušili a rozšířili schopnosti pro dotazování, agregaci a aktualizaci dat v datové sadě.<br /><br /> Další informace najdete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Struktura dotazu LINQ  
 Dotaz LINQ, označovaný také jako *výrazu dotazu*, se skládá z kombinace klauzulí dotazu, které identifikují zdroje dat a iterační proměnné pro dotaz. Výraz dotazu může také obsahovat pokyny pro řazení, filtrování, seskupování a spojování nebo výpočty vyrovnat zdrojová data. Syntaxe výrazu dotazu se podobá syntaxi SQL; Proto vám může připadat velká část syntaxe zkušenosti.  
  
 Výraz dotazu začíná `From` klauzuli. Tato klauzule určuje zdroje dat pro dotaz a proměnné, které se používají k odkazování na každý prvek zdroje dat samostatně. Tyto proměnné jsou pojmenovány *proměnné v rozsahu* nebo *iterační proměnné*. `From` Je vyžadována klauzule dotazu, s výjimkou `Aggregate` dotazy, kde `From` klauzule je volitelný. Po oboru a zdroje dotazu jsou uvedené v `From` nebo `Aggregate` klauzule, může obsahovat libovolnou kombinaci klauzulí dotazů k úpravě dotazu. Informace o klauzulích dotazu naleznete v tématu operátory dotazů LINQ jazyka Visual Basic dále v tomto tématu. Například následující dotaz Určuje zdrojovou kolekci zákaznických dat, jako `customers` proměnné a iterační proměnnou s názvem `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 Tento příklad je platný dotaz sám; Nicméně dotaz mnohem výkonnější při přidání další klauzule dotazu pro upřesnění výsledků. Například můžete přidat `Where` klauzule můžete filtrovat výsledky podle jedné nebo více hodnot. Výrazy dotazu představují jeden řádek kódu. Další klauzule dotazu můžete přidat pouze na konec dotazu. Dotaz můžete rozdělit přes více řádků textu, aby se zlepšila čitelnost pomocí podtržítka (\_) znak pro pokračování řádku. Následující příklad kódu ukazuje příklad dotazu, který zahrnuje `Where` klauzuli.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Další výkonnou klauzulí dotazu je `Select` klauzuli, která umožňuje vrátit pouze vybraná pole ze zdroje dat. Dotazy LINQ vrací vyčíslitelné kolekce výrazných objektů. Dotaz může vrátit kolekci anonymních typů nebo pojmenovaných typů. Můžete použít `Select` klauzuli pro vrácení pouze jedno pole ze zdroje dat. Když toto provedete, typ vrácené kolekce je typ tohoto jednoho pole. Můžete také použít `Select` klauzuli pro vrácení více polí ze zdroje dat. Když toto provedete, typ vrácené kolekce je nový anonymní typ. Můžete také porovnat pole vrácená dotazem s poli zadaného názvu typu. Následující příklad kódu ukazuje výraz dotazu, který vrátí kolekci anonymních typů, jejichž členové obsahují data z vybraných polí ze zdroje dat.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 Dotazy LINQ lze také kombinovat více zdrojů dat a vrácení jednoho výsledku. To můžete udělat s jedním nebo více `From` klauzule, nebo pomocí `Join` nebo `Group Join` klauzulí dotazů. Následující příklad kódu ukazuje výraz dotazu, který kombinuje data odběratele a objednávky a vrátí kolekci anonymních typů s daty odběratele a objednávky.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Můžete použít `Group Join` klauzule vytvoření hierarchického dotazu výsledku, který obsahuje kolekci objektů zákazníka. Každý objekt zákazníka má vlastnost, která obsahuje kolekci všech objednávek tohoto zákazníka. Následující příklad kódu ukazuje výraz dotazu, který jako hierarchické kombinuje data odběratele a objednávky a vrátí kolekci anonymních typů. Dotaz vrátí typ, který zahrnuje `CustomerOrders` vlastnost, která obsahuje kolekci dat objednávky zákazníka. Zahrnuje také `OrderTotal` vlastnost, která obsahuje součet součtů pro všechny objednávky daného zákazníka. (Tento dotaz je ekvivalentní k LEFT OUTER JOIN).  
  
 [!code-vb[VbVbalrIntroToLINQ#6](codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Existuje několik dalších operátorů dotazu LINQ, které vám umožní vytvářet výkonné výrazy dotazů. Další části tohoto tématu popisuje různé klauzule dotazu, které můžete zahrnout do výrazu dotazu. Informace o klauzulích dotazu jazyka Visual Basic, naleznete v tématu [dotazy](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Operátory dotazů LINQ jazyka Visual Basic  

Třídy v <xref:System.Linq> obor názvů a jiných oborech názvů, které podporují dotazy LINQ, zahrnují metody, které můžete volat a vytvářet a upřesnit tak dotazy v závislosti na potřebách vaší aplikace. Visual Basic obsahuje klíčová slova pro následující běžné klauzule dotazu. Informace o klauzulích dotazu jazyka Visual Basic, naleznete v tématu [dotazy](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Klauzule From

Buď [ `From` klauzule](../../../../visual-basic/language-reference/queries/from-clause.md) nebo `Aggregate` klauzule je vyžadována na začátku dotazu. A `From` klauzule Určuje zdrojovou kolekci a proměnnou iterace pro dotaz. Příklad:

[!code-vb[VbVbalrIntroToLINQ#7](codesnippet/VisualBasic/introduction-to-linq_8.vb)]

### <a name="select-clause"></a>Select – klauzule

Volitelné. A [ `Select` klauzule](../../../../visual-basic/language-reference/queries/select-clause.md) deklaruje sadu iteračních proměnných pro dotaz. Příklad:

[!code-vb[VbVbalrIntroToLINQ#8](codesnippet/VisualBasic/introduction-to-linq_9.vb)]

Pokud `Select` není zadána klauzule, iterační proměnné pro dotaz jsou tvořeny iteračními proměnnými určenými klauzulí `From` nebo `Aggregate` klauzuli.

### <a name="where-clause"></a>Klauzule Where

Volitelné. A [ `Where` klauzule](../../../../visual-basic/language-reference/queries/where-clause.md) Určuje podmínku filtrování dotazu. Příklad:

[!code-vb[VbVbalrIntroToLINQ#9](codesnippet/VisualBasic/introduction-to-linq_10.vb)]

### <a name="order-by-clause"></a>Klauzule ORDER by]

| Volitelné. [ `Order By` Klauzule](../../../../visual-basic/language-reference/queries/order-by-clause.md) určuje pořadí řazení pro sloupce v dotazu. Příklad:

[!code-vb[VbVbalrIntroToLINQ#10](codesnippet/VisualBasic/introduction-to-linq_11.vb)]

### <a name="join-clause"></a>Join – klauzule

Volitelné. A [ `Join` klauzule](../../../../visual-basic/language-reference/queries/join-clause.md) kombinuje dvě kolekce do jedné kolekce. Příklad:

[!code-vb[VbVbalrIntroToLINQ#11](codesnippet/VisualBasic/introduction-to-linq_12.vb)]

### <a name="group-by-clause"></a>Group By – klauzule

Volitelné. A [ `Group By` klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md) seskupuje prvky sady výsledků dotazu. Slouží k aplikaci agregačních funkcí na každou skupinu. Příklad:

[!code-vb[VbVbalrIntroToLINQ#12](codesnippet/VisualBasic/introduction-to-linq_13.vb)]

### <a name="group-join-clause"></a>Group Join – klauzule

Volitelné. A [ `Group Join` klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md) kombinuje dvě kolekce do jedné hierarchické kolekce. Příklad:

[!code-vb[VbVbalrIntroToLINQ#13](codesnippet/VisualBasic/introduction-to-linq_14.vb)]

### <a name="aggregate-clause"></a>Aggregate – klauzule

Buď [ `Aggregate` klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md) nebo `From` klauzule je vyžadována na začátku dotazu. `Aggregate` Klauzule použije jeden nebo více agregačních funkcí na kolekci. Například můžete použít `Aggregate` klauzule a vypočítat součet všech prvků vrácených dotazem, stejně jako v následujícím příkladu.

[!code-vb[VbVbalrIntroToLINQ#14](codesnippet/VisualBasic/introduction-to-linq_15.vb)]

Můžete také použít `Aggregate` klauzuli pro úpravu dotazu. Například můžete použít `Aggregate` k provedení výpočtu v kolekci souvisejících dotazů. Příklad:

[!code-vb[VbVbalrIntroToLINQ#15](codesnippet/VisualBasic/introduction-to-linq_16.vb)]

### <a name="let-clause"></a>Let – klauzule

Volitelné. A [ `Let` klauzule](../../../../visual-basic/language-reference/queries/let-clause.md) vypočítá hodnotu a přiřadí ji nové proměnné v dotazu. Příklad:

[!code-vb[VbVbalrIntroToLINQ#16](codesnippet/VisualBasic/introduction-to-linq_17.vb)]

### <a name="distinct-clause"></a>Distinct – klauzule

Volitelné. A `Distinct` klauzule omezí hodnoty aktuální iterační proměnné a odstraní tak duplicitní hodnoty ve výsledcích dotazu. Příklad:

[!code-vb[VbVbalrIntroToLINQ#17](codesnippet/VisualBasic/introduction-to-linq_18.vb)]

### <a name="skip-clause"></a>Skip – klauzule

Volitelné. A [ `Skip` klauzule](../../../../visual-basic/language-reference/queries/skip-clause.md) vynechá zadaný počet prvků v kolekci a vrátí zbývající prvky. Příklad:

[!code-vb[VbVbalrIntroToLINQ#18](codesnippet/VisualBasic/introduction-to-linq_19.vb)]

### <a name="skip-while-clause"></a>Skip While – klauzule

Volitelné. A [ `Skip While` klauzule](../../../../visual-basic/language-reference/queries/skip-while-clause.md) vynechává prvky v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vrací zbývající prvky. Příklad:

[!code-vb[VbVbalrIntroToLINQ#19](codesnippet/VisualBasic/introduction-to-linq_20.vb)]

### <a name="take-clause"></a>Take – klauzule

Volitelné. A [ `Take` klauzule](../../../../visual-basic/language-reference/queries/take-clause.md) vrátí zadaný počet souvislých prvků od začátku kolekce. Příklad:

[!code-vb[VbVbalrIntroToLINQ#20](codesnippet/VisualBasic/introduction-to-linq_21.vb)]

### <a name="take-while-clause"></a>Take While – klauzule

Volitelné. A [ `Take While` klauzule](../../../../visual-basic/language-reference/queries/take-while-clause.md) obsahuje prvky v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vynechány zbývající prvky. Příklad:

[!code-vb[VbVbalrIntroToLINQ#21](codesnippet/VisualBasic/introduction-to-linq_22.vb)]
  
## <a name="use-additional-linq-query-features"></a>Používat další funkce dotazu LINQ  
  
Můžete použít další funkce dotazu LINQ voláním členů vyčíslitelného a dotazovatelného typu, které poskytuje LINQ. Tyto další funkce můžete použít voláním operátora pro konkrétní dotaz na výsledek výrazu dotazu. Například v následujícím příkladu <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> metoda ke kombinaci výsledků dvou dotazů do výsledku jednoho dotazu. Používá <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> metodu pro vrácení výsledků dotazu v podobě obecného seznamu.
  
 [!code-vb[VbVbalrIntroToLINQ#22](codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Podrobnosti o dalších možnostech LINQ naleznete v tématu [přehled standardních operátorů dotazu](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Připojení k databázi pomocí LINQ to SQL  
 V jazyce Visual Basic identifikujete databázové objekty systému SQL Server, jako například tabulky, zobrazení a uložených procedur, které chcete získat přístup pomocí LINQ to SQL souboru. Souboru LINQ to SQL má příponou dbml.  
  
 Pokud máte platné připojení k databázi serveru SQL Server, můžete přidat **třídy LINQ to SQL** šablonu položky projektu. Zobrazí se Návrhář relací objektů (O/R designer). O/R Designer umožňuje přetažení položek, které chcete získat přístup v kódu z **Průzkumníka serveru**/**Průzkumník databáze** na návrhové ploše. Přidá souboru LINQ to SQL <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje vlastnosti a kolekce pro tabulky a zobrazení, které mají přístup k a metody pro uložené procedury, které chcete volat. Po uložení změn do technologie LINQ to SQL (dbml) soubor je můžete přístup k těmto objektům ve vašem kódu odkazem <xref:System.Data.Linq.DataContext> objekt, který je definován pomocí Návrháře relací objektů. <xref:System.Data.Linq.DataContext> Objektu pro váš projekt je s názvem podle názvu vašeho souboru LINQ to SQL. Například technologie LINQ to SQL soubor s názvem Northwind.dbml vytvoří <xref:System.Data.Linq.DataContext> objekt s názvem `NorthwindDataContext`.  
  
 Příklady s podrobnými pokyny najdete v tématu [jak: Dotaz na databázi](how-to-query-a-database-by-using-linq.md) a [jak: Volání uložené procedury](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Funkce jazyka Visual Basic podporující LINQ  
 Visual Basic obsahuje další důležité funkcí, které zjednodušení použití LINQ a snižuje množství kódu, který musíte napsat k provádění dotazů LINQ. Patří mezi ně například:  
  
-   **Anonymní typy**, které umožňují vytvoření nového typu na základě výsledku dotazu.  
  
-   **Implicitně typované proměnné**, které umožňují odložit určení typu a umožňují kompilátoru odvození typu na základě výsledku dotazu.  
  
-   **Rozšiřující metody**, které umožňují rozšířit existující typ vašimi vlastními metodami beze změny samotného typu.  
  
 Podrobnosti najdete v tématu [jazyka Visual Basic funkce, že podpora LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Odložené a okamžité spuštění dotazu

 Provedení dotazu se liší od vytvoření dotazu. Po vytvoření dotazu je jeho spuštění vyvoláno samostatným mechanismem. Dotaz může proveden, jakmile je definován (*okamžité spuštění*), nebo může být definice uložena a dotaz může být proveden později (*odložené provedení*).  
  
 Ve výchozím nastavení při vytváření dotazu samotný dotaz nespustí ihned. Místo toho je definice dotazu uložena v proměnné, která se použije k odkazování výsledku dotazu. Když přístup výsledku proměnné později v kódu, například v `For…Next` smyčky, dotaz je proveden. Tento proces se označuje jako *odložené provedení*.  
  
 Dotazy mohou být provedeny také když jsou definovány, které se označuje jako *okamžité spuštění*. Okamžité spuštění můžete aktivovat použitím metodu, která vyžaduje přístup k jednotlivým elementům výsledku dotazu. To může být výsledek vložení agregační funkce, jako například `Count`, `Sum`, `Average`, `Min`, nebo `Max`. Další informace o agregačních funkcích najdete v tématu [Aggregate – klauzule](../../../language-reference/queries/aggregate-clause.md).  
  
 Použití `ToList` nebo `ToArray` metody bude také vynuceno okamžité spuštění. To může být užitečné, pokud chcete okamžitě spustit dotaz a uložit výsledky do mezipaměti. Další informace o těchto metodách v tématu [převádění datových typů](../../concepts/linq/converting-data-types.md).  
  
 Další informace o provádění dotazů, najdete v části [zápis svůj první dotaz LINQ](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML v jazyce Visual Basic  
 Funkce XML v jazyce Visual Basic zahrnují literály XML a vlastnosti OS XML, které umožňují snadno vytvořit, získat přístup, dotazování a modifikaci XML ve vašem kódu. Literály XML umožňují zapisovat XML přímo v kódu. Kompilátor jazyka Visual Basic používá XML jako datový objekt první třídy.  
  
 Následující příklad kódu ukazuje, jak vytvořit prvek XML, přístup k jeho dílčím prvkům a atributům a dotazu na obsah prvku s využitím jazyka LINQ.  
  
 [!code-vb[VbXmlSamples#8](../../../language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Další informace najdete v tématu [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Související prostředky  
  
|Téma|Popis|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Popisuje funkce XML v jazyce Visual Basic, která mohou být dotazovány a které umožňují zahrnout XML jako datové objekty první třídy v kódu jazyka Visual Basic.|  
|[Dotazy](../../../language-reference/queries/index.md)|Poskytuje referenční informace o klauzulích dotazu, které jsou k dispozici v jazyce Visual Basic.|  
|[LINQ (Language-Integrated Query)](../../concepts/linq/index.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro funkci LINQ.|  
|[LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro funkci LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro funkci LINQ na objekty.|  
|[LINQ to ADO.NET (stránka portálu)](../../concepts/linq/linq-to-adonet-portal-page.md)|Obsahuje odkazy na obecné informace, pokyny pro programování a ukázky pro funkci LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro funkci LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Postupy a návody
 [Postupy: Dotaz na databázi](how-to-query-a-database-by-using-linq.md)  
  
 [Postupy: Volání uložené procedury](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Postupy: Změna dat v databázi](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Postupy: Kombinace dat s LINQ pomocí spojení](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Postupy: Řazení výsledků dotazu](how-to-sort-query-results-by-using-linq.md)  
  
 [Postupy: Filtrování výsledků dotazu](how-to-filter-query-results-by-using-linq.md)  
  
 [Postupy: Počet, SUMA nebo průměr dat](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Postupy: Hledání minimální nebo maximální hodnoty ve výsledku dotazu](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Kapitola 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) v [programovacího jazyka Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Viz také:

- [LINQ (Language-Integrated Query)](../../concepts/linq/index.md)
- [Přehled technologie LINQ to XML v jazyce Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [Přehled LINQ to DataSet](~/docs/framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
