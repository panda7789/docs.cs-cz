---
title: Kalendářní a časová data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: bdcbaffe1be4933b89c7bf0d3a11e1bb871bc2bd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450295"
---
# <a name="date-and-time-data"></a>Kalendářní a časová data
SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času. Nové typy dat zahrnují samostatné typy pro datum a čas a rozšířené datové typy s větším rozsahem, přesností a vědomím časového pásma. Počínaje verzí 3,5 .NET Framework Service Pack (SP) 1 .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>) poskytuje plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008. Abyste mohli používat tyto nové funkce s SqlClient, musíte nainstalovat .NET Framework 3,5 SP1 (nebo novější).  
  
 Verze SQL Server starších než SQL Server 2008 obsahovaly jenom dva typy dat pro práci s hodnotami data a času: `datetime` a `smalldatetime`. Oba tyto datové typy obsahují jak hodnotu data, tak časovou hodnotu, což usnadňuje práci s pouze hodnotami data a času. Tyto datové typy také podporují data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v 1753. Dalším omezením je, že tyto starší datové typy nejsou v časovém pásmu. díky tomu je obtížné pracovat s daty, která pocházejí z několika časových pásem.  
  
 Kompletní dokumentace pro SQL Server datové typy jsou k dispozici v SQL Server Knihy online. V následující tabulce jsou uvedena témata o vstupní úrovni pro konkrétní verzi pro data data a času.  
  
 **Dokumentace SQL Serveru**  
  
1. [Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Datové typy data a času zavedené v SQL Server 2008  
 Následující tabulka popisuje nové datové typy data a času.  
  
|SQL Server datový typ|Popis|  
|--------------------------|-----------------|  
|`date`|Datový typ `date` má 1. ledna 01 do 31. prosince 9999 s přesností 1 den. Výchozí hodnota je 1. ledna 1900. Velikost úložiště je 3 bajty.|  
|`time`|Datový typ `time` ukládá pouze hodnoty času na základě 24hodinovém času. Datový typ `time` má rozsah 00:00:00.0000000 až 23:59:59.9999999 s přesností 100 nanosekund. Výchozí hodnota je 00:00:00.0000000 (půlnoc). Datový typ `time` podporuje uživatelem definovanou zlomkovou přesnost druhé a velikost úložiště se v závislosti na zadané přesnosti liší od 3 do 6 bajtů.|  
|`datetime2`|`datetime2` datový typ kombinuje rozsah a přesnost `date` a `time` datových typů do jediného datového typu.<br /><br /> Výchozí hodnoty a formáty řetězcového literálu jsou stejné jako definice v datových typech `date` a `time`.|  
|`datetimeoffset`|Datový typ `datetimeoffset` obsahuje všechny funkce `datetime2` s časovým posunem dalšího časového pásma. Posun časového pásma je reprezentován jako [+&#124;-] hh: mm. HH je 2 číslice od 00 do 14, které reprezentují počet hodin v posunu časového pásma. MM je 2 číslice od 00 do 59, které reprezentují počet dalších minut v posunu časového pásma. Formáty času jsou podporovány až 100 nanosekund. Povinný symbol + nebo-označuje, zda je posunutí časového pásma přidáno nebo odečteno od času UTC (univerzální časová souřadnice nebo Greenwichský střední čas) k získání místního času.|  
  
> [!NOTE]
> Další informace o použití klíčového slova `Type System Version` naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Formát data a pořadí data  
 Způsob, jakým SQL Server analyzují hodnoty data a času, nezávisí pouze na typu verze systému a verzi serveru, ale také na výchozím jazykovém nastavení serveru a formátu. Řetězec kalendářního data, který funguje pro formáty data v jednom jazyku, může být nerozpoznatelný, pokud je dotaz spuštěn pomocí připojení, které používá jiný jazyk a nastavení formátu data.  
  
 Příkaz jazyka Transact-SQL SET implicitně nastaví parametr DateFormat, který určuje pořadí částí data. Pomocí příkazu Transact-SQL SET parametr DateFormat pro připojení můžete určit hodnoty data řazením částí data v pořadí MDY, DMY, YMD, není, MYD nebo DYM.  
  
 Pokud pro připojení nezadáte žádné parametr DateFormat, používá SQL Server výchozí jazyk přidružený k tomuto připojení. Například řetězec data "01/02/03" by byl interpretován jako MDY (2. ledna 2003) na serveru s nastavením jazyka USA angličtinu a jako DMY (1. února 2003) na serveru s nastavením jazyka britské angličtiny. Rok je určen pomocí pravidla pro přerušení roku SQL Server, které definuje datum přerušení pro přiřazení hodnoty století. Další informace najdete v tématu [možnost přerušení dvou číslic v roce](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).  
  
> [!NOTE]
> Formát data není není podporován při převodu z formátu řetězce na `date`, `time`, `datetime2`nebo `datetimeoffset`.  
  
 Další informace o tom, jak SQL Server interpretuje data data a času, najdete v tématu [použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Datové typy a parametry typu datum/čas  
 Následující výčty byly přidány do <xref:System.Data.SqlDbType> pro podporu nových datových typů data a času.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Můžete určit datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jednoho z předchozích <xref:System.Data.SqlDbType> výčtů. 

> [!NOTE]
> Vlastnost `DbType` `SqlParameter` nelze nastavit na `SqlDbType.Date`.

 Můžete také určit typ <xref:System.Data.SqlClient.SqlParameter> obecně nastavením vlastnosti <xref:System.Data.SqlClient.SqlParameter.DbType%2A> objektu `SqlParameter` na konkrétní hodnotu výčtu <xref:System.Data.DbType>. Následující hodnoty výčtu byly přidány do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datových typů:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Tyto nové výčty doplňují výčty `Date`, `Time`a `DateTime`, které existovaly v dřívějších verzích .NET Framework.  
  
 Typ poskytovatele .NET Framework dat objektu Parameter je odvozen z .NET Framework typu hodnoty objektu Parameter nebo z `DbType` objektu Parameter... Nebyly zavedeny žádné nové datové typy <xref:System.Data.SqlTypes> pro podporu nových datových typů data a času. Následující tabulka popisuje mapování mezi datovými typy data a času SQL Server 2008 a datovými typy CLR.  
  
|SQL Server datový typ|Typ rozhraní .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.DateTime|Datum|Datum|  
|time|System. TimeSpan|Čas|Čas|  
|datetime2|System.DateTime|DateTime2|DateTime2|  
|DateTimeOffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.DateTime|DateTime|DateTime|  
|smalldatetime|System.DateTime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Vlastnosti SqlParameter  
 Následující tabulka obsahuje popis `SqlParameter` vlastností, které jsou relevantní pro datové typy data a času.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Získává nebo nastavuje, jestli je hodnota null. Když odešlete hodnotu parametru s hodnotou null na server, je nutné zadat <xref:System.DBNull>místo `null` (`Nothing` v Visual Basic). Další informace o hodnotách null databáze naleznete v tématu [zpracování hodnot null](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Získá nebo nastaví maximální počet číslic, které se použijí k reprezentaci hodnoty. Toto nastavení se ignoruje u datových typů data a času.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Získá nebo nastaví počet desetinných míst, na které je vyřešena časová část hodnoty pro `Time`, `DateTime2`a `DateTimeOffset`. Výchozí hodnota je 0, což znamená, že skutečné měřítko je odvozeno od hodnoty a odesláno na server.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignoruje se pro datové typy data a času.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví hodnotu parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví hodnotu parametru.|  
  
> [!NOTE]
> Hodnoty času, které jsou menší než nula nebo větší než nebo rovny 24 hodinám, budou vyvolat <xref:System.ArgumentException>.  
  
### <a name="creating-parameters"></a>Vytváření parametrů  
 Objekt <xref:System.Data.SqlClient.SqlParameter> lze vytvořit pomocí jeho konstruktoru nebo jeho přidáním do <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním metody `Add` <xref:System.Data.SqlClient.SqlParameterCollection>. Metoda `Add` bude přebírat jako vstup buď argumentů konstruktoru, nebo existujícího objektu Parameter.  
  
 Následující části tohoto tématu obsahují příklady, jak zadat parametry data a času. Další příklady práce s parametry najdete v tématu [Konfigurace parametrů a datových typů parametrů](../configuring-parameters-and-parameter-data-types.md) a [parametrů DataAdapter](../dataadapter-parameters.md).  
  
### <a name="date-example"></a>Příklad data  
 Následující fragment kódu ukazuje, jak zadat parametr `date`.  
  
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
  
### <a name="time-example"></a>Příklad času  
 Následující fragment kódu ukazuje, jak zadat parametr `time`.  
  
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
 Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částmi data a času.  
  
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
  
### <a name="datetimeoffset-example"></a>Datový příklad DateTimeOffSet  
 Následující fragment kódu ukazuje, jak zadat parametr `DateTimeOffSet` s datem, časem a posunem časového pásma 0.  
  
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
 Parametry lze také zadávat pomocí metody `AddWithValue` <xref:System.Data.SqlClient.SqlCommand>, jak je znázorněno v následujícím fragmentu kódu. Metoda `AddWithValue` však neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 Parametr `@date` mohl na serveru namapovat na datový typ `date`, `datetime`nebo `datetime2`. Při práci s novými datovými typy `datetime` musíte explicitně nastavit vlastnost <xref:System.Data.SqlDbType> parametru na datový typ instance. Použití <xref:System.Data.SqlDbType.Variant> nebo implicitně dodávání hodnot parametrů může způsobit problémy s zpětnou kompatibilitou s datovými typy `datetime` a `smalldatetime`.  
  
 Následující tabulka ukazuje, které `SqlDbTypes` jsou odvozeny z typů CLR:  
  
|Typ CLR|Odvozená SqlDbType|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Načítání dat data a času  
 Následující tabulka popisuje metody, které slouží k načtení hodnot data a času SQL Server 2008.  
  
|SqlClient – metoda|Popis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Načte zadanou hodnotu sloupce jako strukturu <xref:System.DateTime>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Načte zadanou hodnotu sloupce jako strukturu <xref:System.DateTimeOffset>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Vrátí typ, který je pro pole základní typ specifický pro poskytovatele. Vrátí stejné typy jako `GetFieldType` pro nové typy data a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Načte hodnotu zadaného sloupce. Vrátí stejné typy jako `GetValue` pro nové typy data a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Načte hodnoty v zadaném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Načte hodnotu sloupce jako <xref:System.Data.SqlTypes.SqlString>. K <xref:System.InvalidCastException> dojde, pokud data nelze vyjádřit jako `SqlString`.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Načte data sloupce jako výchozí `SqlDbType`. Vrátí stejné typy jako `GetValue` pro nové typy data a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Načte hodnoty v zadaném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Načte hodnotu sloupce jako řetězec, pokud je systémová verze typu nastavená na SQL Server 2005. K <xref:System.InvalidCastException> dojde, pokud data nelze vyjádřit jako řetězec.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Načte zadanou hodnotu sloupce jako strukturu <xref:System.TimeSpan>.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Načte zadanou hodnotu sloupce jako svůj základní typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Načte hodnoty sloupce v poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|Vrátí <xref:System.Data.DataTable>, který popisuje metadata sady výsledků dotazu.|  
  
> [!NOTE]
> Nové `SqlDbTypes` data a času nejsou podporovány pro kód, který provádí vnitroprocesové v procesu SQL Server. Pokud je jeden z těchto typů předán serveru, bude vyvolána výjimka.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Zadání hodnot data a času jako literálů  
 Datové typy data a času lze zadat pomocí různých různých formátů řetězcového literálu, které SQL Server poté vyhodnocovány v době běhu a jejich převodem do interních struktur data a času. SQL Server rozpoznává data data a času uzavřená v jednoduchých uvozovkách ('). Následující příklady ukazují některé formáty:  
  
- Formáty abecedního data, například `'October 15, 2006'`.  
  
- Číselné formáty data, například `'10/15/2006'`.  
  
- Nesamostatné formáty řetězců, například `'20061015'`, které by byly interpretovány jako 15. října 2006, pokud používáte standardní formát data standardu ISO.  
  
> [!NOTE]
> Kompletní dokumentaci pro všechny řetězcové literálové formáty a další funkce datových typů data a času můžete najít v SQL Server Knihy online.  
  
 Hodnoty času, které jsou menší než nula nebo větší než nebo rovny 24 hodinám, budou vyvolat <xref:System.ArgumentException>.  
  
## <a name="resources-in-sql-server-books-online"></a>Prostředky v SQL Server Knihy online  
 Další informace o práci s hodnotami data a času v SQL Server najdete v následujících zdrojích informací v SQL Server Knihy online.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Datové typy a funkce data a času (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Poskytuje přehled všech datových typů a funkcí data a času v jazyce Transact-SQL.|  
|[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Poskytuje informace o datových typech a funkcích data a času a příklady jejich použití.|  
|[Datové typy (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|Popisuje systémové datové typy v SQL Server.|  
  
## <a name="see-also"></a>Viz také

- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
