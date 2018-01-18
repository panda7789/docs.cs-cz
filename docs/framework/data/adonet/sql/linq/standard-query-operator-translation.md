---
title: "Operátor posunutí standardní dotazu"
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
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fc99fea9b722f6c3395f6bade625a09c6e97eb08
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="standard-query-operator-translation"></a>Operátor posunutí standardní dotazu
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Standardní operátory dotazu překládá příkazy SQL. Procesor dotazů databáze určuje sémantika provádění překlad SQL.  
  
 Standardní operátory dotazu jsou definovány proti *pořadí*. Je posloupnost *seřazené* a spoléhá na referenční identity pro každý prvek pořadí. Další informace najdete v tématu [standardní přehled operátory dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Především se týká SQL *neuspořádané sady hodnot*. Řazení je obvykle explicitně stanovené, po zpracování operace, která se použije na poslední výsledek dotazu na místo na mezilehlých výsledků. Identity jsou určené hodnoty. Z toho důvodu jsou dotazy SQL pochopeny jak nakládat s multisets (*obalů*) místo *nastaví*.  
  
 Následující odstavce popisují rozdíly mezi standardní operátory dotazu a jejich překlad SQL pro zprostředkovatele SQL Server pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="operator-support"></a>Podpora – operátor  
  
### <a name="concat"></a>concat  
 <xref:System.Linq.Enumerable.Concat%2A> Metoda je definována pro seřazené multisets, kde pořadí příjemce a pořadí argument identická. <xref:System.Linq.Enumerable.Concat%2A>funguje jako `UNION ALL` přes multisets, za nímž následuje běžné pořadí.  
  
 Posledním krokem je před vytváří výsledky řazení v systému SQL. <xref:System.Linq.Enumerable.Concat%2A>Pořadí argumentů nezachová. Aby odpovídající řazení, musí explicitně řazení výsledků <xref:System.Linq.Enumerable.Concat%2A>.  
  
### <a name="intersect-except-union"></a>Intersect, s výjimkou sjednocení  
 <xref:System.Linq.Enumerable.Intersect%2A> a <xref:System.Linq.Enumerable.Except%2A> metody jsou dobře definované jenom na sady. Sémantika pro multisets není definován.  
  
 <xref:System.Linq.Enumerable.Union%2A> Metoda je definována pro multisets jako neuspořádaný zřetězení multisets (efektivně výsledek klauzuli UNION ALL v systému SQL).  
  
### <a name="take-skip"></a>Proveďte přeskočit  
 <xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> metody jsou dobře definované pouze proti *seřazené sady*. Pro multisets nebo Neseřazený sady sémantiky není definován.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když jsou použity v dotazy pro SQL Server 2000. Další informace najdete v tématu "Přeskočit a trvat výjimky v systému SQL Server 2000" položky v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 Z důvodu omezení na pořadí v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argument z těchto metod na výsledek metody. Například vezměte v úvahu následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu:  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 Vygenerovaný SQL pro tento kód přesune řazení na konec následujícím způsobem:  
  
```  
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
  
 Je zřejmé, že všechny zadané pořadí musí být konzistentní při <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou zřetězen dohromady. Jinak výsledky nejsou definovány.  
  
 Obě <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou dobře definovaný nezáporné, konstantní integrální argumenty, které jsou na základě specifikace standardní – operátor dotazu.  
  
### <a name="operators-with-no-translation"></a>Operátory s žádné překlad  
 Následující metody nejsou přeložen [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Nejčastější příčinou je rozdíl mezi Neseřazený multisets a pořadí.  
  
|Operátory|Logický základ hlediska|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Dotazy SQL pracovat multisets, nikoli na pořadí. `ORDER BY`musí být poslední klauzule použita výsledky. Z tohoto důvodu není žádná pro obecné účely překladu pro tyto dvě metody.|  
|<xref:System.Linq.Enumerable.Reverse%2A>|Překlad tuto metodu je možné, seřazené sady, ale není aktuálně přeložit pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Je možné, seřazené sady překlad z těchto metod, ale není aktuálně přeložit pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Dotazy SQL pracovat multisets, nikoli na indexovanou pořadí.|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>(přetížení s arg výchozí)|Obecně platí nelze zadat výchozí hodnotu pro libovolné řazené kolekce členů. Je možné v některých případech prostřednictvím vnější spojení, hodnoty Null pro řazené kolekce členů.|  
  
## <a name="expression-translation"></a>Překlad výrazu  
  
### <a name="null-semantics"></a>Sémantika hodnotu Null.  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepředstavuje porovnání null sémantiku SQL. Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL. Z tohoto důvodu projeví sémantiky sémantiku SQL, která jsou definována v nastavení serveru nebo připojení. Například dvě hodnoty null považovány za nerovné pod výchozí nastavení serveru SQL, ale můžete změnit nastavení můžete změnit sémantiky. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nebere v úvahu nastavení serveru při jeho překládá dotazy.  
  
 Porovnání s literál null je přeložená na příslušnou verzi SQL (`is null` nebo `is not null`).  
  
 Hodnota `null` v kolaci je definovaný systémem SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nedojde ke změně kolace.  
  
### <a name="aggregates"></a>Agregace  
 Metoda aggregate standardní – operátor dotazu <xref:System.Linq.Enumerable.Sum%2A> vyhodnotí na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechána beze změny, a <xref:System.Linq.Enumerable.Sum%2A> vyhodnocuje `null` místo nula pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null.  
  
 Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Linq.Enumerable.Sum%2A> z 32bitové celé číslo není počítaný počty pomocí 64-bit výsledky. Přetečení mohou vyskytovat u [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Sum%2A>i v případě implementace standardní – operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.  
  
 Podobně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Average%2A> z celé číslo hodnoty se vypočítávají jako `integer`, ne jako `double`.  
  
### <a name="entity-arguments"></a>Argumenty entity  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Umožňuje typy entit, který se má použít v <xref:System.Linq.Enumerable.GroupBy%2A> a <xref:System.Linq.Enumerable.OrderBy%2A> metody. V překladu tyto operátory použití argument typu považován za ekvivalentní k určení všech členů tohoto typu. Například následující kód je ekvivalentní:  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>Equatable / porovnatelný z hlediska argumenty  
 Porovnávání argumentů je nezbytné k implementaci z následujících metod:  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje rovnosti a porovnání pro *ploché* argumenty, ale ne pro argumenty, které jsou nebo obsahují pořadí. Ploché argument je typu, který může být namapovaná na řádek, SQL. Projekce jeden nebo více typů entit, které lze určit staticky neobsahují sekvenci považuje za plochý argument.  
  
 Následují příklady ploché argumenty:  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 Následují příklady argumentů jiný dvojrozměrném (hierarchické).  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Překlad funkce jazyka Visual Basic  
 Následující pomocných funkcí, které jsou používány Visual Basic – kompilátor jsou převedeny na odpovídající operátory jazyka SQL a funkce:  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 Převod metody:  
  
|||||  
|-|-|-|-|  
|ToBoolean|ToSByte|ToByte|ToChar|  
|ToCharArrayRankOne|ToDate|ToDecimal|ToDouble|  
|ToInteger|ToUInteger|ToLong|ToULong|  
|ToShort|ToUShort|ToSingle|ToString|  
  
## <a name="inheritance-support"></a>Podpora dědičnosti  
  
### <a name="inheritance-mapping-restrictions"></a>Omezení pro mapování dědičnosti  
 Další informace najdete v tématu [postupy: mapování hierarchie dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
### <a name="inheritance-in-queries"></a>Dědičnost v dotazech.  
 Přetypování C# jsou podporovány pouze v projekci. Přetypování, které se používají jinde nejsou přeložit a budou ignorovány. Kromě zajištění dostatečného SQL funkce názvy SQL skutečně pouze provede ekvivalent common language runtime (CLR) <xref:System.Convert>. To znamená SQL, můžete změnit hodnoty jednoho typu do jiného. Není žádný ekvivalent přetypování, protože neexistuje žádná koncepce nový výklad stejné bits jako jiný typ CLR. To je důvod, proč C# převést lze pouze místně. Není používat vzdáleně.  
  
 Operátory, `is` a `as`a `GetType` metoda nejsou omezeni `Select` operátor. Použitím v jiné operátory dotazu také.  
  
## <a name="sql-server-2008-support"></a>SQL Server 2008 Support  
 Od verze rozhraní .NET Framework 3.5 SP1, technologie LINQ to SQL podporuje mapování na nové datum a čas typy, které se poprvé objevila v systému SQL Server 2008. Ale existují určitá omezení pro LINQ to SQL operátory dotazu, které můžete použít při fungování s hodnotami, které jsou namapované na tyto nové typy.  
  
### <a name="unsupported-query-operators"></a>Operátory nepodporované dotazu  
 Následující operátory dotazu nejsou podporovány na hodnotách, které jsou namapované na nové typy datum a čas systému SQL Server: `DATETIME2`, `DATE`, `TIME`, a `DATETIMEOFFSET`.  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 Další informace o mapování pro tyto typy datum a čas systému SQL Server najdete v tématu [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="sql-server-2005-support"></a>SQL Server 2005 Support  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje následující funkce SQL Server 2005:  
  
-   Uložené procedury napsané pro SQL CLR.  
  
-   Uživatelem definovaný typ.  
  
-   Funkce dotazů XML.  
  
## <a name="sql-server-2000-support"></a>SQL Server 2000 Support  
 Následující [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] omezení (ve srovnání s [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Křížové použít a vnější použít operátory  
 Nejsou k dispozici v těchto operátorů [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]se pokusí řadu přepisů nahradili odpovídající spojení.  
  
 `Cross Apply`a `Outer Apply` jsou generovány pro navigaci relace. Sada dotazů, pro které je možné taková přepisů není dobře definované. Z tohoto důvodu minimální sadu dotazy, které je podporováno pro [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] je sada, který nezahrnuje vztah navigace.  
  
### <a name="text--ntext"></a>text / ntext  
 Datové typy `text`  /  `ntext` nelze použít v určité operace dotazů vůči `varchar(max)`  /  `nvarchar(max)`, který podporuje [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].  
  
 Žádné řešení, je k dispozici pro toto omezení. Konkrétně, nemůžete použít `Distinct()` na žádný výsledek, který obsahuje členy, které jsou mapované na `text` nebo `ntext` sloupce.  
  
### <a name="behavior-triggered-by-nested-queries"></a>Chování aktivovány vnořené dotazy  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)](prostřednictvím SP4) má vazač některá specifika, které jsou aktivovány vnořené dotazy. Sada dotazy SQL, která aktivuje tyto specifika není dobře definované. Z tohoto důvodu nelze definovat sadu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy, které by mohly způsobit výjimky serveru SQL Server.  
  
### <a name="skip-and-take-operators"></a>Přeskočit a trvat operátory  
 <xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když se používají v dotazech proti [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. Další informace najdete v tématu "Přeskočit a trvat výjimky v systému SQL Server 2000" položky v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="object-materialization"></a>Objekt Materialization  
 Vlastnost materialization vytvoří objekty CLR z řádků, které jsou vráceny dotazy SQL pro jeden nebo více.  
  
-   Následující volání jsou *provést místně* jako součást materialization:  
  
    -   Konstruktory  
  
    -   `ToString`metody v projekce  
  
    -   Přetypování typu v projekce  
  
-   Metody, které následují <xref:System.Linq.Enumerable.AsEnumerable%2A> metoda jsou *provést místně*. Tato metoda nezpůsobí okamžité spuštění.  
  
-   Můžete použít `struct` jako návratový typ výsledku dotazu nebo jako člen skupiny typ výsledku. Entit musí být třídy. Anonymní typy jsou vyhodnocena jako instance třídy, ale s názvem struktury (bez entity) mohou být používány projekce.  
  
-   Členem návratový typ výsledku dotazu může být typu <xref:System.Linq.IQueryable%601>. Ho je vyhodnocena jako místní kolekce.  
  
-   Následující metody způsobit, že *okamžitou materialization* pořadí, které se použijí metody pro:  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Vrácení nebo přeskočení prvků v posloupnosti](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 [Zřetězení dvou sekvencí](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 [Vrácení rozdílů množin mezi dvěma sekvencemi](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 [Vrácení průniku množin mezi dvěma sekvencemi](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 [Vrácení sjednocení množin mezi dvěma sekvencemi](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
