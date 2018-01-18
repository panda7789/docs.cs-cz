---
title: Neshody typu SQL CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a027bd898409708dd6800908a6736f5853058df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sql-clr-type-mismatches"></a>Neshody typu SQL CLR
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]umožňuje automatizovat většinu překlad mezi objektový model a SQL Server. Nicméně některých situacích zabránit přesný překlad. Tyto klíče neshody mezi běžné typy language runtime (CLR) a typy databáze systému SQL Server jsou shrnuty v následující části. Můžete najít další podrobnosti o konkrétní typ mapování a funkce překladu v [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) a [datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).  
  
## <a name="data-types"></a>Datové typy  
 Při odesílání dotazu do databáze, a při výsledky budou odeslány do objektový model dochází k převodu mezi CLR a SQL Server. Například následující dotaz jazyka Transact-SQL vyžaduje dva převody hodnot:  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 Aby bylo možné spustit dotaz na serveru SQL Server, musí být zadána hodnota pro parametr Transact-SQL. V tomto příkladu `id` hodnota parametru musí být nejprve převedeny z modulu CLR <xref:System.Int32?displayProperty=nameWithType> typ k systému SQL Server `INT` zadejte tak, aby databáze můžete porozumět, co je hodnota. Pak se načíst výsledky, SQL Server `DateOfBirth` sloupec musí být převedeny z SQL serveru `DATETIME` typ, který má CLR <xref:System.DateTime?displayProperty=nameWithType> typ pro použití v modelu objektu. Typy v modelu objektu CLR a databáze systému SQL Server v tomto příkladu se mít fyzické mapování. Ale není to vždy.  
  
### <a name="missing-counterparts"></a>Chybí svými protějšky  
 Následující typy nemají přiměřené svými protějšky.  
  
-   V modulu CLR se neshoduje <xref:System> obor názvů:  
  
    -   **Nepodepsané celá čísla**. Tyto typy jsou obvykle namapované na jejich podepsané svými protějšky větší velikosti předejdete přetečení. Literály lze převést na podepsané číselný stejné nebo menší velikosti, na základě hodnoty.  
  
    -   **Logická hodnota**. Tyto typy lze mapovat na bit nebo větší číselnou nebo řetězec. Literál lze mapovat na výraz, který se vyhodnotí na stejnou hodnotu (například `1=1` v SQL pro `True` ve CLS).  
  
    -   **TimeSpan**. Tento typ reprezentuje rozdíl mezi dvěma `DateTime` hodnoty a nemusí odpovídat `timestamp` systému SQL Server. Modul CLR <xref:System.TimeSpan?displayProperty=nameWithType> také mapovat k systému SQL Server `TIME` typu v některých případech. SQL Server `TIME` typu byla určena pouze kladné hodnoty představují méně než 24 hodin. Modul CLR <xref:System.TimeSpan> má mnohem větší rozsah.  
  
    > [!NOTE]
    >  Specifické pro službu SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] typy v <xref:System.Data.SqlTypes> nejsou součástí Toto porovnání.  
  
-   Neshody v systému SQL Server:  
  
    -   **Pevná délka znakové typy**. Příkaz Transact-SQL rozlišuje mezi kategorií kódování Unicode a kódování Unicode a má tři odlišné typy v každé kategorii: pevná délka `nchar` / `char`, proměnlivou délkou `nvarchar` / `varchar`, a větší velikost `ntext` / `text`. Typy znaků pevnou délkou mapovat modulu CLR <xref:System.Char?displayProperty=nameWithType> typ pro načítání znaků, ale jejich nemusí odpovídat skutečně stejného typu v převody a chování.  
  
    -   **Bit**. I když `bit` stejný počet hodnot, jako má doména `Nullable<Boolean>`, jsou dva různé typy. `Bit`přijímá hodnoty `1` a `0` místo `true` / `false`a nelze jej použít jako rovnocenné výrazy logických hodnot.  
  
    -   **Časové razítko**. Na rozdíl od CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ, SQL Server `TIMESTAMP` typ představuje číslo 8 bajtů generovaných databázi, která je jedinečné pro jednotlivé aktualizace a není založena na rozdíl mezi <xref:System.DateTime> hodnoty.  
  
    -   **Peníze** a **SmallMoney**. Tyto typy lze mapovat na <xref:System.Decimal> , ale jsou v podstatě různé typy a jako takový nakládá serverových funkcí a převody.  
  
### <a name="multiple-mappings"></a>Víc mapování  
 Existuje mnoho typů dat systému SQL Server, které můžete namapovat na jeden nebo více typů CLR data. Existují také mnoho typů CLR, které můžete namapovat na jeden nebo více typů systému SQL Server. I když mapování může být podporovaná technologií LINQ to SQL, neznamená to, že existují dva typy namapované mezi CLR a SQL Server jsou ideální shoda v přesnost, rozsah a sémantiku. Některé mapování může zahrnovat rozdíly v některého nebo všech z těchto dimenzí. Můžete najít podrobnosti o těchto potenciální rozdíly pro různé možnosti mapování na [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
### <a name="user-defined-types"></a>Uživatelem definované typy  
 Uživatelem definované typy CLR jsou navržené tak, abyste přemostění mezery typ systému. Nicméně surface zajímavé problémy o správě verzí typu. Ke změně verze na klienta nemusí odpovídat změnou v typu uložené na serveru databáze. Všechny tyto změny způsobí, že jiný Neshoda typu, kde nemusí odpovídat Sémantika typu a mezera verze je pravděpodobně budou zobrazeny. Další komplikace docházet k hierarchie dědičnosti jsou rozdělili v následných verzí.  
  
## <a name="expression-semantics"></a>Sémantika výrazů  
 Kromě pairwise neshody mezi typy CLR a databáze výrazy přidání složitosti do neshody. Je třeba zvážit neshody v operátor sémantiku, funkce sémantiku, převod implicitní typu a pravidla priorit.  
  
 Následující témata ukazují neshody mezi zjevně podobné výrazy. Může být možné generovat SQL výrazů, které odpovídají sémanticky daného výrazu CLR. Ale není jasné jestli sémantického rozdíly mezi zjevně podobné výrazy jsou zřejmá CLR uživateli, a proto jestli jsou změny, které jsou požadovány pro sémantické ekvivalenční určené nebo ne. To je obzvláště důležité problém při vyhodnocování výrazu pro sadu hodnot. Viditelnost rozdíl může závisí na data - a bude obtížné určit během kódování a ladění.  
  
### <a name="null-semantics"></a>Sémantika hodnotu Null.  
 Výrazy SQL zadejte s hodnotou tři logiku pro výrazy logických hodnot. Výsledkem mohou být true, false nebo hodnotu null. Naopak CLR určuje dvěma hodnotami výsledek logickou hodnotu pro porovnání zahrnující hodnoty null. Vezměte v úvahu následující kód:  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 Podobně jako nastaly problémy s předpokladem o výsledcích dvěma hodnotami.  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 V předchozím případě můžete získat ekvivalentní chování při generování SQL, ale překlad nemusí přesně odrážet svůj záměr.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepředstavuje C# `null` nebo [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` porovnání sémantiku SQL. Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL. Sémantika projeví SQL sémantiku podle definice nastavení serveru nebo připojení. Dvě hodnoty null považovány za nerovné pod výchozí nastavení serveru SQL (i když můžete změnit nastavení můžete změnit sémantiky). Bez ohledu na to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nebere v úvahu nastavení serveru v překlad dotazu.  
  
 Porovnání s literálové `null` (`nothing`) je přeložená na příslušnou verzi SQL (`is null` nebo `is not null`).  
  
 Hodnota `null` (`nothing`) v kolaci je definovaný systémem SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nezmění kolace.  
  
### <a name="type-conversion-and-promotion"></a>Převod typů a povýšení  
 SQL podporuje širokou škálu implicitní převody ve výrazech. Podobné výrazy v jazyce C# by vyžadovaly explicitní přetypování. Příklad:  
  
-   `Nvarchar`a `DateTime` typy je možné porovnávat v SQL bez žádné explicitní přetypování; C# vyžaduje explicitní převod.  
  
-   `Decimal`je implicitně převést na `DateTime` v systému SQL. C# neumožňuje pro implicitní převod.  
  
 Typ priority v Transact-SQL se podobně liší od priority typu v C# protože základní sadu typů se liší. Mezi seznamy přednost ve skutečnosti není žádný vztah zrušte podmnožinu nebo nadmnožinou. Například porovnání `nvarchar` s `varchar` způsobí, že implicitní převod `varchar` výraz, který se `nvarchar`. Modul CLR poskytuje žádná ekvivalentní povýšení.  
  
 Tyto rozdíly v jednoduchých případech způsobit CLR výrazy s přetypování být redundantní pro odpovídající výraz SQL. Je důležité, mezilehlých výsledků výrazu SQL může implicitně převést na typ, který nemá přesné protějšek v C#, a naopak. Celkově platí testování, ladění a ověření těchto výrazů přidá významné zatížení na uživatele.  
  
### <a name="collation"></a>Kolace  
 Příkaz Transact-SQL podporuje explicitní řazení jako poznámky typy řetězec znaků. Tyto kolace určit platnost určité porovnání. Porovnání dva sloupce s jinou kolací explicitní je například k chybě. Použití mnohem jednodušší typu řetězec CTS nezpůsobí takové chyby. Podívejte se na následující příklad:  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 Ve skutečnosti dílčí kolace vytvoří *omezený typ* není nahraditelné.  
  
 Pořadí řazení podobně, může být výrazně odlišné mezi systémy typu. Tento rozdíl ovlivňuje řazení výsledků. <xref:System.Guid>je na všech 16 bajtů seřazené podle lexicographic pořadí (`IComparable()`), zatímco T-SQL porovná identifikátory GUID v následujícím pořadí: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3). Toto uspořádání bylo provedeno v SQL 7.0 při generované NT identifikátory GUID měl takový octet příkaz. Přístup zajistit společně pocházejí identifikátory GUID, které jsou generované na stejném uzlu clusteru v postupném pořadí podle časového razítka. Přístup byl také užitečná pro vytváření indexů (vložení stát připojí místo náhodných IOs). Pořadí byl kódována později v systému Windows z důvodu aspekty ochrany osobních údajů, ale SQL musí udržovat kompatibilitu. Alternativní řešení je použití <xref:System.Data.SqlTypes.SqlGuid> místo <xref:System.Guid>.  
  
### <a name="operator-and-function-differences"></a>Operátor a rozdíly ve funkcích  
 Operátory a funkce, které jsou v podstatě srovnatelné mají podobný sémantiku. Příklad:  
  
-   C# určuje sémantiku krátké okruh založený na lexikální pořadí operandy pro logické operátory `&&` a `||`. SQL na druhé straně je určená pro dotazy založené na sadě a proto poskytuje dává větší svobodu pro Optimalizátor k rozhodování o pořadí zpracování. Některé důsledky zahrnují následující:  
  
    -   Sémanticky ekvivalentní překlad by vyžadovaly "`CASE` ... `WHEN` … `THEN`"vytvořit v systému SQL, aby se zabránilo změny pořadí spouštění operand.  
  
    -   Přijít překlad, aby `AND` / `OR` operátory může způsobit neočekávané chyby, pokud výraz jazyka C# závisí na vyhodnocení Druhý operand založen na výsledek vyhodnocení první operand.  
  
-   `Round()`funkce má jinou sémantiku [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] a v T-SQL.  
  
-   Počáteční index pro řetězce je 0 v modulu CLR ale 1 v systému SQL. Proto všechny funkce, která má index musí překlad index.  
  
-   Modul CLR podporuje operátor numerického zbytku (%) pro čísla s plovoucí desetinnou ale SQL neexistuje.  
  
-   `Like` Operátor efektivně získá automatické přetížení podle implicitní převody. I když `Like` operátor je definována pro provoz na typy řetězec znaků, implicitní převod z číselnými typy nebo `DateTime` typy umožňuje tyto typy jiné než řetězec, který se má použít s `Like` stejně dobře. V CTS neexistují porovnatelné implicitní převody. Proto je potřeba další přetížení.  
  
    > [!NOTE]
    >  To `Like` operátor chování platí pouze; pro C# jazyka Visual Basic `Like` – klíčové slovo je beze změny.  
  
-   Přetečení je vždy zaškrtnuto v systému SQL, ale musí být explicitně určena v jazyce C# (ne v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) předejdete wraparound. Zadané číslo sloupce C1, C2 a C3, pokud je C1 + C2 uložen v C3 (C3 nastavte aktualizace T = C1 + C2).  
  
    ```  
    create table T3 (  
        Col1      integer,  
        Col2      integer  
    )  
    insert into T3 (col1, col2) values (2147483647, 5)  
    -- Valid values: max integer value and 5.  
    select * from T3 where col1 + col2 < 0  
    -- Produces arithmetic overflow error.  
    ```  
  
 [!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
 [!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]  
  
-   SQL provede symetrický aritmetické operace zaokrouhlení při [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] používá banker je zaokrouhlení. Najdete v článku Knowledge Base 196652 další podrobnosti.  
  
-   Ve výchozím nastavení pro běžné národní prostředí porovnání řetězců znaků se velká a malá písmena v systému SQL. V jazyce Visual Basic a v jazyce C# jsou malá a velká písmena. Například `s == "Food"` (`s = "Food"` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) a `s == "Food"` přispět odlišné výsledky, pokud `s` je `food`.  
  
    ```  
    -- Assume default US-English locale (case insensitive).  
    create table T4 (  
        Col1      nvarchar (256)  
    )  
    insert into T4 values (‘Food’)   
    insert into T4 values (‘FOOD’)  
    select * from T4 where Col1 = ‘food’  
    -- Both the rows are returned because of case-insensitive matching.  
    ```  
  
 [!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
 [!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]  
  
-   Operátory / funkce u argumenty typu znak pevnou délkou v systému SQL, že výrazně odlišné sémantiku než stejné operátory nebo funkce modulu CLR u <xref:System.String?displayProperty=nameWithType>. Může zobrazit také jako rozšíření popsané v části o typech chybějící příslušného problému.  
  
    ```  
    create table T4 (  
        Col1      nchar(4)  
    )  
    Insert into T5(Col1) values ('21');  
    Insert into T5(Col1) values ('1021');  
    Select * from T5 where Col1 like '%1'  
    -- Only the second row with Col1 = '1021' is returned.  
    -- Not the first row!  
    ```  
  
     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]  
  
     Podobný problém se vyskytuje v zřetězení řetězců.  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 Souhrnně convoluted překlad mohou být požadovány pro CLR výrazy a další operátory nebo funkce může být nutné vystavit funkcionalitu SQL.  
  
### <a name="type-casting"></a>Přetypování typu  
 V jazyce C# a v systému SQL, uživatelé mohou přepsat výchozí sémantika výrazů pomocí explicitního typu přetypování (`Cast` a `Convert`). Tato funkce vystavení přes hranice typu systému však představuje dilematem. Přetypování SQL poskytující požadované sémantiku nelze přeložit snadno odpovídající jazyka C# přetypování. Na druhé straně nejde přetypování C# přeložit přímo na ekvivalentní SQL přetypování z důvodu neshody typu, chybějící svými protějšky a jiný typ přednost hierarchií. Je kompromis mezi vystavení Neshoda typu systému a ztrátě významné power výrazu.  
  
 Přetypování typu v ostatních případech nemusí být potřeba v obou doménách pro ověření výrazu ale můžou požadovat, abyste měli jistotu, že je jiné než výchozí mapování správně použít pro výraz.  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a>Problémy s výkonem  
 Monitorování účtů pro některé-modulu CLR SQL serveru rozdíly typu může resut k poklesu výkonu při překračování mezi CLR a SQL Server typu systémy. Příklady situací, což ovlivňuje výkon, patří:  
  
-   Vynutit pořadí vyhodnocení pro logické a operátory  
  
-   Generování SQL k vynucení pořadí predikátem vyhodnocení omezuje možnost Optimalizátor SQL.  
  
-   Převody typů zda zavedená kompilátorem CLR nebo objekt relační implementací dotaz, může omezovat použití indexu.  
  
     Například  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     Vezměte v úvahu překlad výrazu `(s = SOME_STRING_CONSTANT)`.  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 Kromě sémantického rozdílů je důležité vzít v úvahu dopad na výkon při překročení meze mezi SQL serverem a systémy typu CLR. Pro velké sady dat můžete tyto problémy s výkonem určit, zda je aplikace nasadit.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
