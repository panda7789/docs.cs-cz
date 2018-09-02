---
title: Převod standardních operátorů dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: fb4910e48af58463c5c851173f8e3caf4594cc3a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424227"
---
# <a name="standard-query-operator-translation"></a>Převod standardních operátorů dotazů
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Standardní operátory dotazu se přeloží na příkazy jazyka SQL. Procesor dotazů databáze určuje sémantika provádění SQL překladu.  
  
 Standardní operátoři dotazu jsou definováni proti *pořadí*. Sekvence je *seřazené* a spoléhá na referenční identitě pro každý prvek pořadí. Další informace najdete v tématu [přehled standardních operátorů dotazu](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 SQL se především se týká *neuspořádaná sady hodnot*. Řazení je obvykle výslovně uvedeno, následné zpracování operace, která se použije na výsledek dotazu, nikoli mezilehlých výsledků. Identita je definovaná pomocí hodnoty. Z tohoto důvodu jsou dotazy SQL pochopitelné řešit multisets (*kontejnery objektů a dat*) namísto *nastaví*.  
  
 Následující odstavce popisují rozdíly mezi standardní operátory dotazu a jejich překlad SQL pro zprostředkovatel SQL Server pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="operator-support"></a>Podpora – operátor  
  
### <a name="concat"></a>concat  
 <xref:System.Linq.Enumerable.Concat%2A> Metoda je definována pro uspořádaný multisets, kde příjemce a pořadím argumentu shodují. <xref:System.Linq.Enumerable.Concat%2A> funguje jako `UNION ALL` přes multisets, za nímž následuje běžné pořadí.  
  
 Posledním krokem je řazení SQL předtím, než se produkují výsledky. <xref:System.Linq.Enumerable.Concat%2A> Nezachovávat hodnotu pořadí z jejích argumentů. Aby odpovídající řazení, musí explicitně řazení výsledků <xref:System.Linq.Enumerable.Concat%2A>.  
  
### <a name="intersect-except-union"></a>Intersect, s výjimkou sjednocení  
 <xref:System.Linq.Enumerable.Intersect%2A> a <xref:System.Linq.Enumerable.Except%2A> metody jsou pouze na sady dobře definované. Sémantika pro multisets není definován.  
  
 <xref:System.Linq.Enumerable.Union%2A> Je definována metoda pro multisets jako Neseřazený zřetězení multisets (efektivně výsledek klauzuli UNION ALL v SQL).  
  
### <a name="take-skip"></a>Take, Skip  
 <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> metody jsou dobře definované pouze proti *seřazené sady*. Sémantika pro Neseřazený sady nebo multisets nejsou definovány.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když se používají v dotazech pro SQL Server 2000. Další informace najdete v tématu "Přeskočit a převzít výjimky v systému SQL Server 2000" položka v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 Z důvodu omezení řazení SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argument z těchto metod na výsledek metody. Představte si třeba následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu:  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 Vygenerovaný SQL pro tento kód přesune řazení do konce a následujícím způsobem:  
  
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
  
 Je zřejmé, že všechny zadané řazení musí být konzistentní při <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou zřetězen dohromady. V opačném případě nejsou výsledky definovány.  
  
 Obě <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> jsou jasně definované pro záporná, konstantní celočíselné argumenty, které jsou založené na specifikaci standardního operátoru dotazu.  
  
### <a name="operators-with-no-translation"></a>Operátory se žádný překlad  
 Následující metody nepřekládá podle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Nejběžnějším důvodem je rozdíl mezi Neseřazený multisets a pořadí.  
  
|Operátory|Důvody|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Dotazy SQL pracují s multisets, ne podle pořadí. `ORDER BY` je nutné poslední klauzule použít na výsledky. Z tohoto důvodu neexistuje žádný překlad pro obecné účely pro tyto dvě metody.|  
|<xref:System.Linq.Enumerable.Reverse%2A>|Překlad tuto metodu je možné seřazené sady, ale není aktuálně přeložit modulem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Převod z těchto metod je možné seřazené sady, ale není aktuálně přeložit modulem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Dotazy SQL pracují s multisets, ne na indexovanou pořadí.|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (přetížení s výchozí argument)|Obecně platí nelze zadat výchozí hodnotu pro libovolný záznam. Hodnoty Null pro řazené kolekce členů je možné v některých případech prostřednictvím vnější spojení.|  
  
## <a name="expression-translation"></a>Výraz posunutí  
  
### <a name="null-semantics"></a>Sémantika s hodnotou Null  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepředstavuje sémantiku porovnání null v SQL. Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL. Z tohoto důvodu odrážet sémantiku sémantiku SQL, který se definuje na základě nastavení serveru nebo připojení. Například dvě hodnoty null se považují za nestejné podle výchozího nastavení systému SQL Server, ale můžete změnit nastavení, chcete-li změnit sémantiku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nebere v úvahu nastavení serveru při překládá dotazy.  
  
 Porovnání s literál null se přeloží na odpovídající verzi SQL (`is null` nebo `is not null`).  
  
 Hodnota `null` kolace je určené systému SQL Server. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nedojde ke změně kolace.  
  
### <a name="aggregates"></a>Agregace  
 Metoda standardního operátoru dotazu aggregate <xref:System.Linq.Enumerable.Sum%2A> vyhodnocen jako nula k prázdné sekvenci nebo sekvenci, která obsahuje pouze hodnoty Null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechány beze změny, a <xref:System.Linq.Enumerable.Sum%2A> vyhodnotí jako `null` místo nula k prázdné sekvenci nebo sekvenci, která obsahuje pouze hodnoty Null.  
  
 Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Linq.Enumerable.Sum%2A> 32-bit integer není počítaný množství pomocí 64-bit výsledky. Přetečení může dojít k pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Sum%2A>i v případě implementace standardní operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.  
  
 Podobně [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad <xref:System.Linq.Enumerable.Average%2A> celého čísla je vypočítán hodnoty jako `integer`, ne jako `double`.  
  
### <a name="entity-arguments"></a>Argumenty entity  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Umožňuje typy entit, který se má použít v <xref:System.Linq.Enumerable.GroupBy%2A> a <xref:System.Linq.Enumerable.OrderBy%2A> metody. V překladu těchto operátorů použijte argument typu je považovány za ekvivalentní se zadáním všechny členy tohoto typu. Například následující kód je ekvivalentní:  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>Equatable / srovnatelné argumenty  
 Rovnost hodnoty argumentů se vyžaduje k provedení následujících metod:  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje rovnosti a porovnání pro *plochý* argumenty, ale ne pro argumenty, které jsou nebo obsahovat sekvence. Plochý argumentu je typ, který je možné mapovat na řádku SQL. Projekce jednoho nebo více typů entit, které se dá určit staticky neobsahují sekvenci se považuje za argumentem bez stromové struktury.  
  
 Následuje několik příkladů argumentů bez stromové struktury:  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 Následují příklady argumenty jiných ploché (hierarchické).  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Funkce převodu jazyka Visual Basic  
 Následující pomocná funkce, které se používají v kompilátoru jazyka Visual Basic jsou přeloženy na odpovídající SQL operátory a funkce:  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 Převod metody:  
  
|||||  
|-|-|-|-|  
|ToBoolean|Tosbyte –|Tobyte –|Tochar –|  
|ToCharArrayRankOne|Do data|Todecimal –|Todouble –|  
|ToInteger|ToUInteger|ToLong|ToULong|  
|ToShort|ToUShort|Tosingle –|ToString|  
  
## <a name="inheritance-support"></a>Podpora dědičnosti  
  
### <a name="inheritance-mapping-restrictions"></a>Omezení pro mapování dědičnosti  
 Další informace najdete v tématu [postupy: mapování hierarchií dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
### <a name="inheritance-in-queries"></a>Dědičnost v dotazech  
 Přetypování C# jsou podporovány pouze v projekci. Přetypování, které se používají jinde nepřekládá a budou ignorovány. Kromě SQL názvy funkcí, SQL ve skutečnosti provádí pouze ekvivalent modulu common language runtime (CLR) <xref:System.Convert>. To znamená SQL, můžete změnit hodnoty jednoho typu na jiný. Neexistuje žádný ekvivalent přetypování, protože neexistuje žádný koncept opětovná interpretace bity stejné jako u jiného typu CLR. To je důvod, proč a C# přetypování funguje jenom místně. Není vzdálený.  
  
 Operátory, `is` a `as`a `GetType` metoda nejsou omezeni `Select` operátor. Jejich lze použít v jiných operátorů dotazu také.  
  
## <a name="sql-server-2008-support"></a>Podpora serveru SQL Server 2008  
 Počínaje rozhraním .NET Framework 3.5 SP1, LINQ to SQL podporuje mapování na nové datum a čas typy zavedena v systému SQL Server 2008. Existují ale určitá omezení do technologie LINQ to SQL operátorů dotazu, které můžete použít při práci s hodnotami, které jsou namapované na tyto nové typy.  
  
### <a name="unsupported-query-operators"></a>Dotaz se nepodporuje operátory  
 Následující operátory dotazu nejsou podporovány u hodnot, které jsou namapované na nové typy data a času systému SQL Server: `DATETIME2`, `DATE`, `TIME`, a `DATETIMEOFFSET`.  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 Další informace o mapování pro tyto typy data a času systému SQL Server najdete v tématu [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="sql-server-2005-support"></a>Podpora SQL serveru 2005  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nepodporuje následující funkce SQL Server 2005:  
  
-   Uložené procedury napsané pro SQL CLR.  
  
-   Uživatelem definovaného typu.  
  
-   Funkce dotazu XML.  
  
## <a name="sql-server-2000-support"></a>Podpora serveru SQL Server 2000  
 Následující [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] omezení (ve srovnání s [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) ovlivnit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporovat.  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Křížové použití a vnější použít operátory  
 Tyto operátory nejsou k dispozici v [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí řadu přepisů pro jejich nahrazení odpovídající spojení.  
  
 `Cross Apply` a `Outer Apply` jsou generovány pro navigaci vztah. Sadu dotazů, pro které je možné takové přepisů není dobře definováno. Z tohoto důvodu minimální sadu dotazů, které je podporováno pro [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] je sada, která nezahrnuje vztah navigace.  
  
### <a name="text--ntext"></a>text / ntext  
 Datové typy `text`  /  `ntext` nelze použít v určité operace dotazů vůči `varchar(max)`  /  `nvarchar(max)`, které jsou podporovány [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].  
  
 Žádné řešení, protože je k dispozici pro toto omezení. Konkrétně byste měli nelze použít `Distinct()` na některý z výsledků, který obsahuje členy, které jsou mapovány na `text` nebo `ntext` sloupce.  
  
### <a name="behavior-triggered-by-nested-queries"></a>Chování aktivuje vnořené dotazy  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] (prostřednictvím SP4) má vazač některá specifika, které jsou aktivovány vnořené dotazy. Sadu dotazů SQL, který spouští tyto specifika není dobře definováno. Z tohoto důvodu nelze definovat sadu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy, které může způsobit, že výjimky serveru SQL Server.  
  
### <a name="skip-and-take-operators"></a>Přeskočit a převzít operátory  
 <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když se používají v dotazech proti [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. Další informace najdete v tématu "Přeskočit a převzít výjimky v systému SQL Server 2000" položka v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="object-materialization"></a>Materializace objektů  
 Materializace vytvoří objekty CLR z řádků, které jsou vráceny dotazy SQL jeden nebo více.  
  
-   Následující volání jsou *spuštěn lokálně* jako součást materializace:  
  
    -   Konstruktory  
  
    -   `ToString` metody v projekce  
  
    -   Přetypování typu v projekce  
  
-   Metody, které následují <xref:System.Linq.Enumerable.AsEnumerable%2A> metodu *spuštěn lokálně*. Tato metoda nezpůsobí okamžité spuštění.  
  
-   Můžete použít `struct` jako návratový typ výsledku dotazu, nebo jako člen typu výsledku. Entity jsou musí být třídy. Anonymní typy jsou vyhodnocena jako instance třídy, ale pojmenované struktury (jiné entity) lze použít v projekci.  
  
-   Člen návratový typ výsledku dotazu nemůže být typu <xref:System.Linq.IQueryable%601>. Je vyhodnocena jako místní kolekce.  
  
-   Následující metody způsobit, že *okamžité materializace* sekvence, která se použijí metody pro:  
  
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
