---
title: Převod standardních operátorů dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 4df1653b7bd6865ad9f5d7d3fb9be6815dcfe018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781012"
---
# <a name="standard-query-operator-translation"></a>Převod standardních operátorů dotazů

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]přeloží standardní operátory dotazu na příkazy SQL. Procesor dotazů databáze určuje sémantiku provádění překladu SQL.

Standardní operátory dotazu jsou definovány pro *sekvence*. Sekvence je *seřazena* a spoléhá na referenční identitu pro každý prvek sekvence. Další informace najdete v tématu Přehled [standardních operátorů dotazůC#()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [standardní operátory dotazu (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

SQL slouží hlavně pro *neuspořádané sady hodnot*. Řazení je obvykle výslovně uvedeno, operace následného zpracování, která je použita na konečný výsledek dotazu, nikoli na mezilehlé výsledky. Identita je definována hodnotami. Z tohoto důvodu jsou dotazy SQL srozumitelné pro práci s více sadami (*penalt*) místo *sad*.

Následující odstavce popisují rozdíly mezi standardními operátory dotazů a jejich překladem SQL pro poskytovatele SQL Server pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

## <a name="operator-support"></a>Podpora operátorů

### <a name="concat"></a>Spojuje

<xref:System.Linq.Enumerable.Concat%2A> Metoda je definována pro seřazené množiny, kde pořadí přijímače a pořadí argumentu jsou stejné. <xref:System.Linq.Enumerable.Concat%2A>funguje stejně `UNION ALL` jako více sad následovaných běžným pořadím.

Poslední krok je seřazen v SQL před vytvořením výsledků. <xref:System.Linq.Enumerable.Concat%2A>nezachovává pořadí argumentů. Aby bylo zajištěno vhodné řazení, je nutné explicitně seřadit výsledky <xref:System.Linq.Enumerable.Concat%2A>.

### <a name="intersect-except-union"></a>Průsečík, s výjimkou sjednocení

Metody <xref:System.Linq.Enumerable.Intersect%2A> a<xref:System.Linq.Enumerable.Except%2A> jsou dobře definovány pouze pro sady. Sémantika pro více sad není definována.

<xref:System.Linq.Enumerable.Union%2A> Metoda je definována pro množiny jako neuspořádané zřetězení množin (efektivně výsledek klauzule UNION ALL v SQL).

### <a name="take-skip"></a>Vzít, přeskočit

<xref:System.Linq.Enumerable.Take%2A>metody <xref:System.Linq.Enumerable.Skip%2A> a jsou dobře definovány pouze proti *seřazeným sadám*. Sémantika pro neuspořádané sady nebo více sad není definována.

> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).

Z důvodu omezení pro řazení v SQL se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argumentu těchto metod do výsledku metody. Zvažte například následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz:

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

Vygenerovaný SQL pro tento kód přesune řazení na konec následujícím způsobem:

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

Je zřejmé, že všechna zadaná řazení musí být konzistentní, když <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> zřetězené dohromady. V opačném případě nejsou výsledky definovány.

<xref:System.Linq.Enumerable.Take%2A> A<xref:System.Linq.Enumerable.Skip%2A> jsou dobře definovány pro nezáporné, konstantní celočíselné argumenty založené na standardní specifikaci operátoru dotazu.

### <a name="operators-with-no-translation"></a>Operátory bez překladu

Následující metody nejsou přeloženy pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Nejběžnějším důvodem je rozdíl mezi neseřazenými množinami a sekvencemi.

|Operátory|Dobře chápete důvody|
|---------------|---------------|
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Dotazy SQL pracují s více sadami, nikoli v sekvencích. `ORDER BY`musí se jednat o poslední klauzuli použitou pro výsledky. Z tohoto důvodu neexistuje žádný překlad pro obecné účely těchto dvou metod.|
|<xref:System.Linq.Enumerable.Reverse%2A>|Překlad této metody je možný pro seřazenou sadu, ale není aktuálně přeložen pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Překlad těchto metod je možný pro seřazenou sadu, ale není aktuálně přeložen pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Dotazy SQL pracují s více sadami, nikoli s indexovanými sekvencemi.|
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>(Overload s výchozím ARG)|Obecně platí, že u libovolné řazené kolekce členů nejde zadat výchozí hodnotu. Hodnoty null pro řazené kolekce členů jsou možné v některých případech prostřednictvím vnějších spojení.|

## <a name="expression-translation"></a>Překlad výrazu

### <a name="null-semantics"></a>Sémantika null

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]neukládá sémantiku porovnání s hodnotou null na SQL. Operátory porovnání jsou syntakticky přeloženy na jejich ekvivalenty SQL. Z tohoto důvodu sémantika odráží sémantiku SQL, která je definovaná nastavením serveru nebo připojení. Například dvě hodnoty null se považují za neshodné s výchozím SQL Server nastavením, ale můžete změnit nastavení pro změnu sémantiky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nebere v úvahu nastavení serveru při překládání dotazů.

Porovnání s literálem null je přeloženo na odpovídající verzi SQL (`is null` nebo `is not null`).

Hodnota `null` v kolaci je definována SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nemění kolaci.

### <a name="aggregates"></a>Agregace

Agregační metoda <xref:System.Linq.Enumerable.Sum%2A> standardního operátoru dotazu vyhodnocuje nulu pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému jsou sémantika jazyka SQL ponechána beze změny a <xref:System.Linq.Enumerable.Sum%2A> vyhodnocena `null` jako místo nuly pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null.

Omezení SQL pro mezilehlé výsledky se vztahují na agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Počet <xref:System.Linq.Enumerable.Sum%2A> celočíselných hodnot v čísle 32 není počítán pomocí 64 bitových výsledků. Přetečení může nastat pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Sum%2A>překlad, i když standardní implementace operátoru dotazu nezpůsobí přetečení odpovídající posloupnosti v paměti.

`integer` `double`Podobně je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Average%2A> převod celočíselných hodnot vypočítán jako, nikoli jako.

### <a name="entity-arguments"></a>Argumenty entity

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]umožňuje použít typy entit v <xref:System.Linq.Enumerable.GroupBy%2A> metodách a. <xref:System.Linq.Enumerable.OrderBy%2A> V překladu těchto operátorů je použití argumentu typu považováno za ekvivalent pro určení všech členů tohoto typu. Například následující kód je ekvivalentní:

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a>Nejrovnější/porovnatelné argumenty

V implementaci následujících metod je vyžadována rovnost argumentů:

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje rovnost a porovnávání pro *rovné* argumenty, ale ne pro argumenty, které jsou nebo obsahují sekvence. Plochý argument je typ, který lze namapovat na řádek SQL. Projekce jednoho nebo více typů entit, které lze staticky určit, aby neobsahovala sekvenci, je považována za plochý argument.

Následují příklady plochých argumentů:

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

Následují příklady neplochých (hierarchických) argumentů.

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a>Visual Basic překlad funkce

Následující pomocné funkce, které jsou používány kompilátorem Visual Basic, jsou přeloženy do odpovídajících funkcí a operátorů SQL:

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

Metody převodu:

|||||
|-|-|-|-|
|ToBoolean|ToSByte –|ToByte –|ToChar –|
|ToCharArrayRankOne|V tomto|ToDecimal –|ToDouble –|
|ToInteger|ToUInteger|ToLong|ToULong|
|ToShort|ToUShort|ToSingle –|Metodu|

## <a name="inheritance-support"></a>Podpora dědičnosti

### <a name="inheritance-mapping-restrictions"></a>Omezení mapování dědičnosti

Další informace najdete v tématu [jak: Mapování hierarchií](how-to-map-inheritance-hierarchies.md)dědičnosti.

### <a name="inheritance-in-queries"></a>Dědičnost v dotazech

C#přetypování jsou podporovaná jenom v projekci. Přetypování, která jsou používána jinde, nejsou přeložena a jsou ignorována. Z nezávisle na názvech funkcí SQL provádí SQL skutečně pouze ekvivalent modulu CLR (Common Language Runtime <xref:System.Convert>). To znamená, že SQL může změnit hodnotu jednoho typu na jiný. Neexistuje žádný ekvivalent přetypování CLR, protože neexistuje koncept přeinterpretace stejných bitů jako u jiného typu. To je důvod, C# proč přetypování funguje pouze místně. Nejedná se o vzdálenou.

Operátory, `is` `Select` a `as` a`GetType` metody nejsou omezeny na operátor. Je možné je použít také v jiných operátorech dotazu.

## <a name="sql-server-2008-support"></a>SQL Server 2008 Support

Počínaje verzí .NET Framework 3,5 SP1 LINQ to SQL podporuje mapování na nové typy data a času zavedené pomocí SQL Server 2008. Existují však určitá omezení pro operátory LINQ to SQL dotazů, které lze použít při práci s hodnotami mapovanými na tyto nové typy.

### <a name="unsupported-query-operators"></a>Nepodporované operátory dotazů

Následující operátory dotazu nejsou podporovány v hodnotách mapovaných na `DATETIME2`nové SQL Server typy data a času:, `DATE`, `TIME` `DATETIMEOFFSET`a.

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

Další informace o mapování na tyto SQL Server typy data a času naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).

## <a name="sql-server-2005-support"></a>SQL Server 2005 Support

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující funkce SQL Server 2005:

- Uložené procedury napsané pro SQL CLR.

- Uživatelem definovaný typ.

- Funkce dotazů XML.

## <a name="sql-server-2000-support"></a>SQL Server 2000 Support

Následující omezení SQL Server 2000 (v porovnání s Microsoft SQL Server 2005) mají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vliv na podporu.

### <a name="cross-apply-and-outer-apply-operators"></a>Operátory vzájemného použití a vnějšího použití

Tyto operátory nejsou k dispozici v SQL Server 2000. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pokusí se o řadu přepsání, která je nahradí příslušnými spojeními.

`Cross Apply`a `Outer Apply` jsou generovány pro navigaci relací. Sada dotazů, pro které jsou takové přepisy možné, není dobře definována. Z tohoto důvodu je minimální sada dotazů, které jsou podporovány pro SQL Server 2000, sadou, která nezahrnuje navigaci relací.

### <a name="text--ntext"></a>text/ntext

Datové typy `text`  /  `varchar(max)`  / nelze použít v určitých operacích dotazu proti`nvarchar(max)`, které jsou podporovány Microsoft SQL Server 2005. `ntext`

Pro toto omezení není k dispozici žádné řešení. Konkrétně nemůžete použít `Distinct()` na žádný výsledek, který obsahuje členy mapované na `text` nebo `ntext` sloupce.

### <a name="behavior-triggered-by-nested-queries"></a>Chování aktivované vnořenými dotazy

Pořadač SQL Server 2000 (přes SP4) obsahuje některé idiosyncrasies, které se spouštějí ve vnořených dotazech. Sada dotazů SQL, které aktivují tyto idiosyncrasies, není správně definovaná. Z tohoto důvodu nemůžete definovat sadu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazů, které by mohly způsobit SQL Server výjimky.

### <a name="skip-and-take-operators"></a>Přeskočit a převzít operátory

<xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).

## <a name="object-materialization"></a>Materializace objektů

Materializace vytvoří objekty CLR z řádků, které jsou vráceny jedním nebo více dotazy jazyka SQL.

- Následující volání se *spouštějí místně* jako součást materializace:

  - Konstruktory

  - `ToString`metody v projekce

  - Typy přetypování v projekce

- Metody, které následují <xref:System.Linq.Enumerable.AsEnumerable%2A> metodu jsou *spouštěny místně*. Tato metoda nezpůsobí okamžité provedení.

- Můžete použít `struct` jako návratový typ výsledku dotazu nebo jako člen typu výsledku. Entity jsou nutné pro třídy. Anonymní typy jsou materializované jako instance třídy, ale pojmenované struktury (jiné než entity) se dají použít v projekci.

- Člen návratového typu výsledku dotazu může být typu <xref:System.Linq.IQueryable%601>. Je vyhodnocena jako místní kolekce.

- Následující metody způsobují *okamžitou materializaci* sekvence, na kterou jsou metody aplikovány:

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a>Viz také:

- [Referenční informace](reference.md)
- [Vrácení nebo přeskočení prvků v posloupnosti](return-or-skip-elements-in-a-sequence.md)
- [Zřetězení dvou sekvencí](concatenate-two-sequences.md)
- [Vrácení rozdílů množin mezi dvěma sekvencemi](return-the-set-difference-between-two-sequences.md)
- [Vrácení průniku množin mezi dvěma sekvencemi](return-the-set-intersection-of-two-sequences.md)
- [Vrácení sjednocení množin mezi dvěma sekvencemi](return-the-set-union-of-two-sequences.md)
