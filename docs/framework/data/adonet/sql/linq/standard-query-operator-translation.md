---
title: Převod standardních operátorů dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: af22b6a895fef8037eb5c069ffb7cb23d1333531
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833685"
---
# <a name="standard-query-operator-translation"></a>Převod standardních operátorů dotazů

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá standardní operátory dotazu na příkazy SQL. Procesor dotazů databáze určuje sémantiku provádění překladu SQL.

Standardní operátory dotazu jsou definovány pro *sekvence*. Sekvence je *seřazena* a spoléhá na referenční identitu pro každý prvek sekvence. Další informace najdete v tématu Přehled [standardních operátorů dotazůC#()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [standardní operátory dotazu (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

SQL slouží hlavně pro *neuspořádané sady hodnot*. Řazení je obvykle výslovně uvedeno, operace následného zpracování, která je použita na konečný výsledek dotazu, nikoli na mezilehlé výsledky. Identita je definována hodnotami. Z tohoto důvodu jsou dotazy SQL srozumitelné pro práci s více sadami (*penalt*) místo *sad*.

Následující odstavce popisují rozdíly mezi standardními operátory dotazů a jejich překladem SQL pro poskytovatele SQL Server pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

## <a name="operator-support"></a>Podpora operátorů

### <a name="concat"></a>spojuje

Metoda <xref:System.Linq.Enumerable.Concat%2A> je definována pro seřazené množiny, kde pořadí přijímače a pořadí argumentu jsou stejné. <xref:System.Linq.Enumerable.Concat%2A> funguje jako `UNION ALL` nad více sadami následovaným běžným pořadím.

Poslední krok je seřazen v SQL před vytvořením výsledků. <xref:System.Linq.Enumerable.Concat%2A> nezachovává pořadí argumentů. Aby bylo zajištěno vhodné řazení, je nutné explicitně seřadit výsledky <xref:System.Linq.Enumerable.Concat%2A>.

### <a name="intersect-except-union"></a>Průsečík, s výjimkou sjednocení

Metody <xref:System.Linq.Enumerable.Intersect%2A> a <xref:System.Linq.Enumerable.Except%2A> jsou dobře definovány pouze pro sady. Sémantika pro více sad není definována.

Metoda <xref:System.Linq.Enumerable.Union%2A> je definována pro množiny jako neuspořádané zřetězení množin (efektivně výsledek klauzule UNION ALL v SQL).

### <a name="take-skip"></a>Vzít, přeskočit

metody <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou dobře definovány pouze proti *seřazeným sadám*. Sémantika pro neuspořádané sady nebo více sad není definována.

> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).

Z důvodu omezení řazení v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí přesunout pořadí argumentů těchto metod do výsledku metody. Zvažte například následující dotaz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:

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

Je zřejmé, že všechna zadaná řazení musí být konzistentní, když <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> zřetězené. V opačném případě nejsou výsledky definovány.

@No__t-0 a <xref:System.Linq.Enumerable.Skip%2A> jsou dobře definovány pro nezáporné, konstantní celočíselné argumenty založené na standardní specifikaci operátoru dotazu.

### <a name="operators-with-no-translation"></a>Operátory bez překladu

Následující metody nejsou přeloženy pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Nejběžnějším důvodem je rozdíl mezi neseřazenými množinami a sekvencemi.

|Operátory|Dobře chápete důvody|
|---------------|---------------|
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Dotazy SQL pracují s více sadami, nikoli v sekvencích. `ORDER BY` musí být poslední klauzulí použitou pro výsledky. Z tohoto důvodu neexistuje žádný překlad pro obecné účely těchto dvou metod.|
|<xref:System.Linq.Enumerable.Reverse%2A>|Překlad této metody je možný pro seřazenou sadu, ale aktuálně není přeložen pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Překlad těchto metod je možný pro seřazenou sadu, ale aktuálně není přeložen pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Dotazy SQL pracují s více sadami, nikoli s indexovanými sekvencemi.|
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (Overload s výchozím ARG)|Obecně platí, že u libovolné řazené kolekce členů nejde zadat výchozí hodnotu. Hodnoty null pro řazené kolekce členů jsou možné v některých případech prostřednictvím vnějších spojení.|

## <a name="expression-translation"></a>Překlad výrazu

### <a name="null-semantics"></a>Sémantika null

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] neukládá sémantiku porovnání s hodnotou null na SQL. Operátory porovnání jsou syntakticky přeloženy na jejich ekvivalenty SQL. Z tohoto důvodu sémantika odráží sémantiku SQL, která je definovaná nastavením serveru nebo připojení. Například dvě hodnoty null se považují za neshodné s výchozím SQL Server nastavením, ale můžete změnit nastavení pro změnu sémantiky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nebere v úvahu nastavení serveru při překládání dotazů.

Porovnání s literálem null je přeloženo na odpovídající verzi SQL (`is null` nebo `is not null`).

Hodnota `null` v kolaci je definována SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemění kolaci.

### <a name="aggregates"></a>Agregace

Standardní metoda operátoru dotazu <xref:System.Linq.Enumerable.Sum%2A> vyhodnocuje jako prázdnou sekvenci nulu nebo sekvenci, která obsahuje pouze hodnoty null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jsou sémantika SQL ponechána beze změny a <xref:System.Linq.Enumerable.Sum%2A> se vyhodnotí jako `null` místo nuly pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null.

Omezení SQL pro mezilehlé výsledky platí pro agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. @No__t-0 32 celočíselných hodnot se nepočítá pomocí 64 bitových výsledků. Přetečení může nastat pro přetečení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Sum%2A>, i když standardní implementace operátoru dotazu nezpůsobí přetečení odpovídající posloupnosti v paměti.

Podobně je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Average%2A> celočíselných hodnot počítaný jako `integer`, nikoli jako `double`.

### <a name="entity-arguments"></a>Argumenty entity

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] povolí použití typů entit v metodách <xref:System.Linq.Enumerable.GroupBy%2A> a <xref:System.Linq.Enumerable.OrderBy%2A>. V překladu těchto operátorů je použití argumentu typu považováno za ekvivalent pro určení všech členů tohoto typu. Například následující kód je ekvivalentní:

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a>Nejrovnější/porovnatelné argumenty

V implementaci následujících metod je vyžadována rovnost argumentů:

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje rovnost a porovnávání pro *rovné* argumenty, ale ne pro argumenty, které jsou nebo obsahují sekvence. Plochý argument je typ, který lze namapovat na řádek SQL. Projekce jednoho nebo více typů entit, které lze staticky určit, aby neobsahovala sekvenci, je považována za plochý argument.

Následují příklady plochých argumentů:

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

Následují příklady neplochých (hierarchických) argumentů:

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

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

Další informace najdete v tématu [Postupy: mapování hierarchií dědičnosti](how-to-map-inheritance-hierarchies.md).

### <a name="inheritance-in-queries"></a>Dědičnost v dotazech

C#přetypování jsou podporovaná jenom v projekci. Přetypování, která jsou používána jinde, nejsou přeložena a jsou ignorována. Z nezávisle na názvech funkcí SQL provádí SQL skutečně pouze ekvivalent modulu CLR (Common Language Runtime) <xref:System.Convert>. To znamená, že SQL může změnit hodnotu jednoho typu na jiný. Neexistuje žádný ekvivalent přetypování CLR, protože neexistuje koncept přeinterpretace stejných bitů jako u jiného typu. To je důvod, C# proč přetypování funguje pouze místně. Nejedná se o vzdálenou.

Operátory, `is` a `as` a metoda `GetType` nejsou omezeny na operátor `Select`. Je možné je použít také v jiných operátorech dotazu.

## <a name="sql-server-2008-support"></a>Podpora SQL Server 2008

Počínaje verzí .NET Framework 3,5 SP1 LINQ to SQL podporuje mapování na nové typy data a času zavedené pomocí SQL Server 2008. Existují však určitá omezení pro operátory LINQ to SQL dotazů, které lze použít při práci s hodnotami mapovanými na tyto nové typy.

### <a name="unsupported-query-operators"></a>Nepodporované operátory dotazů

Následující operátory dotazu nejsou podporovány u hodnot namapovaných na nové SQL Server typy data a času: `DATETIME2`, `DATE`, `TIME` a `DATETIMEOFFSET`.

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

Další informace o mapování na tyto SQL Server typy data a času naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).

## <a name="sql-server-2005-support"></a>Podpora SQL Server 2005

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje následující funkce SQL Server 2005:

- Uložené procedury napsané pro SQL CLR.

- Uživatelem definovaný typ.

- Funkce dotazů XML.

## <a name="sql-server-2000-support"></a>Podpora SQL Server 2000

Následující omezení SQL Server 2000 (v porovnání s Microsoft SQL Server 2005) ovlivňují podporu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].

### <a name="cross-apply-and-outer-apply-operators"></a>Operátory vzájemného použití a vnějšího použití

Tyto operátory nejsou k dispozici v SQL Server 2000. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí o řadu přepsání, aby je nahradila příslušnými spojeními.

`Cross Apply` a `Outer Apply` jsou generovány pro navigační vztahy. Sada dotazů, pro které jsou takové přepisy možné, není dobře definována. Z tohoto důvodu je minimální sada dotazů, které jsou podporovány pro SQL Server 2000, sadou, která nezahrnuje navigaci relací.

### <a name="text--ntext"></a>text/ntext

Datové typy `text` @ no__t-1 @ no__t-2 nelze použít v některých operacích dotazu proti `varchar(max)` @ no__t-4 @ no__t-5, které jsou podporovány Microsoft SQL Server 2005.

Pro toto omezení není k dispozici žádné řešení. Konkrétně nemůžete použít `Distinct()` u všech výsledků, které obsahují členy namapované na `text` nebo `ntext` sloupce.

### <a name="behavior-triggered-by-nested-queries"></a>Chování aktivované vnořenými dotazy

Pořadač SQL Server 2000 (přes SP4) obsahuje některé idiosyncrasies, které se spouštějí ve vnořených dotazech. Sada dotazů SQL, které aktivují tyto idiosyncrasies, není správně definovaná. Z tohoto důvodu nelze definovat sadu dotazů [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], které by mohly způsobit SQL Server výjimky.

### <a name="skip-and-take-operators"></a>Přeskočit a převzít operátory

<xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000. Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).

## <a name="object-materialization"></a>Materializace objektů

Materializace vytvoří objekty CLR z řádků, které jsou vráceny jedním nebo více dotazy jazyka SQL.

- Následující volání se *spouštějí místně* jako součást materializace:

  - Konstruktory

  - metody `ToString` v projekce

  - Typy přetypování v projekce

- Metody, které následují metodu <xref:System.Linq.Enumerable.AsEnumerable%2A>, jsou *spouštěny místně*. Tato metoda nezpůsobí okamžité provedení.

- Jako návratový typ výsledku dotazu můžete použít `struct` nebo jako člen typu výsledku. Entity jsou nutné pro třídy. Anonymní typy jsou materializované jako instance třídy, ale pojmenované struktury (jiné než entity) se dají použít v projekci.

- Člen návratového typu výsledku dotazu může být typu <xref:System.Linq.IQueryable%601>. Je vyhodnocena jako místní kolekce.

- Následující metody způsobují *okamžitou materializaci* sekvence, na kterou jsou metody aplikovány:

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a>Viz také:

- [Reference](reference.md)
- [Vrácení nebo přeskočení prvků v posloupnosti](return-or-skip-elements-in-a-sequence.md)
- [Zřetězení dvou sekvencí](concatenate-two-sequences.md)
- [Vrácení rozdílů množin mezi dvěma sekvencemi](return-the-set-difference-between-two-sequences.md)
- [Vrácení průniku množin mezi dvěma sekvencemi](return-the-set-intersection-of-two-sequences.md)
- [Vrácení sjednocení množin mezi dvěma sekvencemi](return-the-set-union-of-two-sequences.md)
