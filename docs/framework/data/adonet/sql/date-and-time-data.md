---
title: Kalendářní a časová data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: d7a016b8911cee3091dec24bc26d1f1965f54749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148761"
---
# <a name="date-and-time-data"></a>Kalendářní a časová data
SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a čase. Nové datové typy zahrnují samostatné typy pro datum a čas a rozšířené datové typy s větším rozsahem, přesností a povědomím o časovém pásmu. Počínaje aktualizací .NET Framework verze 3.5 Service Pack (SP) 1 poskytuje<xref:System.Data.SqlClient>zprostředkovatel dat rozhraní .NET Framework pro SQL Server ( ) plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008. Chcete-li tyto nové funkce s klientem SqlClient používat, je nutné nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější).  
  
 Verze serveru SQL Server starších než SQL Server 2008 měly pouze `datetime` `smalldatetime`dva datové typy pro práci s hodnotami data a času: a . Oba tyto datové typy obsahují hodnotu data i časovou hodnotu, což ztěžuje práci pouze s hodnotami data nebo pouze času. Tyto datové typy také podporují pouze data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v roce 1753. Dalším omezením je, že tyto starší datové typy nejsou vědomi časového pásma, což ztěžuje práci s daty, která pochází z více časových pásem.  
  
 Kompletní dokumentace pro datové typy serveru SQL Server je k dispozici v SQL Server Books Online. V následující tabulce jsou uvedena témata pro data a čas pro konkrétní verzi.  
  
 **Dokumentace SQL Serveru**  
  
1. [Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a>Datové typy data a času zavedené v serveru SQL Server 2008  
 Následující tabulka popisuje nové datové typy data a času.  
  
|Datový typ serveru SQL Server|Popis|  
|--------------------------|-----------------|  
|`date`|Datový `date` typ má rozsah 1 leden, 01 až prosinec 31, 9999 s přesností 1 den. Výchozí hodnota je 1. Velikost úložiště je 3 bajty.|  
|`time`|Datový `time` typ ukládá pouze časové hodnoty na základě 24hodinových hodin. Datový `time` typ má rozsah 00:00:00.0000000 až 23:59:59.99999999 s přesností 100 nanosekund. Výchozí hodnota je 00:00:00.0000000 (půlnoc). Datový `time` typ podporuje uživatelem definovanou zlomkovou druhou přesnost a velikost úložiště se pohybuje od 3 do 6 bajtů na základě zadané přesnosti.|  
|`datetime2`|Datový `datetime2` typ kombinuje rozsah a přesnost `date` `time` a datových typů do jednoho datového typu.<br /><br /> Výchozí hodnoty a formáty literálu řetězce jsou `date` stejné `time` jako hodnoty definované v datových typech a.|  
|`datetimeoffset`|Datový `datetimeoffset` typ má všechny `datetime2` funkce s další časové pásmo posun. Posun časového pásma je reprezentován jako [+&#124;-] HH:MM. HH je 2 číslice v rozsahu od 00 do 14, které představují počet hodin v posunu časového pásma. MM je 2 číslice v rozsahu od 00 do 59, které představují počet dalších minut v posunu časového pásma. Formáty času jsou podporovány na 100 nanosekund. Povinné znaménko + nebo - označuje, zda je posun časového pásma přidán nebo odečten od času UTC (Universal Time Coordinate nebo Greenwich Mean Time) pro získání místního času.|  
  
> [!NOTE]
> Další informace o `Type System Version` použití klíčového slova naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="date-format-and-date-order"></a>Formát data a pořadí kalendářních dat  
 Způsob analýzy hodnot data a času serveru SQL Server závisí nejen na verzi systému typu a verzi serveru, ale také na výchozím nastavení jazyka a formátu serveru. Řetězec kalendářních dat, který pracuje pro formáty kalendářních dat jednoho jazyka, může být nerozpoznatelný, pokud je dotaz proveden připojením, které používá nastavení formátu jiného jazyka a data.  
  
 Příkaz Transact-SQL SET LANGUAGE implicitně nastaví DATEFORMAT, který určuje pořadí částí data. Příkaz SET DATEFORMAT Transact-SQL můžete použít pro připojení k rozpovězení hodnot kalendářních dat pořadím součástí data v pořadí MDY, DMY, YMD, YDM, MYD nebo DYM.  
  
 Pokud pro připojení nezadáte žádný formát DATEFORMAT, sql server použije výchozí jazyk přidružený k připojení. Například řetězec kalendářních dat 01/02/03 by byl interpretován jako MDY (2. ledna 2003) na serveru s jazykovým nastavením angličtiny ve Spojených státech a jako DMY (1. února 2003) na serveru s jazykovým nastavením britské angličtiny. Rok je určen pomocí sql server je cutoff rok pravidlo, které definuje datum přerušení pro přiřazení hodnoty století. Další informace naleznete v tématu [možnost přerušení přerušení rokdvouci](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).  
  
> [!NOTE]
> Formát data YDM není při převodu z `date`formátu `time` `datetime2`řetězce `datetimeoffset`do formátu řetězce na , , nebo .  
  
 Další informace o interpretaci dat data a času serveru SQL Server naleznete [v tématu Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).  
  
## <a name="datetime-data-types-and-parameters"></a>Datové typy a parametry data a času  
 Následující výčty byly přidány <xref:System.Data.SqlDbType> pro podporu nové datové typy data a času.  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

Datový typ a můžete <xref:System.Data.SqlClient.SqlParameter> určit pomocí jednoho z <xref:System.Data.SqlDbType> předchozích výčtů.

> [!NOTE]
> Vlastnost `DbType` a do `SqlParameter` . `SqlDbType.Date`

 <xref:System.Data.SqlClient.SqlParameter> Typ objektu můžete také určit obecně <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nastavením `SqlParameter` vlastnosti objektu na určitou <xref:System.Data.DbType> hodnotu výčtu. Pro podporu datových typů a <xref:System.Data.DbType> `datetimeoffset` byly `datetime2` přidány následující hodnoty výčtu:  
  
- DbType.DateTime2  
  
- DbType.DateTimeOffset  
  
 Tyto nové výčty `Date`doplňují `Time`, `DateTime` a výčty, které existovaly v dřívějších verzích rozhraní .NET Framework.  
  
 Typ datového zprostředkovatele rozhraní .NET Framework objektu parametru je odvozen z typu rozhraní .NET Framework hodnoty objektu parametru `DbType` nebo z objektu parametru. Nebyly <xref:System.Data.SqlTypes> zavedeny žádné nové datové typy, které by podporovaly nové datové typy data a času. Následující tabulka popisuje mapování mezi datovými typy data a času serveru SQL Server 2008 a datovými typy CLR.  
  
|Datový typ serveru SQL Server|Typ rozhraní .NET Framework|System.Data.SqlDbType|System.Data.DbType|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|date|System.datetime|Datum|Datum|  
|time|System.TimeSpan|Time|Time|  
|datetime2|System.datetime|DatumČas2|DatumČas2|  
|Datetimeoffset|System.DateTimeOffset|DateTimeOffset|DateTimeOffset|  
|datetime|System.datetime|DateTime|DateTime|  
|Smalldatetime|System.datetime|DateTime|DateTime|  
  
### <a name="sqlparameter-properties"></a>Vlastnosti parametru SqlParameter  
 Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy data a času.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|Získá nebo nastaví, zda je hodnota nullable. Při odeslání hodnoty parametru null na server, je nutné zadat <xref:System.DBNull>, spíše než `null` (v`Nothing` jazyce Visual Basic). Další informace o hodnotách null databáze naleznete v [tématu Zpracování hodnot Null](handling-null-values.md).|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|Získá nebo nastaví maximální počet číslic použitých k reprezentaci hodnoty. Toto nastavení je ignorováno pro datové typy data a času.|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|Získá nebo nastaví počet desetinných míst, na které je `Time` `DateTime2`časová `DateTimeOffset`část hodnoty vyřešena pro , ,a . Výchozí hodnota je 0, což znamená, že skutečné měřítko je odvozeno z hodnoty a odesláno na server.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Ignorováno pro datové typy data a času.|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví hodnotu parametru.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví hodnotu parametru.|  
  
> [!NOTE]
> Časové hodnoty, které jsou menší než nula nebo větší <xref:System.ArgumentException>nebo rovno 24 hodin bude vyvolat .  
  
### <a name="creating-parameters"></a>Vytváření parametrů  
 Objekt můžete <xref:System.Data.SqlClient.SqlParameter> vytvořit pomocí jeho konstruktoru nebo jeho <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> přidáním `Add` do kolekce <xref:System.Data.SqlClient.SqlParameterCollection>voláním metody . Metoda `Add` bude trvat jako vstupní argumenty konstruktoru nebo existující parametr objektu.  
  
 Další části v tomto tématu obsahují příklady, jak zadat parametry data a času. Další příklady práce s parametry naleznete [v tématu Konfigurace parametrů a datových typů parametrů](../configuring-parameters-and-parameter-data-types.md) a parametrů [datového adaptéru](../dataadapter-parameters.md).  
  
### <a name="date-example"></a>Příklad data  
 Následující fragment kódu ukazuje, jak `date` zadat parametr.  
  
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
 Následující fragment kódu ukazuje, jak `time` zadat parametr.  
  
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
 Následující fragment kódu ukazuje, jak `datetime2` zadat parametr s částí data a času.  
  
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
  
### <a name="datetimeoffset-example"></a>Příklad dateTimeOffSet  
 Následující fragment kódu ukazuje, jak `DateTimeOffSet` zadat parametr s datem, časem a posunem časového pásma 0.  
  
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
 Parametry můžete zadat také `AddWithValue` pomocí metody <xref:System.Data.SqlClient.SqlCommand>a , jak je znázorněno na následujícím fragmentu kódu. `AddWithValue` Metoda však neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 Parametr `@date` může být `date`mapován na typ , `datetime`nebo `datetime2` datový typ na serveru. Při práci s `datetime` novými datovými typy je <xref:System.Data.SqlDbType> nutné explicitně nastavit vlastnost parametru na datový typ instance. Použití <xref:System.Data.SqlDbType.Variant> nebo implicitně zadání hodnot parametrů může způsobit `datetime` `smalldatetime` problémy se zpětnou kompatibilitou s datovými typy a.  
  
 V následující tabulce `SqlDbTypes` jsou uvedeny, které jsou odvozeny od kterých clr typy:  
  
|Typ CLR|Odvozený sqldbtype|  
|--------------|------------------------|  
|DateTime|SqlDbType.DateTime|  
|TimeSpan|SqlDbType.Time|  
|DateTimeOffset|SqlDbType.DateTimeOffset|  
  
## <a name="retrieving-date-and-time-data"></a>Načítání dat data a času  
 Následující tabulka popisuje metody, které se používají k načtení hodnot data a času serveru SQL Server 2008.  
  
|Metoda SqlClient|Popis|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|Načte zadanou hodnotu <xref:System.DateTime> sloupce jako strukturu.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|Načte zadanou hodnotu <xref:System.DateTimeOffset> sloupce jako strukturu.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|Vrátí typ, který je základní typ specifický pro zprostředkovatele pro pole. Vrátí stejné typy `GetFieldType` jako pro nové typy dat a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|Načte hodnotu zadaného sloupce. Vrátí stejné typy `GetValue` jako pro nové typy dat a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|Načte hodnoty v zadaném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|Načte hodnotu sloupce <xref:System.Data.SqlTypes.SqlString>jako . Dojde <xref:System.InvalidCastException> k, pokud data nelze vyjádřit `SqlString`jako .|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|Načte data sloupců `SqlDbType`jako výchozí . Vrátí stejné typy `GetValue` jako pro nové typy dat a času.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|Načte hodnoty v zadaném poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|Načte hodnotu sloupce jako řetězec, pokud je typ systémová verze nastavena na SQL Server 2005. Dojde <xref:System.InvalidCastException> k, pokud data nelze vyjádřit jako řetězec.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|Načte zadanou hodnotu <xref:System.TimeSpan> sloupce jako strukturu.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|Načte zadanou hodnotu sloupce jako základní typ CLR.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|Načte hodnoty sloupců v poli.|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<xref:System.Data.DataTable> Vrátí, který popisuje metadata sady výsledků.|  
  
> [!NOTE]
> Nové datum a `SqlDbTypes` čas nejsou podporovány pro kód, který je spuštěn v procesu v SQL Server. Výjimka bude vyvolána, pokud jeden z těchto typů je předán serveru.  
  
## <a name="specifying-date-and-time-values-as-literals"></a>Zadání hodnot data a času jako literály  
 Datové typy data a času můžete zadat pomocí různých formátů řetězců literálu, které sql server vyhodnocuje za běhu a převádí je na interní struktury data a času. SQL Server rozpozná data a čas dat, která je uzavřena v jednoduchých uvozovkách ('). Následující příklady ukazují některé formáty:  
  
- Abecední formáty `'October 15, 2006'`kalendářních dat, například .  
  
- Číselné formáty kalendářních dat, například `'10/15/2006'`.  
  
- Neoddělené formáty řetězců, `'20061015'`například , které by byly interpretovány jako 15.  
  
> [!NOTE]
> Kompletní dokumentaci pro všechny formáty literálu řetězce a další funkce datových typů data a času naleznete v části SQL Server Books Online.  
  
 Časové hodnoty, které jsou menší než nula nebo větší <xref:System.ArgumentException>nebo rovno 24 hodin bude vyvolat .  
  
## <a name="resources-in-sql-server-books-online"></a>Prostředky v knihách serveru SQL Server Online  
 Další informace o práci s hodnotami data a času na serveru SQL Server naleznete v následujících prostředcích v části SQL Server Books Online.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Datové typy a funkce data a času (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|Obsahuje přehled všech datových typů a funkcí data a času transact-SQL.|  
|[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))|Obsahuje informace o datech a čase datových typů a funkcí a příklady jejich použití.|  
|[Datové typy (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)|Popisuje systémové datové typy v serveru SQL Server.|  
  
## <a name="see-also"></a>Viz také

- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)
- [Přehled ADO.NET](../ado-net-overview.md)
