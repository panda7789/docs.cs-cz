---
title: SQL-CLR Type Mismatches
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 0abb1bd25c40ba55806fe80b39db1ac418f3f308
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700946"
---
# <a name="sql-clr-type-mismatches"></a>SQL-CLR Type Mismatches
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatizuje většinu překlad mezi objektový model a systému SQL Server. Nicméně některé situace zabránit přesné překladu. Tyto klíče neshody mezi běžné typy language runtime (CLR) a typy databáze systému SQL Server jsou shrnuté v následujících částech. Můžete najít další podrobnosti o mapování určitého typu a funkce překladu na [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) a [datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).  
  
## <a name="data-types"></a>Datové typy  
 Při odesílání dotazu do databáze a kdy se výsledky odesílají zpět k objektovému modelu dochází k převodu mezi CLR a systému SQL Server. Například následující dotaz jazyka Transact-SQL vyžaduje dva převody hodnot:  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 Předtím, než je možné provést dotaz v systému SQL Server, musíte zadat hodnotu pro parametr příkazů jazyka Transact-SQL. V tomto příkladu `id` hodnota parametru musí být nejdříve přeložena z modul CLR. <xref:System.Int32?displayProperty=nameWithType> typu k serveru SQL Server `INT` tak, aby databáze můžete pochopit, co je hodnota. Potom k načtení výsledků, SQL Server `DateOfBirth` sloupec musí být převedeny z SQL serveru `DATETIME` typ, který má modul CLR <xref:System.DateTime?displayProperty=nameWithType> typ pro použití v objektovém modelu. V tomto příkladu typy CLR objektový model a databáze systému SQL Server mají přirozené mapování. Ale není to vždy.  
  
### <a name="missing-counterparts"></a>Chybějící protějšky  
 Následující typy nemají přiměřené protějšky.  
  
-   V modulu CLR se neshoduje s <xref:System> obor názvů:  
  
    -   **Čísla typu unsigned integer**. Tyto typy se obvykle mapují na své ekvivalenty podepsaný o větší velikosti chcete zabránit přetečení. Literály lze převést na číselnou znaménkem stejné nebo menší velikosti na základě hodnoty.  
  
    -   **Logická**. Tyto typy lze mapovat na bit nebo větší numerická nebo řetězec. Literál je možné mapovat na výraz, který se vyhodnotí jako stejná hodnota (například `1=1` v SQL pro `True` ve specifikaci CLS).  
  
    -   **Časový interval**. Tento typ reprezentuje rozdíl mezi dvěma `DateTime` hodnoty a nemusí odpovídat `timestamp` systému SQL Server. Modul CLR <xref:System.TimeSpan?displayProperty=nameWithType> může také namapovat na SQL Server `TIME` typ v některých případech. SQL Server `TIME` typu byla určena pouze k reprezentaci kladné hodnoty kratší než 24 hodin. Modul CLR <xref:System.TimeSpan> má mnohem větší rozsah.  
  
    > [!NOTE]
    >  SQL Server – konkrétní [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] napíše <xref:System.Data.SqlTypes> nejsou součástí tohoto porovnání.  
  
-   Neshody v systému SQL Server:  
  
    -   **Typy znaků pevné délky**. Příkaz Transact-SQL rozlišuje mezi kategorie sady Unicode a kódování Unicode a má tři různé typy v každé kategorii: pevnou délku `nchar` / `char`, s proměnnou délkou `nvarchar` / `varchar`, a větší velikost `ntext` / `text`. Typy znaků pevné délky mapovat CLR <xref:System.Char?displayProperty=nameWithType> znaky typu pro načtení, ale ve skutečnosti neodpovídají na stejný typ. převody a chování.  
  
    -   **Bit**. I když `bit` doména má stejný počet hodnot jako `Nullable<Boolean>`, jsou dva různé typy. `Bit` přijímá hodnoty `1` a `0` místo `true` / `false`a nelze jej použít jako rovnocenné logických výrazů.  
  
    -   **Časové razítko**. Na rozdíl od CLR <xref:System.TimeSpan?displayProperty=nameWithType> zadejte SQL Server `TIMESTAMP` typ představuje číslo 8bajtový generován databází, které je jedinečné pro jednotlivé aktualizace a není založena na rozdíl mezi <xref:System.DateTime> hodnoty.  
  
    -   **Peníze** a **SmallMoney**. Tyto typy lze mapovat na <xref:System.Decimal> , ale jsou v podstatě různé typy a jako takový nakládá serverových funkcí a převody.  
  
### <a name="multiple-mappings"></a>Mapování více  
 Existuje mnoho typů dat serveru SQL Server, namapované na jeden nebo více datové typy CLR. Existují také mnoho typů CLR, které můžete namapovat na jeden nebo více typů systému SQL Server. I když mapování může být podporována technologií LINQ to SQL, neznamená to, že tyto dva typy mapovány mezi CLR a systému SQL Server se skvěle hodí v přesnost, rozsahu a sémantika. Některé mapování může obsahovat rozdíly v některých nebo všech těchto dimenzí. Můžete najít podrobnosti o těchto rozdílech potenciální pro různé možnosti mapování na [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
### <a name="user-defined-types"></a>Uživatelem definované typy  
 Uživatelem definované typy CLR jsou navržené tak, abychom překleňte propast systému typu. Nicméně poskytování zajímavých problémů o správě verzí typu. Změnou v typ uložený na databázovém serveru nemusí odpovídat změnu ve verzi na straně klienta. Tato změna způsobí, že jiný Neshoda typu, kde nemusí odpovídat Sémantika typu a mezera verze je pravděpodobné, že budou zobrazeny. Hierarchie dědičnosti implementovány v následných verzích docházet k další komplikace.  
  
## <a name="expression-semantics"></a>Sémantika výrazů  
 Výrazy kromě pairwise Neshoda mezi typy CLR a databáze přidat složitost neshoda. Musí přestat považovat neshody v operátor sémantiku, sémantiku funkce, implicitní převod typu a pravidel.  
  
 Následující témata ukazují neshody mezi zjevně podobné výrazy. Je možné generovat SQL výrazy, které jsou sémanticky ekvivalentní daného výrazu CLR. Ale není jasné, jestli jsou menší významové rozdíly mezi zjevně podobné výrazy CLR uživateli zřejmé, a proto určuje, zda jsou určeny změny, které jsou požadovány pro sémantické ekvivalence nebo ne. To je zvlášť zásadní potíže při vyhodnocování výrazu pro sadu hodnot. Viditelnost rozdíl může záviset na data – a být obtížné určit během psaní kódu a ladění.  
  
### <a name="null-semantics"></a>Sémantika s hodnotou Null  
 Výrazy SQL poskytují tři vracející logiku pro logické výrazy. Výsledkem může být true, false nebo null. Naopak CLR určuje dvěma hodnotami výsledek logickou hodnotu pro porovnání s hodnotami null. Vezměte v úvahu následující kód:  
  
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
  
 Podobný problém se vyskytuje za předpokladu o výsledcích dvěma hodnotami.  
  
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
  
 V předchozím případě získáte ekvivalentního chování při generování SQL, ale překladu nemusí přesně odrážet váš záměr.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepředstavuje C# `null` nebo Visual Basic `nothing` porovnání sémantiky pro SQL. Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL. Sémantika odrážet SQL sémantiku dle nastavení serveru nebo připojení. Dvě hodnoty null se považují za nestejné podle výchozího nastavení systému SQL Server (i když můžete změnit nastavení můžete změnit sémantiku). Bez ohledu na to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nebere v úvahu nastavení serveru v překladu dotazu.  
  
 Porovnání s literál `null` (`nothing`) se přeloží na odpovídající verzi SQL (`is null` nebo `is not null`).  
  
 Hodnota `null` (`nothing`) v kolaci je definován pomocí SQL serveru. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nedojde ke změně kolace.  
  
### <a name="type-conversion-and-promotion"></a>Převod typu a podpora  
 SQL podporuje širokou škálu implicitních převodů ve výrazech. Podobně jako výrazy v C# by vyžaduje explicitní přetypování. Příklad:  
  
-   `Nvarchar` a `DateTime` typy lze porovnat v SQL bez žádné explicitní přetypování; C# vyžaduje explicitní převod.  
  
-   `Decimal` je implicitně převeden na `DateTime` v SQL. C#neumožňuje implicitní převod.  
  
 Priorita typ příkazů jazyka Transact-SQL se liší od typu priority v C# protože základní sadu typů se liší. Mezi seznamy prioritu ve skutečnosti není žádný vztah vymazat dílčí/nadmnožinou. Například porovnávání `nvarchar` s `varchar` způsobí, že implicitní převod `varchar` výraz, který se `nvarchar`. CLR poskytuje žádná ekvivalentní povýšení.  
  
 Tyto rozdíly v jednoduché případech způsobit výrazy CLR pomocí přetypování redundantní pro odpovídající výraz SQL. Důležitější je, mezivýsledků SQL výraz může být implicitně povýšen na typ, který nemá přesné protějšek v C#a naopak. Celkově testování, ladění a ověřování těchto výrazů přidá významné zatížení na uživatele.  
  
### <a name="collation"></a>Kolace  
 Příkaz Transact-SQL podporuje explicitní řazení jako poznámky a typy řetězce znaků. Tyto kolace určení platnosti určité porovnání. Například dva sloupce s jinou kolací explicitní porovnávání se o chybu. Použití typu řetězec mnohem jednodušší CTS nezpůsobí tyto chyby. Vezměte v úvahu v následujícím příkladu:  
  
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
  
 V důsledku toho se vytvoří klauzule kolace *s omezením pomocí specifikátoru typu* , který není zaměnitelné.  
  
 Pořadí řazení podobně, může být výrazně liší mezi systémy typu. Tento rozdíl se týká řazení výsledků. <xref:System.Guid> je ve slovníkovém pořadí seřazená podle všech 16 bajtů (`IComparable()`), zatímco T-SQL porovnává GUID v následujícím pořadí: node(10-15) clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3). Toto uspořádání bylo provedeno SQL 7.0, kdy tyto objednávky octet NT generované identifikátory GUID. Tento přístup, že jsou splněné, GUID, které jsou generované na stejném uzlu clusteru pochází společně v postupném pořadí podle časového razítka. Přístup byl také užitečné pro vytváření indexů (vložení stát připojí namísto náhodného IOs). Pořadí se kódována později ve Windows z důvodu aspekty ochrany osobních údajů, ale SQL musí zachovat kompatibilitu. Alternativní řešení, je použít <xref:System.Data.SqlTypes.SqlGuid> místo <xref:System.Guid>.  
  
### <a name="operator-and-function-differences"></a>Operátor a rozdíly ve funkcích  
 Operátory a funkce, které jsou v podstatě srovnatelné mají mírně odlišnou sémantiku. Příklad:  
  
-   C#Určuje sémantiku zkráceného vyhodnocení na základě lexikální pořadí operandy pro logické operátory `&&` a `||`. SQL na druhé straně je určena pro dotazy založené na sadě a proto poskytuje více volnosti pro Optimalizátor rozhodnout pořadí provádění. Důsledky patří následující:  
  
    -   Sémanticky ekvivalentní překlad by vyžadovaly "`CASE` ... `WHEN` … `THEN`"vytvořit v SQL, aby se zabránilo změny pořadí spouštění operand.  
  
    -   Volný převod do kódu `AND` / `OR` operátory může způsobit neočekávané chyby, pokud C# výraz spoléhá na vyhodnocení druhého operandu je založeno na výsledku vyhodnocení prvním operandem.  
  
-   `Round()` funkce má odlišnou sémantiku [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] a v T-SQL.  
  
-   Počáteční index pro řetězce je 0 v modulu CLR, ale 1 v SQL. Proto všechny funkce, které má index musí index překladu.  
  
-   Modul CLR podporuje operátor numerického zbytku (%) pro čísla s plovoucí desetinnou ale SQL to neuvádí.  
  
-   `Like` Operátor efektivně získá automatické přetížení založené na implicitní převody. I když `Like` je operátor definován provozovat na znakové řetězce typy implicitní převod z číselných typů nebo `DateTime` umožňuje tyto typy jiné než řetězec, který se má použít s typy `Like` stejně. V CTS neexistují porovnatelné implicitní převody. Proto je potřeba další přetížení.  
  
    > [!NOTE]
    >  To `Like` operátor chování platí pro C# pouze; Visual Basic `Like` – klíčové slovo je beze změny.  
  
-   Přetečení vždy změnami SQL ale musí být explicitně zadán v C# (nejsou v jazyce Visual Basic), aby vrácení. Zadaný sloupcích s celými čísly C1, C2 a C3, pokud je C1 + C2 je uložen v C3 (C3 nastavte aktualizace T = C1 + C2).  
  
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
  
-   SQL provede symetrický aritmetické operace při zaokrouhlení [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] společnosti používá bankovní zaokrouhlení. Najdete v článku znalostní báze 196652 další podrobnosti.  
  
-   Ve výchozím nastavení pro běžné národní prostředí jsou porovnávání řetězců znaků velkých a malých písmen v SQL. V jazyce Visual Basic a v C#, jsou malá a velká písmena. Například `s == "Food"` (`s = "Food"` v jazyce Visual Basic) a `s == "Food"` mohou přinést různé výsledky, pokud `s` je `food`.  
  
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
  
-   Operátory nebo funkce použít pro argumenty typu znaků pevné délky v SQL mají výrazně odlišnou sémantiku než stejné operátory nebo funkce u CLR <xref:System.String?displayProperty=nameWithType>. To může také zobrazit jako rozšíření chybí problému protějšek popsáno v části o typech.  
  
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
  
     Podobný problém se vyskytuje pomocí zřetězení řetězců.  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 Stručně řečeno složitými překladu může být nezbytný pro CLR výrazy a další operátory nebo funkce může být nutné vystavit funkčnost SQL.  
  
### <a name="type-casting"></a>Přetypování typu  
 V C# a v SQL, můžou uživatelé potlačit výchozí sémantika výrazů pomocí přetypování explicitních typů (`Cast` a `Convert`). Vystavení tuto funkci systému hranice typu však představuje dilema. Přetypování SQL, která poskytuje požadovanou sémantiku nejde přeložit snadno do odpovídající C# přetypování. Na druhé straně C# přetypování nelze přeložit přímo na ekvivalentní SQL přetypovat z důvodu neshody typů, chybějící protějšky a hierarchie prioritu různých typů. Je kompromis mezi vystavení Neshoda typu systému a ztrátě významné sílu výrazu.  
  
 V jiných případech nemusí být potřeba v obou domén pro ověření výrazu přetypování typu, ale může být vyžadováno, aby se zajistilo, že je správně použít jiné než výchozí mapování pro výraz.  
  
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
 Monitorování účtů pro některé-modulu CLR SQL serveru rozdíly typu může vést ke snížení výkonu při přecházení mezi mezi CLR a systému SQL Server typu systémy. Příklady scénářů vliv na výkon, patří:  
  
-   Vynutit pořadí vyhodnocování pro logické a/nebo operátory  
  
-   Generování SQL k vynucení pořadí vyhodnocení predikátu omezuje možnost optimalizace SQL.  
  
-   Převody typů, ať už zavedené kompilátorem CLR nebo implementaci objektově-relační dotazu, může omezovat použití indexu.  
  
     Například  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     Vezměte v úvahu překladu výrazu `(s = SOME_STRING_CONSTANT)`.  
  
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
  
 Kromě menší významové rozdíly je důležité vzít v úvahu dopad na výkon při přecházení mezi mezi SQL serverem a systémy typ CLR. Pro velké datové sady můžete tyto problémy s výkonem zjistit, zda je aplikace nasadit.  
  
## <a name="see-also"></a>Viz také:
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
