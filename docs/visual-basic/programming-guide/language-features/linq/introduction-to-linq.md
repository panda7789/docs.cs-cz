---
title: Úvod do LINQ
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
ms.openlocfilehash: 610f2a1020cc15f855b3ddfc0917e14aae34fb82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344940"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Představení technologie LINQ v jazyce Visual Basic
LINQ (Language-Integrated Query) přidává funkce pro dotazy do Visual Basic a poskytuje jednoduché a výkonné funkce, když pracujete se všemi druhy dat. Místo odeslání dotazu do databáze, která se má zpracovat, nebo práce s jinou syntaxí dotazu pro každý typ vyhledávaných dat, LINQ zavádí dotazy jako součást Visual Basicho jazyka. Používá sjednocenou syntaxi bez ohledu na typ dat.  
  
 LINQ umožňuje dotazovat se na data z databáze SQL Server, XML, polí v paměti a kolekcí, datových sad ADO.NET nebo jakýchkoli jiných vzdálených nebo místních zdrojů dat, které podporují technologii LINQ. To lze provést pomocí běžných Visual Basic prvků jazyka. Vzhledem k tomu, že vaše dotazy jsou napsány v jazyce Visual Basic, jsou výsledky dotazu vráceny jako objekty silného typu. Tyto objekty podporují technologii IntelliSense, která umožňuje psát kód rychleji a zachytit chyby v dotazech v době kompilace místo v době běhu. Dotazy LINQ lze použít jako zdroj dalších dotazů pro upřesnění výsledků. Mohou být také vázány na ovládací prvky, aby uživatelé mohli snadno zobrazit a upravit výsledky dotazu.  
  
 Například následující příklad kódu ukazuje dotaz LINQ, který vrátí seznam zákazníků z kolekce a seskupí je na základě jejich umístění.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>Spuštění příkladů  
 Chcete-li spustit příklady v úvodu a ve [struktuře oddílu dotazu LINQ](#structure-of-a-linq-query) , zahrňte následující kód, který vrátí seznam zákazníků a objednávek.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>Zprostředkovatelé LINQ  
 *Zprostředkovatel LINQ* mapuje vaše Visual Basic dotazy LINQ na zdroj dat, se kterým se dotazuje. Když napíšete dotaz LINQ, zprostředkovatel převezme dotaz a převede ho na příkazy, které bude zdroj dat moci spustit. Zprostředkovatel také převede data ze zdroje na objekty, které tvoří výsledek dotazu. Nakonec převede objekty na data při odeslání aktualizací do zdroje dat.  
  
 Visual Basic obsahuje následující poskytovatele LINQ.  
  
|Zprostředkovatel|Popis|  
|---|---|  
|LINQ na objekty|Poskytovatel LINQ to Objects umožňuje zadat dotaz na kolekce a pole v paměti. Pokud objekt podporuje rozhraní <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>, poskytovatel LINQ to Objects vám umožní dotazovat se na něj.<br /><br /> Poskytovatele LINQ to Objects můžete povolit importováním oboru názvů <xref:System.Linq>, který je importován ve výchozím nastavení pro všechny Visual Basic projekty.<br /><br /> Další informace o poskytovateli LINQ to Objects najdete v tématu [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|Technologie LINQ to SQL|Poskytovatel LINQ to SQL umožňuje zadávat dotazy a upravovat data v databázi SQL Server. To usnadňuje mapování objektového modelu pro aplikaci na tabulky a objekty v databázi.<br /><br /> Visual Basic usnadňuje práci s LINQ to SQL včetně Návrhář relací objektů (O/R Designer). Tento Návrhář slouží k vytvoření objektového modelu v aplikaci, která je mapována na objekty v databázi. Návrhář O/R také poskytuje funkce pro mapování uložených procedur a funkcí na objekt <xref:System.Data.Linq.DataContext>, který spravuje komunikaci s databází a ukládá stav pro optimistické kontroly souběžnosti.<br /><br /> Další informace o poskytovateli LINQ to SQL najdete v tématu [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Další informace o Návrhář relací objektů naleznete v tématu [LINQ to SQL Tools v aplikaci Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|Technologie LINQ to XML|Poskytovatel LINQ to XML umožňuje zadávat dotazy a upravovat XML. Můžete upravit XML v paměti nebo můžete načíst XML z a uložit XML do souboru.<br /><br /> Kromě toho poskytovatel LINQ to XML povoluje literály XML a vlastnosti OS XML, které umožňují psát XML přímo v kódu Visual Basic. Další informace najdete v tématu [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|Poskytovatel LINQ to DataSet umožňuje dotazování a aktualizaci dat v datové sadě ADO.NET. Můžete přidat sílu technologie LINQ do aplikací, které používají datové sady, aby bylo možné zjednodušit a roztáhnout funkce pro dotazování, agregaci a aktualizaci dat v datové sadě.<br /><br /> Další informace najdete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Struktura dotazu LINQ  
 Dotaz LINQ, který se často označuje jako *výraz dotazu*, se skládá z kombinace klauzulí dotazu, které identifikují zdroje dat a proměnné iterace pro dotaz. Výraz dotazu může také obsahovat pokyny pro řazení, filtrování, seskupování a spojování nebo výpočty, které se mají použít na zdrojová data. Syntaxe výrazu dotazu se podobá syntaxi SQL; Proto se může stát, že se seznámíte se syntaxí.  
  
 Výraz dotazu začíná klauzulí `From`. Tato klauzule identifikuje zdrojová data pro dotaz a proměnné, které se používají k odkazování na jednotlivé prvky zdrojových dat. Tyto proměnné jsou pojmenované *proměnné rozsahu* nebo *proměnné iterace*. Klauzule `From` je vyžadována pro dotaz s výjimkou dotazů `Aggregate`, kde klauzule `From` je volitelná. Po určení rozsahu a zdroje dotazu v klauzulích `From` nebo `Aggregate` můžete použít libovolnou kombinaci klauzulí dotazu pro upřesnění dotazu. Podrobnosti o klauzulích dotazu naleznete v tématu Visual Basic operátory dotazů LINQ dále v tomto tématu. Následující dotaz například identifikuje zdrojovou kolekci zákaznických dat jako proměnnou `customers` a proměnnou iterace s názvem `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 Tento příklad je platný dotaz sám o sobě; Dotaz však bude mnohem výkonnější, pokud přidáte další klauzule dotazu pro upřesnění výsledku. Například můžete přidat klauzuli `Where` pro filtrování výsledku podle jedné nebo více hodnot. Výrazy dotazů jsou jedním řádkem kódu; na konec dotazu můžete jednoduše připojit další klauzule dotazu. Dotaz můžete rozdělit na více řádků textu, aby se zlepšila čitelnost pomocí znaku podtržítka (\_) pro pokračování řádku. Následující příklad kódu ukazuje příklad dotazu, který obsahuje klauzuli `Where`.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 Další výkonnou klauzulí dotazu je klauzule `Select`, která umožňuje vracet pouze vybraná pole ze zdroje dat. Dotazy LINQ vracejí vyčíslitelné kolekce objektů silně typovaného typu. Dotaz může vrátit kolekci anonymních typů nebo pojmenovaných typů. Klauzuli `Select` lze použít pro vrácení pouze jednoho pole ze zdroje dat. Pokud to provedete, typ vrácené kolekce je typ tohoto jediného pole. Klauzuli `Select` lze použít také k vrácení více polí ze zdroje dat. Pokud to provedete, typ vrácené kolekce je nový anonymní typ. Můžete také porovnat pole vrácená dotazem s poli zadaného pojmenovaného typu. Následující příklad kódu ukazuje výraz dotazu, který vrací kolekci anonymních typů, které mají členy vyplněné daty z vybraných polí ze zdroje dat.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 Dotazy LINQ lze také použít ke kombinování více zdrojů dat a vrácení jediného výsledku. To lze provést pomocí jedné nebo více `From` klauzulí nebo pomocí klauzulí `Join` nebo `Group Join` dotazu. Následující příklad kódu ukazuje výraz dotazu, který kombinuje data o zákaznících a objednávkách a vrátí kolekci anonymních typů obsahujících data zákazníka a objednávky.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 Pomocí klauzule `Group Join` lze vytvořit hierarchický výsledek dotazu, který obsahuje kolekci zákaznických objektů. Každý objekt zákazníka má vlastnost, která obsahuje kolekci všech objednávek pro daného zákazníka. Následující příklad kódu ukazuje výraz dotazu, který kombinuje data o zákaznících a objednávkách jako hierarchický výsledek a vrátí kolekci anonymních typů. Dotaz vrátí typ, který obsahuje vlastnost `CustomerOrders`, která obsahuje kolekci dat objednávky pro zákazníka. Obsahuje také vlastnost `OrderTotal`, která obsahuje součet součtů pro všechny objednávky daného zákazníka. (Tento dotaz je ekvivalentem levého VNĚJŠÍho spojení.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 Existuje několik dalších operátorů dotazů LINQ, pomocí kterých můžete vytvářet výkonné výrazy dotazů. Další část tohoto tématu popisuje různé klauzule dotazu, které můžete zahrnout do výrazu dotazu. Podrobnosti o Visual Basic klauzulích dotazů najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic operátory dotazů LINQ  

Třídy v oboru názvů <xref:System.Linq> a jiné obory názvů, které podporují dotazy LINQ, obsahují metody, které lze volat pro vytváření a zpřesnění dotazů na základě potřeb vaší aplikace. Visual Basic obsahuje klíčová slova pro následující klauzule běžných dotazů. Podrobnosti o Visual Basic klauzulích dotazů najdete v tématu [dotazy](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Klauzule From

Pro zahájení dotazu je vyžadována buď [klauzule`From`](../../../../visual-basic/language-reference/queries/from-clause.md) , nebo klauzule `Aggregate`. Klauzule `From` Určuje zdrojovou kolekci a proměnnou iterace pro dotaz. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select – klauzule

Volitelná. [Klauzule`Select`](../../../../visual-basic/language-reference/queries/select-clause.md) deklaruje sadu proměnných iterace pro dotaz. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

Pokud není zadána klauzule `Select`, proměnné iterace pro dotaz se skládají z proměnných iterace určených klauzulí `From` nebo `Aggregate`.

### <a name="where-clause"></a>Klauzule Where

Volitelná. [Klauzule`Where`](../../../../visual-basic/language-reference/queries/where-clause.md) Určuje podmínku filtrování pro dotaz. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>ORDER by – klauzule]

| Volitelné. [Klauzule`Order By`](../../../../visual-basic/language-reference/queries/order-by-clause.md) určuje pořadí řazení pro sloupce v dotazu. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join – klauzule

Volitelná. [Klauzule`Join`](../../../../visual-basic/language-reference/queries/join-clause.md) kombinuje dvě kolekce do jedné kolekce. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By – klauzule

Volitelná. [Klauzule`Group By`](../../../../visual-basic/language-reference/queries/group-by-clause.md) seskupí prvky výsledku dotazu. Dá se použít k aplikování agregačních funkcí na každou skupinu. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join – klauzule

Volitelná. [Klauzule`Group Join`](../../../../visual-basic/language-reference/queries/group-join-clause.md) kombinuje dvě kolekce do jedné hierarchické kolekce. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate – klauzule

Pro zahájení dotazu je vyžadována buď [klauzule`Aggregate`](../../../../visual-basic/language-reference/queries/aggregate-clause.md) , nebo klauzule `From`. Klauzule `Aggregate` aplikuje jednu nebo více agregačních funkcí na kolekci. Například můžete použít klauzuli `Aggregate` pro výpočet součtu všech prvků vrácených dotazem, jak je uvedeno v následujícím příkladu.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

Můžete také použít klauzuli `Aggregate` pro úpravu dotazu. Například můžete použít klauzuli `Aggregate` k provedení výpočtu v související kolekci dotazů. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let – klauzule

Volitelná. [Klauzule`Let`](../../../../visual-basic/language-reference/queries/let-clause.md) vypočítá hodnotu a přiřadí ji k nové proměnné v dotazu. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct – klauzule

Volitelná. Klauzule `Distinct` omezuje hodnoty aktuální proměnné iterace tak, aby se vyloučily duplicitní hodnoty ve výsledcích dotazu. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip – klauzule

Volitelná. [Klauzule`Skip`](../../../../visual-basic/language-reference/queries/skip-clause.md) obchází zadaný počet prvků v kolekci a vrátí zbývající prvky. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>Skip While – klauzule

Volitelná. [Klauzule`Skip While`](../../../../visual-basic/language-reference/queries/skip-while-clause.md) obchází prvky v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající prvky. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take – klauzule

Volitelná. [Klauzule`Take`](../../../../visual-basic/language-reference/queries/take-clause.md) vrací zadaný počet souvislých prvků od začátku kolekce. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While – klauzule

Volitelná. [Klauzule`Take While`](../../../../visual-basic/language-reference/queries/take-while-clause.md) obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající prvky. Příklad:

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Použití dalších funkcí dotazů LINQ  
  
Můžete použít další funkce dotazů LINQ voláním členů výčtových a Queryable typů poskytovaných LINQ. Tyto další funkce můžete použít voláním konkrétního operátoru dotazu na výsledek výrazu dotazu. Například následující příklad používá metodu <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> pro kombinování výsledků dvou dotazů do jednoho výsledku dotazu. Pomocí metody <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> vrátí výsledek dotazu jako obecný seznam.
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 Podrobnosti o dalších možnostech LINQ najdete v tématu [Přehled standardních operátorů dotazů](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Připojení k databázi pomocí LINQ to SQL  
 V Visual Basic identifikujete SQL Server databázových objektů, jako jsou tabulky, zobrazení a uložené procedury, ke kterým chcete získat přístup pomocí souboru LINQ to SQL. Soubor LINQ to SQL má příponu. dbml.  
  
 Pokud máte platné připojení k databázi SQL Server, můžete do projektu přidat šablonu položky **LINQ to SQL třídy** . Tím se zobrazí Návrhář relací objektů (Návrhář O/R). Návrhář O/R umožňuje přetahovat položky, ke kterým chcete přistupovat, z **Průzkumník serveru**/**Průzkumník databáze** na plochu návrháře. Soubor LINQ to SQL přidá do projektu objekt <xref:System.Data.Linq.DataContext>. Tento objekt obsahuje vlastnosti a kolekce pro tabulky a zobrazení, ke kterým chcete získat přístup, a metody pro uložené procedury, které chcete volat. Po uložení změn do souboru LINQ to SQL (. dbml) máte přístup k těmto objektům v kódu odkazem na objekt <xref:System.Data.Linq.DataContext>, který je definován v Návrháři relací. Objekt <xref:System.Data.Linq.DataContext> pro projekt je pojmenován na základě názvu vašeho LINQ to SQL souboru. Například LINQ to SQL soubor s názvem Northwind. dbml vytvoří objekt <xref:System.Data.Linq.DataContext> s názvem `NorthwindDataContext`.  
  
 Příklady s podrobnými pokyny najdete v tématech [Postup: dotazování databáze](how-to-query-a-database-by-using-linq.md) a [Postupy: volání uložené procedury](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic funkce podporující technologii LINQ  
 Visual Basic zahrnuje další důležité funkce, které zjednodušují použití LINQ a snižují množství kódu, který musíte napsat k provádění dotazů LINQ. Patří mezi ně například:  
  
- **Anonymní typy**, které umožňují vytvořit nový typ založený na výsledku dotazu.  
  
- **Implicitně typované proměnné**, které umožňují odložit určení typu a nechat kompilátor odvodit typ na základě výsledku dotazu.  
  
- **Metody rozšíření**, které umožňují rozšířit existující typ vlastními metodami, aniž by bylo potřeba měnit samotný typ.  
  
 Podrobnosti najdete v tématu [Visual Basic funkce, které podporují technologii LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Odložené a okamžité provedení dotazu

 Provádění dotazů je oddělené od vytvoření dotazu. Po vytvoření dotazu se jeho spuštění aktivuje pomocí samostatného mechanismu. Dotaz může být proveden hned po definování (*okamžité provedení*), nebo může být definice uložena a dotaz může být proveden později (*odložené spuštění*).  
  
 Ve výchozím nastavení se při vytváření dotazu samotný dotaz nespustí okamžitě. Místo toho je definice dotazu uložena v proměnné, která se používá k odkazování na výsledek dotazu. Pokud je výsledkem proměnné výsledků dotazu později v kódu, například ve smyčce `For…Next`, je dotaz proveden. Tento proces se označuje jako *odložené provádění*.  
  
 Dotazy mohou být provedeny také při jejich definování, což se označuje jako *okamžité provedení*. Okamžité spuštění můžete aktivovat aplikováním metody, která vyžaduje přístup k jednotlivým prvkům výsledku dotazu. Může to být výsledek zahrnutí agregační funkce, například `Count`, `Sum`, `Average`, `Min`nebo `Max`. Další informace o agregačních funkcích naleznete v tématu [klauzule Aggregate](../../../language-reference/queries/aggregate-clause.md).  
  
 Použití metod `ToList` nebo `ToArray` také vynutí okamžité provedení. To může být užitečné, když chcete spustit dotaz okamžitě a uložit výsledky do mezipaměti. Další informace o těchto metodách naleznete v tématu [Převod datových typů](../../concepts/linq/converting-data-types.md).  
  
 Další informace o provádění dotazů naleznete v tématu [zápis prvního dotazu LINQ](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML v jazyce Visual Basic  
 Funkce XML v Visual Basic zahrnují literály XML a vlastnosti osy XML, které umožňují snadno vytvářet, přistupovat, dotazovat a upravovat XML ve vašem kódu. Literály XML umožňují psát XML přímo v kódu. Kompilátor Visual Basic považuje XML za datový objekt první třídy.  
  
 Následující příklad kódu ukazuje, jak vytvořit element XML, získat přístup k jeho dílčím elementům a atributům a zadat dotaz na obsah elementu pomocí LINQ.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Další informace najdete v tématu [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Související prostředky  
  
|Téma|Popis|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Popisuje funkce XML v Visual Basic, které lze dotazovat a které umožňují zahrnout XML jako datové objekty první třídy v kódu Visual Basic.|  
|[Dotazy](../../../language-reference/queries/index.md)|Poskytuje referenční informace o klauzulích dotazu, které jsou k dispozici v Visual Basic.|  
|[LINQ (jazykově integrovaný dotaz)](../../concepts/linq/index.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro LINQ.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro LINQ to Objects.|  
|[LINQ to ADO.NET (stránka portálu)](../../concepts/linq/linq-to-adonet-portal-page.md)|Obsahuje odkazy na Obecné informace, pokyny pro programování a ukázky pro LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Obsahuje obecné informace, pokyny pro programování a ukázky pro LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Témata postupy a návody
 [Postupy: dotazování databáze](how-to-query-a-database-by-using-linq.md)  
  
 [Postupy: volání uložené procedury](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Postupy: Změna dat v databázi](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Postupy: kombinování dat pomocí spojení](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Postupy: řazení výsledků dotazu](how-to-sort-query-results-by-using-linq.md)  
  
 [Postupy: filtrování výsledků dotazu](how-to-filter-query-results-by-using-linq.md)  
  
 [Postupy: počítání, suma nebo průměr dat](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Postupy: hledání minimální nebo maximální hodnoty ve výsledku dotazu](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Kapitola 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) v [programování Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Viz také:

- [LINQ (jazykově integrovaný dotaz)](../../concepts/linq/index.md)
- [Přehled LINQ to XML v Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [Přehled LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
