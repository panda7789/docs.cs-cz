---
title: "Představení technologie LINQ v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7882614b9663d1c38f137f7a69054d5bbd50b19
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="introduction-to-linq-in-visual-basic"></a>Představení technologie LINQ v jazyce Visual Basic
Language-Integrated Query (LINQ) přidá funkce dotazu pro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] a poskytuje jednoduché a výkonné možnosti při práci s nejrůznějších druhy data. Místo odesílání dotazu na databázi zpracovat nebo práci s syntaxe různých dotazu pro každý typ dat, které hledáte, představuje LINQ dotazů v rámci [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jazyk. Použije jednotná syntaxe bez ohledu na typ dat:  
  
 LINQ vám umožní zadat dotaz na data z databáze serveru SQL, XML, pole v paměti a kolekcí, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové sady, nebo jiná vzdáleného nebo místního data zdroj tohoto podporuje LINQ. Můžete k tomu všechny s běžné [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jazykové elementy. Protože jsou v dotazech [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jazyka, výsledky dotazu jsou vrácena jako objektů se silným typem. Tyto objekty podporují technologii IntelliSense, které umožňují rychlejší psaní kódu a zpracovávat chyby v dotazech v době kompilace místo v době běhu. Dotazy LINQ slouží jako zdroj další dotazy k zpřesnění výsledků. Mohou také být vázány na ovládací prvky, aby uživatelé mohou snadno zobrazit nebo upravit výsledky dotazu.  
  
 Například následující příklad kódu ukazuje dotaz LINQ, který vrátí seznam zákazníků z kolekce a skupiny, které je založené na jejich umístění.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 V tomto tématu najdete informace o těchto oblastech:  
  
-   [Spuštění příkladů](#RunningtheExamples)  
  
-   [Zprostředkovatelé LINQ](#LINQProviders)  
  
-   [Struktura dotazu LINQ](#StructureOfALINQQuery)  
  
-   [Operátory dotazů LINQ jazyka Visual Basic](#VisualBasicLINQQueryOperators)  
  
-   [Připojení k databázi pomocí technologie LINQ to SQL](#ConnectingToADatabase)  
  
-   [Funkce Visual Basic podporující LINQ](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [Při provádění dotazu odložené a okamžitě](#QueryExecution)  
  
-   [XML v jazyce Visual Basic](#XMLInVisualBasic)  
  
-   [Související informační zdroje](#RelatedResources)  
  
-   [Postupy a návody](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a>Spuštění příkladů  
 Pokud chcete spustit v příkladech v úvodu a v části "Struktura z dotaz LINQ", zahrnují následující kód, který vrátí seznam Zákazníci a objednávky.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a>Zprostředkovatelé LINQ  
 A *LINQ zprostředkovatele* mapuje vaší [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dotazů LINQ ke zdroji dat, která je dotazována. Při psaní dotazu LINQ zprostředkovatel získá takový dotaz a překládá do příkazy, které zdroje dat bude možné spustit. Zprostředkovatel také převádí data ze zdroje na objekty, které tvoří výsledek dotazu. Nakonec převede objekty k datům při odesílání aktualizací na zdroj dat.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]obsahuje tyto zprostředkovatele LINQ.  
  
|Zprostředkovatel|Popis|  
|---|---|  
|LINQ na objekty|LINQ na objekty zprostředkovatele umožňuje dotaz na kolekce v paměti a pole. Pokud objekt podporuje buď <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> rozhraní LINQ na objekty zprostředkovatele umožňuje dotazování ho.<br /><br /> LINQ na objekty zprostředkovatele můžete povolit importováním <xref:System.Linq> obor názvů, který je importován ve výchozím nastavení pro všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekty.<br /><br /> Další informace o LINQ na objekty poskytovatele najdete v tématu [LINQ na objekty](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).|  
|Technologie LINQ to SQL|Technologie LINQ to SQL zprostředkovatele umožňuje dotazování a upravovat data v databázi systému SQL Server. To usnadňuje mapování objektový model pro aplikace s tabulkami a objekty v databázi.<br /><br /> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]usnadňuje práci s technologie LINQ to SQL zahrnutím Návrhář relací objektů (Návrhář relací objektů). Tento návrhář slouží k vytvoření objektu modelu v aplikaci, která se mapuje na objekty v databázi. Návrhář relací objektů také poskytuje funkce pro mapování uložené procedury a funkce na <xref:System.Data.Linq.DataContext> objekt, který spravuje komunikaci s databází a ukládá stav pro optimistickou metodu souběžného kontroly.<br /><br /> Další informace o dotazech LINQ to SQL poskytovatele najdete v tématu [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md). Další informace o Návrhář relací objektů najdete v tématu [technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|Technologie LINQ to XML|Technologie LINQ to XML zprostředkovatele umožňuje dotazování a upravit XML. Můžete upravit v paměti XML nebo XML můžete načíst z a uložit XML do souboru.<br /><br /> Kromě toho umožňuje LINQ to XML zprostředkovatele literály XML a vlastnosti osy XML, které vám umožní zapisovat přímo v kódu XML vaší [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu. Další informace najdete v tématu [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ na DataSet|LINQ na DataSet zprostředkovatele umožňuje dotazování a aktualizace dat v [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datovou sadu. Výkon LINQ můžete přidat do aplikace, které používají datové sady, aby bylo možné zjednodušit a získali další možnosti pro dotazování, agregace a aktualizace dat v datovou sadu.<br /><br /> Další informace najdete v tématu [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
##  <a name="StructureOfALINQQuery"></a>Struktura dotazu LINQ  
 Dotaz LINQ, často označuje jako *dotaz výrazu*, se skládá z kombinace klauzule dotazu, které identifikují datové zdroje a iterační proměnné pro dotaz. Výraz dotazu může zahrnovat taky pokyny pro řazení, filtrování, seskupování a připojení nebo výpočty použít ke zdrojovým datům. Syntaxe výrazu dotazu syntaxe SQL, vypadá takto: Proto můžete zjistit většinu syntaxe seznámit.  
  
 Výraz dotazu začíná `From` klauzule. Tuto klauzuli identifikuje zdroj dat pro dotaz a proměnné, které se používají k odkazování na každý prvek zdrojová data jednotlivě. Tyto proměnné jsou pojmenované *rozsahu proměnné* nebo *iterační proměnné*. `From` Je vyžadována klauzule pro daný dotaz, s výjimkou `Aggregate` dotazy, kde `From` klauzule je volitelný. Po oboru a zdroj dotazu se budou identifikovat `From` nebo `Aggregate` klauzule, může obsahovat libovolnou kombinaci klauzule dotazu pro upřesnění dotazu. Podrobnosti o klauzule dotazu najdete v tématu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] operátory dotazu LINQ později v tomto tématu. Například následující dotaz identifikuje kolekci zdroje dat zákazníka, jako `customers` proměnné a proměnná iterace s názvem `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 Tato ukázka je platný dotaz samostatně; dotaz je však mnohem silnější při přidání další klauzule dotazu upřesněte výsledek. Například můžete přidat `Where` klauzule filtrovat výsledek podle jednoho nebo více hodnot. Výrazy dotazů jsou jediný řádek kódu; klauzule další dotaz můžete připojit pouze na konec dotazu. Dotaz můžete rozdělit mezi několik řádků textu ke zlepšení čitelnosti pomocí podtržítko (\_) znak pokračování řádku. Následující příklad kódu ukazuje příklad dotazu, který zahrnuje `Where` klauzule.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Je jinou klauzuli účinný dotazovací `Select` klauzuli, která umožní vám vrátit pouze vybrané pole ze zdroje dat. Dotazy LINQ vrátí vyčíslitelná kolekce objektů se silným typem. Dotaz může vracet kolekci anonymní nebo pojmenované typy. Můžete použít `Select` klauzule, která vrátí ze zdroje dat pouze jedno pole. Když to uděláte, je typ kolekce vrátil typ tohoto jediné pole. Můžete také `Select` klauzule vrátit více polí ze zdroje dat. Když to uděláte, typ kolekce vrátil je nový typ anonymní. Také můžete přiřadit pole vrácené dotazem na pole s názvem zadaného typu. Následující příklad kódu ukazuje výraz dotazu, který vrátí kolekce anonymní typy, které mají členů naplněný daty z vybrané pole ze zdroje dat.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 Dotazy LINQ mohou sloužit také kombinovat více zdrojů dat a vrátí jeden výsledek. To lze provést s jedním nebo více `From` klauzule, nebo pomocí `Join` nebo `Group Join` dotaz klauzule. Následující příklad kódu ukazuje výraz dotazu, který kombinuje data zákazníků a pořadí a vrátí kolekci anonymní typy obsahující zákazníka a pořadí data.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Můžete použít `Group Join` klauzule vytvoření výsledku hierarchické dotazu, který obsahuje kolekci objektů zákazníka. Každý objekt zákazník má vlastnost, která obsahuje kolekci všech objednávek tohoto zákazníka. Následující příklad kódu ukazuje výraz dotazu, který kombinuje zákazníka a pořadí dat v důsledku toho hierarchické a vrátí kolekci anonymní typy. Dotaz vrátí typ, který zahrnuje `CustomerOrders` vlastnost, která obsahuje kolekci dat pořadí pro zákazníka. Zahrnuje také `OrderTotal` vlastnost, která obsahuje součet součty pro všechny objednávky tohoto zákazníka. (Tento dotaz je ekvivalentní LEFT OUTER JOIN.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Existuje několik dalších LINQ operátory dotazů, které můžete použít k vytvoření účinný dotazovací výrazy. V další části tohoto tématu popisuje různé klauzule dotazu, které lze zahrnout ve výrazu dotazu. Podrobnosti o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dotaz klauzule najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/queries.md).  
  
##  <a name="VisualBasicLINQQueryOperators"></a>Operátory dotazů LINQ jazyka Visual Basic  
 Třídy v <xref:System.Linq> obor názvů a další obory názvů, které podporují dotazů LINQ obsahují metody, které můžete volat k vytvoření a upřesněte dotazy na základě potřeb vaší aplikace. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]klíčová slova pro nejběžnější klauzule dotazu obsahuje, jak je popsáno v následující tabulce.  
  
|Termín|Definice|  
|---|---|  
|[From – klauzule](../../../../visual-basic/language-reference/queries/from-clause.md)|Buď `From` klauzule nebo `Aggregate` klauzule je potřebných ke spuštění dotazu. A `From` klauzuli určuje kolekci zdroje a proměnná iterace pro dotaz. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[Select – klauzule](../../../../visual-basic/language-reference/queries/select-clause.md)|Volitelné. Deklaruje sadu iterační proměnné pro dotaz. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> Pokud `Select` není zadána klauzule, iterační proměnné pro dotaz obsahovat iterační proměnné určeného `From` nebo `Aggregate` klauzule.|  
|[Kde – klauzule](../../../../visual-basic/language-reference/queries/where-clause.md)|Volitelné. Určuje podmínku filtrování pro dotaz. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Order By – klauzule](../../../../visual-basic/language-reference/queries/order-by-clause.md)|Volitelné. Určuje pořadí řazení sloupců v dotazu. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[JOIN – klauzule](../../../../visual-basic/language-reference/queries/join-clause.md)|Volitelné. Kombinuje dvě kolekce do jedné kolekce. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Group By – klauzule](../../../../visual-basic/language-reference/queries/group-by-clause.md)|Volitelné. Skupiny elementy výsledků dotazu. Slouží k použití agregační funkce pro každou skupinu. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Group Join – klauzule](../../../../visual-basic/language-reference/queries/group-join-clause.md)|Volitelné. Kombinuje dvě kolekce do jedné hierarchické kolekce. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[AGGREGATE – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|Buď `From` klauzule nebo `Aggregate` klauzule je potřebných ke spuštění dotazu. `Aggregate` Klauzule použije jeden nebo více agregační funkce na kolekci. Například můžete použít `Aggregate` klauzule vypočítat součet pro všechny elementy vrácených dotazem.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> Můžete také `Aggregate` klauzule upravit dotaz. Například můžete použít `Aggregate` klauzule provedení výpočtu na kolekci související dotazu.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Let – klauzule](../../../../visual-basic/language-reference/queries/let-clause.md)|Volitelné. Vypočítá hodnotu a přiřadí ji k nové proměnné v dotazu. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[DISTINCT – klauzule](../../../../visual-basic/language-reference/queries/distinct-clause.md)|Volitelné. Omezuje hodnoty aktuální proměnné iterace k odstranění duplicitních hodnot ve výsledcích dotazů. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[Skip – klauzule](../../../../visual-basic/language-reference/queries/skip-clause.md)|Volitelné. Obchází zadaný počet elementů v kolekci a pak vrátí zbývající elementy. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[Skip While – klauzule](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|Volitelné. Obchází elementů v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající elementy. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Take – klauzule](../../../../visual-basic/language-reference/queries/take-clause.md)|Volitelné. Vrátí zadaný počet souvislý elementů od začátku kolekce. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Take While – klauzule](../../../../visual-basic/language-reference/queries/take-while-clause.md)|Volitelné. Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající elementy. Příklad:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 Podrobnosti o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dotaz klauzule najdete v tématu [dotazy](../../../../visual-basic/language-reference/queries/queries.md).  
  
 Můžete vytvořit další funkce dotazů LINQ volání členové typů vyčíslitelná a dotazovatelné poskytované LINQ. Můžete tyto další funkce voláním operátor konkrétní dotaz na výsledek výrazu dotazu. Například následující příklad kódu používá <xref:System.Linq.Enumerable.Union%2A> metoda kombinovat výsledky dva dotazy do výsledku jeden dotaz. Použije <xref:System.Linq.Enumerable.ToList%2A> metoda vrátí výsledek dotazu jako obecný seznam.  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Podrobnosti o dalších možnostech LINQ najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
##  <a name="ConnectingToADatabase"></a>Připojení k databázi pomocí technologie LINQ to SQL  
 V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], identifikují objekty, databáze systému SQL Server, jako je například tabulek, zobrazení a uložených procedur, které chcete získat přístup pomocí LINQ to SQL souboru. Technologie LINQ to SQL souboru s příponou dbml.  
  
 Pokud máte platné připojení k databázi systému SQL Server, můžete přidat **třídy LINQ to SQL** šablony položky do projektu. Tato akce zobrazí Návrhář relací objektů (Návrhář relací objektů). Návrhář relací objektů můžete přetáhnout položky, které chcete získat přístup v kódu z **Průzkumníka serveru**/**Průzkumník databáze** na plochu návrháře. Technologie LINQ to SQL souboru přidá <xref:System.Data.Linq.DataContext> objektu do projektu. Tento objekt obsahuje vlastnosti a kolekce pro tabulky a zobrazení, která mají přístup k a metody pro uložené procedury, které chcete volat. Po uložení změn LINQ to SQL (dbml) souboru pod položkou dostanete tyto objekty v kódu <xref:System.Data.Linq.DataContext> objekt, který je definován Návrhář relací objektů. <xref:System.Data.Linq.DataContext> Objekt pro je s názvem projektu na základě názvu vaší LINQ to SQL souboru. Například LINQ to SQL souboru, který je pojmenován Northwind.dbml vytvoří <xref:System.Data.Linq.DataContext> objekt s názvem `NorthwindDataContext`.  
  
 Příklady s podrobné pokyny najdete v tématu [postupy: dotaz databáze](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md) a [postupy: volání uložené procedury](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md).  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a>Funkce Visual Basic podporující LINQ  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]zahrnuje další upozorňují na důležité funkce, které využívají LINQ jednoduché a snížíte počet kód, který musíte napsat provádět dotazy LINQ. Patří mezi ně například:  
  
-   **Anonymní typy**, které umožňují vytvořit nový typ na základě výsledku dotazu.  
  
-   **Implicitně typované proměnné**, které umožňují odložení určení typu a umožňují kompilátor odvození typu na základě výsledku dotazu.  
  
-   **Rozšiřující metody**, které umožňují rozšířit existující typ s vlastní metody beze změny samotného typu.  
  
 Podrobnosti najdete v tématu [jazyka Visual Basic funkce, podporu LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md).  
  
##  <a name="QueryExecution"></a>Při provádění dotazu odložené a okamžitě  
 Při provádění dotazu je oddělené od vytvoření dotazu. Po vytvoření dotazu její provedení se aktivuje samostatné mechanismus. Dotaz mohou být provedeny, jakmile je definována (*okamžité spuštění*), nebo mohou být uloženy definice a dotaz můžete spustit později (*odložené spouštění*).  
  
 Ve výchozím nastavení když vytvoříte dotaz, samotný dotaz není provedena okamžitě. Místo toho definice dotazu je uložené v proměnné, která slouží k odkazování výsledku dotazu. Pokud přístup proměnnou výsledek dotazu později v kódu, například v `For…Next` smyčky, dotaz se spustí. Tento proces se označuje jako *odložené spouštění*.  
  
 Dotazy můžete také spustit, když jsou definovány, které se označuje jako *okamžité spuštění*. Můžete aktivovat okamžité spuštění použitím metodu, která vyžaduje přístup na jednotlivé prvky výsledku dotazu. To může být výsledkem včetně agregační funkci, jako například `Count`, `Sum`, `Average`, `Min`, nebo `Max`. Další informace o agregační funkce najdete v tématu [Aggregate – klauzule](../../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Pomocí `ToList` nebo `ToArray` metody taky vynutí okamžité spuštění. To může být užitečné, pokud chcete provést dotaz okamžitě a výsledky do mezipaměti. Další informace o těchto metodách v tématu [převádění datových typů](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Další informace o provádění dotazů najdete v tématu [zápis vaše první dotaz LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
##  <a name="XMLInVisualBasic"></a>XML v jazyce Visual Basic  
 Soubor XML funkce [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zahrnují literály XML a vlastnosti osy XML, které umožňují snadno vytvářet, přístup, dotaz a upravovat v kódu XML. XML – literály umožňují zapisovat přímo v kódu XML. Visual Basic – kompilátor zpracovává XML jako první třídy datového objektu.  
  
 Následující příklad kódu ukazuje, jak vytvářet elementu XML, přístup k jeho dílčí elementy a atributy a dotazu pomocí LINQ na obsah elementu.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Další informace najdete v tématu [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).  
  
##  <a name="RelatedResources"></a>Související informační zdroje  
  
|Téma|Popis|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|Popisuje funkce XML v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] může být dotazován a které vám umožňují zahrnout XML jako první třídy datových objektů ve vaší [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.|  
|[Dotazy](../../../../visual-basic/language-reference/queries/queries.md)|Poskytuje referenční informace o klauzule dotazu, které jsou k dispozici v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].|  
|[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|Obsahuje obecné informace, pokyny pro programovací a ukázky pro výrazy LINQ.|  
|[Technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)|Obsahuje obecné informace, pokyny pro programovací a ukázky pro technologie LINQ to SQL.|  
|[LINQ na objekty](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|Obsahuje obecné informace, pokyny pro programovací a ukázky pro LINQ na objekty.|  
|[Technologie LINQ to ADO.NET (portál stránky)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|Obsahuje odkazy na obecné informace, pokyny pro programovací a ukázky pro LINQ na [!INCLUDE[vstecado](~/includes/vstecado-md.md)].|  
|[Technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|Obsahuje obecné informace, pokyny pro programovací a ukázky pro technologie LINQ to XML.|  
  
##  <a name="HowToAndWalkthroughTopics"></a>Postupy a návody  
 [Postupy: dotaz databáze](how-to-query-a-database-by-using-linq.md)  
  
 [Postupy: volání uložené procedury](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Postupy: Změna dat v databázi](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Postupy: kombinace dat s LINQ pomocí spojení](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Postupy: řazení výsledků dotazu](how-to-sort-query-results-by-using-linq.md)  
  
 [Postupy: filtrování výsledků dotazu](how-to-filter-query-results-by-using-linq.md)  
  
 [Postupy: počet, SUMA nebo průměr dat](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Postupy: hledání minimální nebo maximální hodnoty ve výsledku dotazu](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Kapitoly 17: LINQ](http://go.microsoft.com/fwlink/?LinkId=195277) v [programování Visual Basic 2008](http://go.microsoft.com/fwlink/?LinkId=195383)  
  
## <a name="see-also"></a>Viz také  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [LINQ na DataSet přehled](../../../../framework/data/adonet/linq-to-dataset-overview.md)  
 [Technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [Technologie LINQ to SQL nástroje v sadě Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
