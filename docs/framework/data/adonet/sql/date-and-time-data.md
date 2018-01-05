---
title: "Datum a čas dat"
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
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a547bbb38d58d5b4c22e78bfd64fef4094865143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="date-and-time-data"></a>Datum a čas dat
SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času. Nové typy dat zahrnují rozšířené datové typy s větší rozsah, přesnost a časové pásmo a samostatné typy pro datum a čas. Počínaje verzí rozhraní .NET Framework 3.5 Service Pack (SP) 1, zprostředkovatel dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje úplnou podporu pro všechny nové funkce databázového stroje SQL Server 2008. Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro použití s SqlClient tyto nové funkce.  
  
 Verze systému SQL Server starších než SQL Server 2008 pouze měl dvě datové typy pro práci s hodnotami data a času: `datetime` a `smalldatetime`. Oba tyto typy dat obsahovat hodnoty data a hodnotu čas, takže je obtížné pracovat pouze data nebo pouze hodnoty času. Tyto datové typy navíc podporují jenom data, ke kterým došlo po zavedení gregoriánský kalendář v Anglii v 1753. Další omezení je, že tyto starší datové typy nejsou časových pásem vědět, který ztěžuje pro práci s daty, která pochází z více časových pásem.  
  
 Kompletní dokumentaci pro datové typy systému SQL Server je k dispozici v SQL Server Books Online. Následující tabulka uvádí základní témata specifické pro verzi pro data a času.  
  
 **SQL Server Books Online**  
  
1.  [Použitím datum a čas dat](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Datum a čas datové typy zavedená v systému SQL Server 2008  
 Následující tabulka popisuje nové datové typy datum a čas.  
  
|Typ dat systému SQL Server|Popis|  
|--------------------------|-----------------|  
|`date`|`date` Datový typ má rozsah 1. ledna 01 do 31. prosince 9999 s přesností na 1 den. Výchozí hodnota je 1. ledna 1900. Velikost úložiště je 3 bajtů.|  
|`time`|`time` Datový typ ukládá pouze hodnoty času ve 24hodinovém formátu. `time` Datový typ má rozsah 00:00:00.0000000 prostřednictvím 23:59:59.9999999 s přesností na 100 nanosekundách. Výchozí hodnota je 00:00:00.0000000 (půlnoc). `time` Uživatelem definované zlomková přesnost pro sekundy podporuje datový typ a velikost úložiště se liší od 3 do 6 bajtů, podle Zadaná přesnost.|  
|`datetime2`|`datetime2` Datový typ kombinuje rozsah a přesnost `date` a `time` typy dat do jednoho datového typu.<br /><br /> Výchozí hodnoty a formáty literálu řetězce jsou stejné jako názvům definovaným v `date` a `time` datové typy.|  
|`datetimeoffset`|`datetimeoffset` Datový typ má všechny funkce `datetime2` s posunem další časové pásmo. Posun v časových pásmech je reprezentován jako [+ &#124;-] hh: mm. HH jsou 2 číslic od 00 do 14, které představují počtem hodin za posun časového pásma. MM je 2 číslic od 00 do 59 představující počet minut, další v posun časového pásma. Podporované jsou formáty času na 100 nanosekundách. Povinné + nebo - přihlašovací Určuje, zda je posun v časových pásmech přidány nebo odečten od času UTC (Universal Time koordinovat nebo greenwichský střední čas) k získání místního času.|  
  
> [!NOTE]
>  Další informace o používání `Type System Version` – klíčové slovo, najdete v části <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Formát data a pořadí v datu  
 Jak analyzuje hodnoty data a času v systému SQL Server závisí nejen na verzi systému typ a verze serveru, ale také na jazyk a formát výchozí nastavení serveru. Řetězec datum, může nerozpoznatelný, pokud dotaz proveden prostřednictvím funguje pro formátování data z jednoho jazyka, který používá jiný jazyk a formát data nastavení.  
  
 Příkaz jazyka Transact-SQL nastavit implicitně nastaví parametr DATEFORMAT, která určuje pořadí částí data. Příkaz nastavit parametr DATEFORMAT Transact-SQL můžete použít na připojení k rozlišení hodnot data podle částí data v formát MDR, DMY, RMD, RDM, MYD nebo DYM pořadí řazení.  
  
 Pokud nezadáte žádné parametr DATEFORMAT pro připojení, SQL Server používá výchozí jazyk přidružené k připojení. Například datum řetězec "01/02/03" by byl interpretován jako formát MDR (2. ledna 2003) na serveru s nastavením jazyka angličtinu Spojených států a jako DMY (1 února 2003) na serveru s nastavením jazyka britské angličtině. Pomocí pravidla konečného roku systému SQL Server, který definuje datum přerušení pro přiřazení hodnoty století je určen v roce. Další informace najdete v tématu [dvě číslice roku konečného možnost](http://go.microsoft.com/fwlink/?LinkId=120473) v SQL Server Books Online.  
  
> [!NOTE]
>  Formát data RDM nepodporuje při převodu z formátu řetězce na `date`, `time`, `datetime2`, nebo `datetimeoffset`.  
  
 Další informace o interpretace data a času v systému SQL Server najdete v tématu [pomocí datum a čas Data](http://go.microsoft.com/fwlink/?LinkID=98361) v SQL Server 2008 Books Online.  
  
## <a name="datetime-data-types-and-parameters"></a>Datum a čas datové typy a parametry  
 Můžete zadat datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jedné z <xref:System.Data.SqlDbType> výčty. Přidané následující výčty <xref:System.Data.SqlDbType> pro podporu nových typů dat Datum a čas.  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  
  
 Můžete také zadat typ <xref:System.Data.SqlClient.SqlParameter> obecně nastavením <xref:System.Data.SqlClient.SqlParameter.DbType%2A> vlastnost `SqlParameter` objekt, který má určitý <xref:System.Data.DbType> hodnota výčtu. Následující hodnoty výčtu jsou přidané do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datové typy:  
  
-   DbType.DateTime2  
  
-   DbType.DateTimeOffset  
  
 Tyto nové výčty doplnit `Date`, `Time`, a `DateTime` výčty, které existovaly v dřívějších verzích rozhraní .NET Framework.  
  
 Typ zprostředkovatele dat .NET Framework objektu parametr je odvozeno z rozhraní .NET Framework typ hodnoty parametru objektu, nebo z `DbType` parametr objektu. Nové <xref:System.Data.SqlTypes> byly zavedeny datové typy pro podporu nových typů dat Datum a čas. Následující tabulka popisuje mapování mezi datem systému SQL Server 2008 a časové datové typy a datové typy CLR.  
  
|Typ dat systému SQL Server|Typ rozhraní .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Datum|System.DateTime|Datum|Datum|  
|čas|System.TimeSpan|Čas|Čas|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|Datový typ DateTimeOffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|Data a času|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Vlastnosti SqlParameter  
 Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy datum a čas.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Získá nebo nastaví, zda je hodnota Null. Hodnota null parametru odešlete na server, je nutné zadat <xref:System.DBNull>, místo `null` (`Nothing` v jazyce Visual Basic). Další informace o hodnoty Null databáze najdete v tématu [zpracování hodnot Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Získá nebo nastaví maximální počet číslic, na které se používá k reprezentování hodnota. Toto nastavení je ignorováno pro datové typy datum a čas.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Získá nebo nastaví počet desetinných míst, na které se pro čas část hodnoty `Time`, `DateTime2`, a `DateTimeOffset`. Výchozí hodnota je 0, což znamená, že je skutečný měřítka odvodit z hodnoty a odesílá na server.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorovat pro datové typy datum a čas.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví hodnotu parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví hodnotu parametru.|  
  
> [!NOTE]
>  Vyvolá výjimku hodnoty času, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Vytváření parametrů  
 Můžete vytvořit <xref:System.Data.SqlClient.SqlParameter> objekt pomocí jeho konstruktoru, nebo jejím přidáním na <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním `Add` metodu <xref:System.Data.SqlClient.SqlParameterCollection>. `Add` Metoda bude trvat jako vstupní argumenty konstruktoru nebo existujícího objektu parametr.  
  
 Další části v tomto tématu obsahují příklady, jak určit datum a čas parametry. Další příklady práce s parametry, najdete v části [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) a [DataAdapter parametry](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Příklad datum  
 Následující fragment kódu ukazuje, jak určit `date` parametr.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a>Příklad čas  
 Následující fragment kódu ukazuje, jak určit `time` parametr.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a>Příklad Datetime2  
 Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částí datum a čas.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a>Příklad DateTimeOffSet  
 Následující fragment kódu ukazuje, jak určit `DateTimeOffSet` parametr s datum, čas a posun časového pásma 0.  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a>AddWithValue  
 Můžete také zadat parametry pomocí `AddWithValue` metodu <xref:System.Data.SqlClient.SqlCommand>, jak ukazuje následující fragment kódu. Ale `AddWithValue` metoda neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Může parametr mapovat `date`, `datetime`, nebo `datetime2` datový typ na serveru. Při práci s novým `datetime` datové typy, musíte explicitně nastavit parametr <xref:System.Data.SqlDbType> vlastnost, která má datový typ instance. Pomocí <xref:System.Data.SqlDbType.Variant> nebo implicitně zadávání hodnot parametru může způsobit problémy s zpětnou kompatibilitu s `datetime` a `smalldatetime` datové typy.  
  
 Následující tabulka uvádí, které `SqlDbTypes` jsou odvozené z které typy CLR:  
  
|Typ CLR|Odvozené SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|Časový interval|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Načítání datum a čas dat  
 Následující tabulka popisuje metody, které slouží k načtení hodnoty data a času v systému SQL Server 2008.  
  
|SqlClient – metoda|Popis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Načte hodnotu zadaného sloupce jako <xref:System.DateTime> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Načte hodnotu zadaného sloupce jako <xref:System.DateTimeOffset> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Vrátí typ, který je základní typ specifický pro zprostředkovatele pro pole. Vrátí stejné typy jako `GetFieldType` pro nové typy datum a čas.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Načte hodnotu pro určený sloupec. Vrátí stejné typy jako `GetValue` pro nové typy datum a čas.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Načte hodnoty v zadaném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Načte hodnotu sloupce jako <xref:System.Data.SqlTypes.SqlString>. <xref:System.InvalidCastException> Dat nemůže být vyjádřena jako v případě `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Načte data pro sloupec jako jeho výchozí `SqlDbType`. Vrátí stejné typy jako `GetValue` pro nové typy datum a čas.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Načte hodnoty v zadaném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Načte hodnotu sloupce jako řetězec, pokud na verzi systému typ nastavena na systém SQL Server 2005. <xref:System.InvalidCastException> v případě dat nemůže být vyjádřena jako řetězec.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Načte hodnotu zadaného sloupce jako <xref:System.TimeSpan> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Načte hodnotu zadaného sloupce jako jeho základní typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Načte hodnoty ve sloupcích v matici.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Vrátí <xref:System.Data.DataTable> metadata sady výsledků dotazu, který popisuje.|  
  
> [!NOTE]
>  Nové datum a čas `SqlDbTypes` nejsou podporovány pro kód, který spouští v procesu v systému SQL Server. Pokud jeden z těchto typů je předán na server, bude vyvolána výjimka.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Zadání hodnoty data a času jako literály.  
 Můžete určit datum a čas typy dat pomocí různých formátech různých řetězcového literálu, kdy SQL Server pak vyhodnotí za běhu, jejich převedení na struktury interní data a času. SQL Server rozpoznal datum a čas data, která je uzavřen v jednoduchých uvozovkách ('). Následující příklady ukazují, některé formáty:  
  
-   Abecední datum formátů, jako například `'October 15, 2006'`.  
  
-   Číselná data formátů, jako například `'10/15/2006'`.  
  
-   Oddělené formáty řetězců, jako například `'20061015'`, který by byl interpretován jako 15. října 2006, pokud používáte formát data standardu ISO.  
  
> [!NOTE]
>  Kompletní dokumentaci můžete najít pro všechny formáty řetězcového literálu a další funkce data a času datových typů v SQL Server Books Online.  
  
 Vyvolá výjimku hodnoty času, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Prostředky v Online knihách SQL Server 2008  
 Další informace o práci se hodnoty data a času v systému SQL Server 2008 najdete v následujících zdrojích v SQL Server 2008 Books Online.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Datum a čas datové typy a funkce (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|Poskytuje přehled o Transact-SQL data a času datové typy a funkce.|  
|[Použitím datum a čas dat](http://go.microsoft.com/fwlink/?LinkId=98361)|Poskytuje informace o datu a času datové typy a funkce a příklady jejich používání.|  
|[Datové typy (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98362)|Popisuje typy dat systému SQL Server 2008.|  
  
## <a name="see-also"></a>Viz také  
 [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
