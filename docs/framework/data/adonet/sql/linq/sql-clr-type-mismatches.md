---
title: Neshody typů SQL a CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 27708f4bb8e191156f578132602570bc4a6337b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781196"
---
# <a name="sql-clr-type-mismatches"></a>Neshody typů SQL a CLR

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]automatizuje většinu překladu mezi objektovým modelem a SQL Server. Nicméně některé situace zabraňují přesnému překladu. Tyto klíče se neshodují mezi typy modulu CLR (Common Language Runtime) a typy SQL Server databáze jsou shrnuty v následujících oddílech. Další podrobnosti o konkrétních mapováních typů a překladu funkcí najdete v [mapování typů SQL-CLR](sql-clr-type-mapping.md) a [datových typů a funkcí](data-types-and-functions.md).

## <a name="data-types"></a>Datové typy

K překladu mezi CLR a SQL Server dochází při posílání dotazu do databáze a při posílání výsledků zpět do objektového modelu. Například následující dotaz Transact-SQL vyžaduje dva převody hodnot:

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

Než bude možné spustit dotaz na SQL Server, musí být zadána hodnota parametru Transact-SQL. V tomto příkladu `id` musí být hodnota parametru nejprve přeložena z typu CLR <xref:System.Int32?displayProperty=nameWithType> na typ SQL Server `INT` tak, aby databáze mohla pochopit, co je hodnota. Pak pro načtení výsledků musí být sloupec SQL Server `DateOfBirth` přeložen z SQL Server `DATETIME` typu na typ CLR <xref:System.DateTime?displayProperty=nameWithType> pro použití v objektovém modelu. V tomto příkladu mají typy v objektovém modelu CLR a v databázi SQL Server přirozené mapování. Nejedná se však vždy o případ.

### <a name="missing-counterparts"></a>Chybějící protějšky

Následující typy nemají přiměřené protějšky.

- Neshoda v oboru názvů CLR <xref:System> :

  - **Celá čísla bez znaménka**. Tyto typy jsou obvykle mapovány na jejich podepsané protějšky větší velikosti, aby se předešlo přetečení. Literály lze převést na číslo se znaménkem stejné nebo menší velikosti na základě hodnoty.

  - **Logická hodnota**. Tyto typy mohou být mapovány na bit nebo větší řetězec čísla nebo řetězce. Literál lze namapovat na výraz, který je vyhodnocen na stejnou hodnotu (například `1=1` v SQL pro `True` ve specifikaci CLS).

  - **Časový**rozsah. Tento typ představuje rozdíl mezi dvěma `DateTime` hodnotami a neodpovídá hodnotě `timestamp` SQL Server. CLR <xref:System.TimeSpan?displayProperty=nameWithType> může v některých případech také namapovat `TIME` na typ SQL Server. Typ SQL Server `TIME` měl představovat kladné hodnoty méně než 24 hodin. CLR <xref:System.TimeSpan> má mnohem větší rozsah.

  > [!NOTE]
  > V tomto porovnání nejsou zahrnuty SQL Server <xref:System.Data.SqlTypes> .NET Framework typy v nástroji.

- Neshoda v SQL Server:

  - **Typy znaků s pevnou délkou**. Transact-SQL rozlišuje mezi kategoriemi Unicode a non-Unicode a má tři různé typy v každé kategorii: pevná délka `nchar` `varchar` / `char`, proměnlivá `nvarchar`délka /a větší velikost `ntext`. / `text` Typy znaků s pevnou délkou mohou být mapovány na <xref:System.Char?displayProperty=nameWithType> typ CLR pro načítání znaků, ale ve skutečnosti neodpovídají stejnému typu v rámci převodů a chování.

  - **Bit**. I když má `Nullable<Boolean>`doména stejný počet hodnot, jsou tyto dva různé typy. `bit` `Bit`přebírá `1` hodnoty `0` a místo `true`anelzeje použítjakoekvivalentlogickýchvýrazů/. `false`

  - **Časové razítko**. Na rozdíl od typu <xref:System.TimeSpan?displayProperty=nameWithType> CLR představuje typ SQL Server `TIMESTAMP` číslo o velikosti 8 bajtů generované databází, která je jedinečná pro každou aktualizaci a není založena na rozdílu mezi <xref:System.DateTime> hodnotami.

  - **Peníze** a **smallmoney**. Tyto typy lze namapovat na <xref:System.Decimal> , ale jsou v podstatě různé typy a jsou zpracovány jako takové funkce a převody založené na serveru.

### <a name="multiple-mappings"></a>Vícenásobné mapování

Existuje mnoho SQL Server datových typů, které lze mapovat na jeden nebo více datových typů CLR. Existuje také řada typů CLR, které lze namapovat na jeden nebo více typů SQL Server. I když mapování může být podporováno LINQ to SQL, neznamená to, že dva typy namapované mezi CLR a SQL Server jsou dokonalými shodami v přesnosti, rozsahu a sémantikě. Některá mapování mohou zahrnovat rozdíly v některých nebo všech těchto dimenzích. Můžete najít podrobnosti o těchto potenciálních rozdílech pro různé možnosti mapování v [mapování typu SQL-CLR](sql-clr-type-mapping.md).

### <a name="user-defined-types"></a>Uživatelsky definované typy

Uživatelsky definované typy CLR jsou navržené tak, aby pomohly přemostěníovat systémovou mezeru typu. Nicméně mají na starosti zajímavé problémy se správou verzí typů. Změna verze v klientovi se nemusí shodovat s změnou typu uloženého na databázovém serveru. Tato změna způsobí neshodu jiného typu, kde se Sémantika typu neshoduje, a je pravděpodobné, že by se měla zobrazit mezera verze. K dalším komplikacím dochází při refaktorování hierarchií dědičnosti v následných verzích.

## <a name="expression-semantics"></a>Sémantika výrazu

Kromě neshody s neshodou mezi CLR a typy databází přidávají výrazy složitost k neshodě. Neshoda sémantiky operátora, sémantika funkce, implicitní převod typu a pravidla priority musí být zvážena.

Následující pododdíly ilustrují neshodu mezi zjevnými podobnými výrazy. Je možné generovat výrazy SQL, které jsou sémanticky ekvivalentní danému výrazu CLR. Není však jasné, zda jsou sémantické rozdíly mezi zjevnými podobnými výrazy zřejmé pro uživatele CLR, a proto zda jsou zamýšlené a nepotřebné změny pro sémantickou rovnocennost. Jedná se o obzvláště kritický problém při vyhodnocování výrazu pro sadu hodnot. Viditelnost rozdílu může záviset na datech a být obtížné identifikovat během kódování a ladění.

### <a name="null-semantics"></a>Sémantika s hodnotou null

Výrazy SQL poskytují logiku se třemi hodnotami pro logické výrazy. Výsledek může být true, false nebo null. Naproti tomu CLR Určuje logický výsledek se dvěma hodnotami pro porovnání zahrnující hodnoty null. Vezměte v úvahu následující kód:

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

K podobnému problému dochází se zachováním u výsledků se dvěma hodnotami.

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

V předchozím případě můžete získat ekvivalentní chování při generování SQL, ale překlad nemusí přesně odpovídat vašemu záměru.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nezavádí C# `null` ani neVisual Basic `nothing` sémantiky porovnání na SQL. Operátory porovnání jsou syntakticky přeloženy na jejich ekvivalenty SQL. Sémantika odráží sémantiku systému SQL definovanou nastavením serveru nebo připojení. Dvě hodnoty null se považují za neshodné s výchozím nastavením SQL Server (i když můžete změnit nastavení pro změnu sémantiky). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bez ohledu na to nebere v úvahu nastavení serveru v překladu dotazů.

Porovnání s literálem `null` (`nothing`) je přeloženo na odpovídající verzi SQL (`is null` nebo `is not null`).

Hodnota `null` (`nothing`) v kolaci je definována SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemění kolaci.

### <a name="type-conversion-and-promotion"></a>Konverze a propagace typu

SQL podporuje bohatou sadu implicitních převodů ve výrazech. Podobné výrazy C# by vyžadovaly explicitní přetypování. Příklad:

- `Nvarchar`typy `DateTime` a lze v SQL porovnat bez explicitního přetypování; C# vyžaduje explicitní převod.

- `Decimal`je implicitně převeden na `DateTime` v SQL. C#nepovoluje implicitní převod.

Podobně, priorita typu v jazyce Transact-SQL se liší od priority typu v C# , protože podkladová sada typů je odlišná. Ve skutečnosti neexistují žádné jasné vztahy mezi podmnožinou a nadmnožinou mezi seznamy priorit. Například porovnávání `nvarchar` s objektem `varchar` způsobí implicitní převod `varchar` výrazu na `nvarchar`. CLR neposkytuje žádnou ekvivalentní povýšení.

V jednoduchých případech tyto rozdíly způsobují, že výrazy CLR s přetypováními mají být redundantní pro odpovídající výraz SQL. Důležitější je, že mezilehlé výsledky výrazu SQL mohou být implicitně povýšeny na typ, který nemá přesnou protějšek v C#a naopak. Celkový počet, testování, ladění a ověřování těchto výrazů přináší významné zatížení uživatele.

### <a name="collation"></a>Kolace

Transact-SQL podporuje explicitní kolace jako anotace typů řetězců znaků. Tato kolace určují platnost určitých porovnání. Například porovnávání dvou sloupců s různými explicitními kolací je chyba. Použití mnohem zjednodušeného typu řetězce CTS nezpůsobuje takové chyby. Vezměte v úvahu v následujícím příkladu:

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

V důsledku toho podklauzule kolace vytvoří *omezený typ* , který nelze nahradit.

Podobně je možné pořadí řazení výrazně lišit napříč systémy typů. Tento rozdíl ovlivňuje řazení výsledků. <xref:System.Guid>je řazeno na všech 16 bajtů podle lexikografickým pořadím Order`IComparable()`(), zatímco T-SQL porovnává identifikátory GUID v následujícím pořadí: node (10-15), Clock-SEQ (8-9), Time-high (6-7), Time-Mid (4-5), časový-dolní (0-3). Toto řazení bylo provedeno ve formátu SQL 7,0, pokud měly identifikátory GUID generované systémem NT takové pořadí oktetů. Přístup zajišťuje, aby identifikátory GUID generované v clusteru stejného uzlu byly společně v sekvenčním pořadí podle časového razítka. Přístup byl také užitečný pro vytváření indexů (příkazy INSERT se stanou připojením místo náhodného IOs). Pořadí bylo ve Windows později zakódované z důvodu ochrany osobních údajů, ale SQL musí zachovat kompatibilitu. Alternativním řešením je použít <xref:System.Data.SqlTypes.SqlGuid> <xref:System.Guid>místo.

### <a name="operator-and-function-differences"></a>Operátory a funkce – rozdíly

Operátory a funkce, které jsou v podstatě srovnatelné, mají mírně odlišnou sémantiku. Příklad:

- C#Určuje sémantiku krátkého okruhu na základě lexikálního pořadí operandů pro `&&` logické `||`operátory a. SQL na druhé straně je zaměřený na dotazy založené na sadě, a proto nabízí větší volnost v tom, aby Optimalizátor určilo pořadí spouštění. Mezi důsledky patří následující:

  - Překlad sémanticky ekvivalentního překladu by`CASE` vyžadoval "... `WHEN` … `THEN`"konstrukce v jazyce SQL, aby se zabránilo přeřazení spuštění operandu.

  - Volný `AND` převod na / operátory`OR` může způsobit neočekávané chyby, pokud C# výraz spoléhá na vyhodnocení druhého operandu na základě výsledku vyhodnocení prvního operandu.

- `Round()`funkce má odlišnou sémantiku v .NET Framework a v T-SQL.

- Počáteční index pro řetězce je 0 v modulu CLR, ale 1 v SQL. Proto všechny funkce, které mají index, vyžadují překlad indexu.

- Modul CLR podporuje operátor dělení ('% ') pro čísla s plovoucí desetinnou čárkou, ale SQL nikoli.

- `Like` Operátor efektivně získá Automatická přetížení na základě implicitních převodů. I když je `DateTime` `Like` operátor definován pro práci na typech řetězců znaků, implicitní převod z číselných typů nebo typů umožňuje používat tyto neřetězcové typy, a to stejně. `Like` V CTS neexistují srovnatelné implicitní převody. Proto jsou potřeba další přetížení.

    > [!NOTE]
    > Toto `Like` chování operátoru platí C# jenom pro; klíčové `Like` slovo Visual Basic se nezměnilo.

- Přetečení je vždy zaškrtnuto v SQL, ale je nutné ji explicitně zadat C# v (ne v Visual Basic), aby se předešlo wraparound. Předané celočíselné sloupce C1, C2 a C3, pokud je C1 + C2 uložen v C3 (Update T set C3 = C1 + C2).

    ```sql
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

- SQL provádí symetrické aritmetické zaokrouhlování při .NET Framework používá zaokrouhlování bank. Další podrobnosti najdete v článku 196652 znalostní báze.

- Ve výchozím nastavení se u běžných národních prostředí a porovnávání znakových řetězců rozlišují velká a malá písmena v SQL. V Visual Basic a v C#se rozlišují velká a malá písmena. Například `s == "Food"` `s` (`s = "Food"` v Visual Basic) a `s == "Food"` mohou vracet různé výsledky, pokud je `food`.

    ```sql
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

- Operátory nebo funkce aplikované na argumenty znakového typu s pevnou délkou v SQL mají výrazně odlišnou sémantiku než stejné operátory nebo funkce <xref:System.String?displayProperty=nameWithType>aplikované na CLR. Může se také zobrazit jako rozšíření chybějícího problému s protějškem, který je popsán v části o typech.

    ```sql
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

     K podobnému problému dochází při zřetězení řetězců.

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

V souhrnu může být pro výrazy CLR vyžadován překlad konvoluce a další operátory/funkce mohou být nezbytné k vystavení funkcí SQL.

### <a name="type-casting"></a>Přetypování typu

V C# a v SQL mohou uživatelé přepsat výchozí sémantiku výrazů pomocí explicitních přetypování typů (`Cast` a `Convert`). Vystavení této funkce napříč hranicí systému typů ale představuje dilematem. Přetypování SQL, které poskytuje požadovanou sémantiku, nelze snadno přeložit na odpovídající C# přetypování. Na druhé straně C# přetypování nejde přímo přeložit do ekvivalentního přetypování SQL z důvodu neshody typů, chybějících protějšků a různých hierarchií s prioritami typů. Vystavení neshody typů systému a ztráty významného výkonu výrazu je kompromis.

V jiných případech nemusí být přetypování typu potřeba v žádné doméně pro ověření výrazu, ale může být potřeba, aby se zajistilo, že se pro výraz správně použije mapování bez výchozího nastavení.

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a>Problémy s výkonem

Monitorování účtů pro některé rozdíly typu SQL Server-CLR může způsobit snížení výkonu při přechodu mezi systémy CLR a SQL Server typů. Mezi příklady scénářů, které mají vliv na výkon, patří následující:

- Vynucené pořadí vyhodnocení pro logické operátory and/or

- Generování SQL pro vynucení pořadí vyhodnocování predikátu omezuje schopnost Optimalizátoru SQL.

- Převody typů, ať už zavedené kompilátorem CLR nebo implementace relačních dotazů objektu, můžou curtail využití indexu.

     Například

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     Zvažte převod výrazu `(s = SOME_STRING_CONSTANT)`.

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

Kromě sémantických rozdílů je důležité vzít v úvahu dopady na výkon při přechodu mezi systémy SQL Server a CLR typů. U velkých datových sad můžou takové problémy s výkonem určit, jestli je možné aplikaci nasadit.

## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
