---
title: Kalendářní a časová data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: f93f215f7be27196217fd506796fd58c4e11d796
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619188"
---
# <a name="date-and-time-data"></a>Kalendářní a časová data
SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času. Nové datové typy zahrnují rozšířené datové typy s větší rozsah, přesnost a časové pásmo a samostatné typy pro datum a čas. Od verze rozhraní .NET Framework 3.5 Service Pack (SP) 1, zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008. Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro použití těchto nových funkcí s SqlClient.  
  
 Verze systému SQL Server starších než SQL Server 2008 platili jen dva datové typy pro práci s hodnotami data a času: `datetime` a `smalldatetime`. Oba tyto typy dat obsahovat hodnotu data a hodnotu času, které je těžké pracovat pouze datum nebo pouze hodnoty času. Tyto typy dat také podporují jenom data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v 1753. Další omezení je, že tyto starší typy dat nejsou časového pásma vědět, které je těžké pracovat s daty, která pochází z více časových pásem.  
  
 Úplnou dokumentaci pro datové typy serveru SQL Server je k dispozici v SQL Server Books Online. V následující tabulce jsou uvedeny základní témata specifické pro verzi pro data a času.  
  
 **SQL Server Books Online**  
  
1. [Pomocí kalendářní a časová Data](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Datum a čas datové typy zavedena v systému SQL Server 2008  
 Následující tabulka popisuje nové datové typy data a času.  
  
|Datový typ SQL serveru|Popis|  
|--------------------------|-----------------|  
|`date`|`date` Datový typ má rozsah od 1. ledna, 01 do 31. prosince 9999 s přesností na 1 den. Výchozí hodnota je 1. ledna 1900. Velikost úložiště je 3 bajtů.|  
|`time`|`time` Datový typ ukládá časové hodnoty, podle 24 hodin. `time` Typ dat nabízí řadu 00:00:00.0000000 prostřednictvím 23:59:59.9999999 s přesností na 100 nanosekund. Výchozí hodnota je 00:00:00.0000000 (půlnoc). `time` Podporuje uživatelem definované zlomková přesnost pro sekundy datový typ a velikost úložiště se liší od 3 do 6 bajtů podle Zadaná přesnost.|  
|`datetime2`|`datetime2` Datový typ kombinuje rozsah a přesnost `date` a `time` datové typy do jednoho datového typu.<br /><br /> Výchozí hodnoty a řetězec literálu formáty jsou stejné jako s těmi definovanými ve `date` a `time` datové typy.|  
|`datetimeoffset`|`datetimeoffset` Datového typu obsahuje všechny funkce `datetime2` s posunem další časové pásmo. Posun časového pásma je vyjádřena jako [+&#124;-] hh: mm. HH jsou 2 číslic od 00 do 14, které představují počet hodin v posun časového pásma. MM je 2 soustavě v rozsahu od 00 do 59 představující počet dalších minut v posun časového pásma. Formáty času jsou podporovány na 100 nanosekund. Povinné + nebo - znak označuje, zda je posun v časových pásmech přičíst nebo odečíst od času UTC (světový čas koordinovat nebo greenwichský střední čas) k získání místní čas.|  
  
> [!NOTE]
>  Další informace o používání `Type System Version` – klíčové slovo, naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Formát data a pořadí v datu  
 Jak analyzuje hodnoty data a času v systému SQL Server závisí nejen na verzi systému typu a verzi serveru, ale také na jazyk a formát výchozí nastavení serveru. Řetězec data, může být nelze rozpoznat, pokud se dotaz provádí na připojení funguje pro formáty data z jednoho jazyka, který používá jiný jazyk a formát data nastavení.  
  
 Příkaz jazyka Transact-SQL příkaz SET LANGUAGE se implicitně nastaví parametr DATEFORMAT, který určuje pořadí částí data. Příkaz nastavit parametr DATEFORMAT příkazů jazyka Transact-SQL můžete použít na připojení k rozlišení hodnot data podle pořadí částí data v objednávce MDR, DMY, RMD, typy, MYD nebo DYM.  
  
 Pokud nezadáte žádné parametr DATEFORMAT pro připojení, SQL Server používá výchozí jazyk přidružený k připojení. Například řetězec data 01/02/03 "je interpretován jako formát MDR (2. ledna 2003) na serveru s nastavením jazyk angličtinu Spojených států a jako DMY (1. února 2003) na serveru s nastavením jazyka britské angličtiny. Rok je určen pomocí systému SQL Server přerušení rok pravidla, která definuje než datum přerušení pro přiřazení hodnoty století. Další informace najdete v tématu [dvě číslici roce přerušení možnost](https://go.microsoft.com/fwlink/?LinkId=120473) v SQL Server Books Online.  
  
> [!NOTE]
>  Formát data typy není podporován při převodu z formátu řetězce na `date`, `time`, `datetime2`, nebo `datetimeoffset`.  
  
 Další informace o interpretace data a času v systému SQL Server najdete v tématu [pomocí kalendářní a časová Data](https://go.microsoft.com/fwlink/?LinkID=98361) SQL Server 2008 Books Online.  
  
## <a name="datetime-data-types-and-parameters"></a>Datum/čas typy a parametry  
 Následující výčty jsou přidané do <xref:System.Data.SqlDbType> pro podporu nové datové typy data a času.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Můžete zadat datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jednoho z předchozích <xref:System.Data.SqlDbType> výčty. 

> [!NOTE]
> Nelze nastavit `DbType` vlastnost `SqlParameter` k `SqlDbType.Date`.

 Můžete také zadat typ <xref:System.Data.SqlClient.SqlParameter> obecně tak, že nastavíte <xref:System.Data.SqlClient.SqlParameter.DbType%2A> vlastnost `SqlParameter` objekt ke konkrétní <xref:System.Data.DbType> hodnota výčtu. Následující hodnoty výčtu jsou přidané do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datové typy:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Tyto nové výčty doplnit `Date`, `Time`, a `DateTime` výčty, které existovaly ve starších verzích rozhraní .NET Framework.  
  
 Typ zprostředkovatele dat .NET Framework parametr objektu je odvozen z rozhraní .NET Framework typ hodnoty parametru objektu nebo z `DbType` parametr objektu. Žádná nová <xref:System.Data.SqlTypes> byly uvedeny datové typy pro podporu nové datové typy data a času. Následující tabulka popisuje mapování mezi SQL Server 2008 datum a čas datových typů a datové typy CLR.  
  
|Datový typ SQL serveru|Typ rozhraní .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|Datum|System.DateTime|Datum|Datum|  
|čas|System.TimeSpan|Time|Time|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|DateTimeOffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Vlastnosti SqlParameter  
 Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy data a času.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Získá nebo nastaví, zda je hodnota s možnou hodnotou Null. Pokud je hodnota null parametru posíláte na server, je třeba zadat <xref:System.DBNull>, spíše než `null` (`Nothing` v jazyce Visual Basic). Další informace o databázi hodnoty Null, naleznete v tématu [zpracování hodnot Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Získá nebo nastaví maximální počet číslic, na které se používá k reprezentování hodnota. Toto nastavení se ignoruje pro datové typy data a času.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Získá nebo nastaví počet desetinných míst, na které je časová část hodnoty pro `Time`, `DateTime2`, a `DateTimeOffset`. Výchozí hodnota je 0, což znamená, že skutečné škálování je odvozen z hodnoty a odeslat na server.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorovat pro datové typy data a času.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví hodnotu parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví hodnotu parametru.|  
  
> [!NOTE]
>  Vyvolá výjimku časové hodnoty, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Vytváří se parametry  
 Můžete vytvořit <xref:System.Data.SqlClient.SqlParameter> objektu pomocí jeho konstruktoru, nebo jejím přidáním na <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním `Add` metodu <xref:System.Data.SqlClient.SqlParameterCollection>. `Add` Metoda vezme jako vstupní argumenty konstruktoru nebo existující objekt parametru.  
  
 Další části v tomto tématu obsahují příklady toho, jak zadat datum a čas parametry. Další příklady práce s parametry, naleznete v tématu [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) a [parametry adaptéru dat](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
### <a name="date-example"></a>Příklad datum  
 Následující fragment kódu ukazuje, jak určit `date` parametru.  
  
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
 Následující fragment kódu ukazuje, jak určit `time` parametru.  
  
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
 Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částmi datum a čas.  
  
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
 Následující fragment kódu ukazuje, jak určit `DateTimeOffSet` datum, čas a posun časového pásma z 0.  
  
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
 Parametry lze také zadat pomocí `AddWithValue` metodu <xref:System.Data.SqlClient.SqlCommand>, jak je znázorněno v následujícím fragmentu kódu. Ale `AddWithValue` metoda neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> parametru.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 `@date` Parametr namapovat na `date`, `datetime`, nebo `datetime2` datový typ na serveru. Při práci s novými `datetime` datové typy, musíte explicitně nastavit parametr <xref:System.Data.SqlDbType> vlastnost na datový typ instance. Pomocí <xref:System.Data.SqlDbType.Variant> nebo implicitně zadáním hodnot parametrů může způsobit problémy se zpětnou kompatibilitu s `datetime` a `smalldatetime` datové typy.  
  
 Následující tabulka uvádí, které `SqlDbTypes` jsou odvozeny z jaké typy CLR:  
  
|Typ CLR|Odvozené SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Načítají se kalendářní a časová Data  
 Následující tabulka popisuje metody, které slouží k načtení hodnoty data a času v systému SQL Server 2008.  
  
|SqlClient – metoda|Popis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Načte hodnotu zadaného sloupce jako <xref:System.DateTime> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Načte hodnotu zadaného sloupce jako <xref:System.DateTimeOffset> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Vrátí typ, který je základní typ pro pole specifické pro zprostředkovatele. Vrátí stejné typy jako `GetFieldType` pro nové typy data a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Načte hodnotu pro určený sloupec. Vrátí stejné typy jako `GetValue` pro nové typy data a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Načte hodnoty v určeném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Načte se hodnota sloupce jako <xref:System.Data.SqlTypes.SqlString>. <xref:System.InvalidCastException> Nastane, pokud data nelze vyjádřen jako `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Načte data sloupce jako svou výchozí hodnotu `SqlDbType`. Vrátí stejné typy jako `GetValue` pro nové typy data a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Načte hodnoty v určeném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Pokud Type System Version nastavena na SQL Server 2005, načte se hodnota sloupce jako řetězec. <xref:System.InvalidCastException> Nastane, pokud data nelze vyjádřen jako řetězec.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Načte hodnotu zadaného sloupce jako <xref:System.TimeSpan> struktury.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Načte hodnotu zadaného sloupce jako jeho základní typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Načte hodnoty sloupců v poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Vrátí <xref:System.Data.DataTable> , který popisuje metadata sady výsledků dotazu.|  
  
> [!NOTE]
>  Nové datum a čas `SqlDbTypes` nejsou podporovány pro kód, který je spouštěn v procesu v systému SQL Server. Bude vyvolána výjimka, pokud jeden z těchto typů je předán serveru.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Určení hodnoty data a času jako literály  
 Můžete určit datum a čas datové typy s použitím různých formátech různých řetězcového literálu, který SQL Server pak vyhodnotí za běhu, převod na datum/čas vnitřního struktury. SQL Server rozpozná data pro datum a čas, který je uzavřen v jednoduchých uvozovkách ('). Následující příklady ukazují některé formáty:  
  
- Abecední datum formáty, jako například `'October 15, 2006'`.  
  
- Číselná data formátů, jako například `'10/15/2006'`.  
  
- Oddělené formáty řetězců, jako například `'20061015'`, které by být interpretován jako 15. října 2006, pokud používáte formát data ISO.  
  
> [!NOTE]
>  Úplnou dokumentaci najdete pro všechny formáty řetězcového literálu a dalších funkcí datové typy data a času v SQL Server Books Online.  
  
 Vyvolá výjimku časové hodnoty, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-2008-books-online"></a>Prostředky v SQL Server 2008 Books Online  
 Další informace o práci s hodnotami data a času v systému SQL Server 2008 najdete v následujících zdrojích v SQL Server 2008 Books Online.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Datum a čas Data typy a funkce (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|Poskytuje přehled příkazů jazyka Transact-SQL data a času datové typy a funkce.|  
|[Pomocí kalendářní a časová Data](https://go.microsoft.com/fwlink/?LinkId=98361)|Poskytuje informace o datum a čas datové typy a funkce a příklady jejich použití.|  
|[Data Types (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98362)|Popisuje datové typy systému SQL Server 2008.|  
  
## <a name="see-also"></a>Viz také:

- [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Datové typy SQL Serveru a ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
