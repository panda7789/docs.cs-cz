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
# <a name="date-and-time-data"></a><span data-ttu-id="4c317-102">Kalendářní a časová data</span><span class="sxs-lookup"><span data-stu-id="4c317-102">Date and Time Data</span></span>
<span data-ttu-id="4c317-103">SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a čase.</span><span class="sxs-lookup"><span data-stu-id="4c317-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="4c317-104">Nové datové typy zahrnují samostatné typy pro datum a čas a rozšířené datové typy s větším rozsahem, přesností a povědomím o časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="4c317-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="4c317-105">Počínaje aktualizací .NET Framework verze 3.5 Service Pack (SP) 1 poskytuje<xref:System.Data.SqlClient>zprostředkovatel dat rozhraní .NET Framework pro SQL Server ( ) plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4c317-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="4c317-106">Chcete-li tyto nové funkce s klientem SqlClient používat, je nutné nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="4c317-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="4c317-107">Verze serveru SQL Server starších než SQL Server 2008 měly pouze `datetime` `smalldatetime`dva datové typy pro práci s hodnotami data a času: a .</span><span class="sxs-lookup"><span data-stu-id="4c317-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="4c317-108">Oba tyto datové typy obsahují hodnotu data i časovou hodnotu, což ztěžuje práci pouze s hodnotami data nebo pouze času.</span><span class="sxs-lookup"><span data-stu-id="4c317-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="4c317-109">Tyto datové typy také podporují pouze data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v roce 1753.</span><span class="sxs-lookup"><span data-stu-id="4c317-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="4c317-110">Dalším omezením je, že tyto starší datové typy nejsou vědomi časového pásma, což ztěžuje práci s daty, která pochází z více časových pásem.</span><span class="sxs-lookup"><span data-stu-id="4c317-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="4c317-111">Kompletní dokumentace pro datové typy serveru SQL Server je k dispozici v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="4c317-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="4c317-112">V následující tabulce jsou uvedena témata pro data a čas pro konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="4c317-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="4c317-113">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="4c317-113">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="4c317-114">[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="4c317-114">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="4c317-115">Datové typy data a času zavedené v serveru SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="4c317-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="4c317-116">Následující tabulka popisuje nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="4c317-117">Datový typ serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="4c317-117">SQL Server data type</span></span>|<span data-ttu-id="4c317-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4c317-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="4c317-119">Datový `date` typ má rozsah 1 leden, 01 až prosinec 31, 9999 s přesností 1 den.</span><span class="sxs-lookup"><span data-stu-id="4c317-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="4c317-120">Výchozí hodnota je 1.</span><span class="sxs-lookup"><span data-stu-id="4c317-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="4c317-121">Velikost úložiště je 3 bajty.</span><span class="sxs-lookup"><span data-stu-id="4c317-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="4c317-122">Datový `time` typ ukládá pouze časové hodnoty na základě 24hodinových hodin.</span><span class="sxs-lookup"><span data-stu-id="4c317-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="4c317-123">Datový `time` typ má rozsah 00:00:00.0000000 až 23:59:59.99999999 s přesností 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="4c317-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="4c317-124">Výchozí hodnota je 00:00:00.0000000 (půlnoc).</span><span class="sxs-lookup"><span data-stu-id="4c317-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="4c317-125">Datový `time` typ podporuje uživatelem definovanou zlomkovou druhou přesnost a velikost úložiště se pohybuje od 3 do 6 bajtů na základě zadané přesnosti.</span><span class="sxs-lookup"><span data-stu-id="4c317-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="4c317-126">Datový `datetime2` typ kombinuje rozsah a přesnost `date` `time` a datových typů do jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="4c317-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="4c317-127">Výchozí hodnoty a formáty literálu řetězce jsou `date` stejné `time` jako hodnoty definované v datových typech a.</span><span class="sxs-lookup"><span data-stu-id="4c317-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="4c317-128">Datový `datetimeoffset` typ má všechny `datetime2` funkce s další časové pásmo posun.</span><span class="sxs-lookup"><span data-stu-id="4c317-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="4c317-129">Posun časového pásma je reprezentován jako [+&#124;-] HH:MM.</span><span class="sxs-lookup"><span data-stu-id="4c317-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="4c317-130">HH je 2 číslice v rozsahu od 00 do 14, které představují počet hodin v posunu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="4c317-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="4c317-131">MM je 2 číslice v rozsahu od 00 do 59, které představují počet dalších minut v posunu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="4c317-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="4c317-132">Formáty času jsou podporovány na 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="4c317-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="4c317-133">Povinné znaménko + nebo - označuje, zda je posun časového pásma přidán nebo odečten od času UTC (Universal Time Coordinate nebo Greenwich Mean Time) pro získání místního času.</span><span class="sxs-lookup"><span data-stu-id="4c317-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4c317-134">Další informace o `Type System Version` použití klíčového slova naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c317-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="4c317-135">Formát data a pořadí kalendářních dat</span><span class="sxs-lookup"><span data-stu-id="4c317-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="4c317-136">Způsob analýzy hodnot data a času serveru SQL Server závisí nejen na verzi systému typu a verzi serveru, ale také na výchozím nastavení jazyka a formátu serveru.</span><span class="sxs-lookup"><span data-stu-id="4c317-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="4c317-137">Řetězec kalendářních dat, který pracuje pro formáty kalendářních dat jednoho jazyka, může být nerozpoznatelný, pokud je dotaz proveden připojením, které používá nastavení formátu jiného jazyka a data.</span><span class="sxs-lookup"><span data-stu-id="4c317-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="4c317-138">Příkaz Transact-SQL SET LANGUAGE implicitně nastaví DATEFORMAT, který určuje pořadí částí data.</span><span class="sxs-lookup"><span data-stu-id="4c317-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="4c317-139">Příkaz SET DATEFORMAT Transact-SQL můžete použít pro připojení k rozpovězení hodnot kalendářních dat pořadím součástí data v pořadí MDY, DMY, YMD, YDM, MYD nebo DYM.</span><span class="sxs-lookup"><span data-stu-id="4c317-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="4c317-140">Pokud pro připojení nezadáte žádný formát DATEFORMAT, sql server použije výchozí jazyk přidružený k připojení.</span><span class="sxs-lookup"><span data-stu-id="4c317-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="4c317-141">Například řetězec kalendářních dat 01/02/03 by byl interpretován jako MDY (2. ledna 2003) na serveru s jazykovým nastavením angličtiny ve Spojených státech a jako DMY (1. února 2003) na serveru s jazykovým nastavením britské angličtiny.</span><span class="sxs-lookup"><span data-stu-id="4c317-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="4c317-142">Rok je určen pomocí sql server je cutoff rok pravidlo, které definuje datum přerušení pro přiřazení hodnoty století.</span><span class="sxs-lookup"><span data-stu-id="4c317-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="4c317-143">Další informace naleznete v tématu [možnost přerušení přerušení rokdvouci](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span><span class="sxs-lookup"><span data-stu-id="4c317-143">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c317-144">Formát data YDM není při převodu z `date`formátu `time` `datetime2`řetězce `datetimeoffset`do formátu řetězce na , , nebo .</span><span class="sxs-lookup"><span data-stu-id="4c317-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="4c317-145">Další informace o interpretaci dat data a času serveru SQL Server naleznete [v tématu Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="4c317-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="4c317-146">Datové typy a parametry data a času</span><span class="sxs-lookup"><span data-stu-id="4c317-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="4c317-147">Následující výčty byly přidány <xref:System.Data.SqlDbType> pro podporu nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="4c317-148">Datový typ a můžete <xref:System.Data.SqlClient.SqlParameter> určit pomocí jednoho z <xref:System.Data.SqlDbType> předchozích výčtů.</span><span class="sxs-lookup"><span data-stu-id="4c317-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span>

> [!NOTE]
> <span data-ttu-id="4c317-149">Vlastnost `DbType` a do `SqlParameter` . `SqlDbType.Date`</span><span class="sxs-lookup"><span data-stu-id="4c317-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="4c317-150"><xref:System.Data.SqlClient.SqlParameter> Typ objektu můžete také určit obecně <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nastavením `SqlParameter` vlastnosti objektu na určitou <xref:System.Data.DbType> hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="4c317-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="4c317-151">Pro podporu datových typů a <xref:System.Data.DbType> `datetimeoffset` byly `datetime2` přidány následující hodnoty výčtu:</span><span class="sxs-lookup"><span data-stu-id="4c317-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="4c317-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="4c317-152">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="4c317-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="4c317-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="4c317-154">Tyto nové výčty `Date`doplňují `Time`, `DateTime` a výčty, které existovaly v dřívějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c317-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="4c317-155">Typ datového zprostředkovatele rozhraní .NET Framework objektu parametru je odvozen z typu rozhraní .NET Framework hodnoty objektu parametru `DbType` nebo z objektu parametru.</span><span class="sxs-lookup"><span data-stu-id="4c317-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="4c317-156">Nebyly <xref:System.Data.SqlTypes> zavedeny žádné nové datové typy, které by podporovaly nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="4c317-157">Následující tabulka popisuje mapování mezi datovými typy data a času serveru SQL Server 2008 a datovými typy CLR.</span><span class="sxs-lookup"><span data-stu-id="4c317-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="4c317-158">Datový typ serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="4c317-158">SQL Server data type</span></span>|<span data-ttu-id="4c317-159">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c317-159">.NET Framework type</span></span>|<span data-ttu-id="4c317-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="4c317-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="4c317-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="4c317-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="4c317-162">date</span><span class="sxs-lookup"><span data-stu-id="4c317-162">date</span></span>|<span data-ttu-id="4c317-163">System.datetime</span><span class="sxs-lookup"><span data-stu-id="4c317-163">System.DateTime</span></span>|<span data-ttu-id="4c317-164">Datum</span><span class="sxs-lookup"><span data-stu-id="4c317-164">Date</span></span>|<span data-ttu-id="4c317-165">Datum</span><span class="sxs-lookup"><span data-stu-id="4c317-165">Date</span></span>|  
|<span data-ttu-id="4c317-166">time</span><span class="sxs-lookup"><span data-stu-id="4c317-166">time</span></span>|<span data-ttu-id="4c317-167">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="4c317-167">System.TimeSpan</span></span>|<span data-ttu-id="4c317-168">Time</span><span class="sxs-lookup"><span data-stu-id="4c317-168">Time</span></span>|<span data-ttu-id="4c317-169">Time</span><span class="sxs-lookup"><span data-stu-id="4c317-169">Time</span></span>|  
|<span data-ttu-id="4c317-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="4c317-170">datetime2</span></span>|<span data-ttu-id="4c317-171">System.datetime</span><span class="sxs-lookup"><span data-stu-id="4c317-171">System.DateTime</span></span>|<span data-ttu-id="4c317-172">DatumČas2</span><span class="sxs-lookup"><span data-stu-id="4c317-172">DateTime2</span></span>|<span data-ttu-id="4c317-173">DatumČas2</span><span class="sxs-lookup"><span data-stu-id="4c317-173">DateTime2</span></span>|  
|<span data-ttu-id="4c317-174">Datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="4c317-174">datetimeoffset</span></span>|<span data-ttu-id="4c317-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="4c317-175">System.DateTimeOffset</span></span>|<span data-ttu-id="4c317-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="4c317-176">DateTimeOffset</span></span>|<span data-ttu-id="4c317-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="4c317-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="4c317-178">datetime</span><span class="sxs-lookup"><span data-stu-id="4c317-178">datetime</span></span>|<span data-ttu-id="4c317-179">System.datetime</span><span class="sxs-lookup"><span data-stu-id="4c317-179">System.DateTime</span></span>|<span data-ttu-id="4c317-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c317-180">DateTime</span></span>|<span data-ttu-id="4c317-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c317-181">DateTime</span></span>|  
|<span data-ttu-id="4c317-182">Smalldatetime</span><span class="sxs-lookup"><span data-stu-id="4c317-182">smalldatetime</span></span>|<span data-ttu-id="4c317-183">System.datetime</span><span class="sxs-lookup"><span data-stu-id="4c317-183">System.DateTime</span></span>|<span data-ttu-id="4c317-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c317-184">DateTime</span></span>|<span data-ttu-id="4c317-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c317-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="4c317-186">Vlastnosti parametru SqlParameter</span><span class="sxs-lookup"><span data-stu-id="4c317-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="4c317-187">Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="4c317-188">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="4c317-188">Property</span></span>|<span data-ttu-id="4c317-189">Popis</span><span class="sxs-lookup"><span data-stu-id="4c317-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="4c317-190">Získá nebo nastaví, zda je hodnota nullable.</span><span class="sxs-lookup"><span data-stu-id="4c317-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="4c317-191">Při odeslání hodnoty parametru null na server, je nutné zadat <xref:System.DBNull>, spíše než `null` (v`Nothing` jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4c317-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="4c317-192">Další informace o hodnotách null databáze naleznete v [tématu Zpracování hodnot Null](handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="4c317-192">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="4c317-193">Získá nebo nastaví maximální počet číslic použitých k reprezentaci hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4c317-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="4c317-194">Toto nastavení je ignorováno pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="4c317-195">Získá nebo nastaví počet desetinných míst, na které je `Time` `DateTime2`časová `DateTimeOffset`část hodnoty vyřešena pro , ,a .</span><span class="sxs-lookup"><span data-stu-id="4c317-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="4c317-196">Výchozí hodnota je 0, což znamená, že skutečné měřítko je odvozeno z hodnoty a odesláno na server.</span><span class="sxs-lookup"><span data-stu-id="4c317-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="4c317-197">Ignorováno pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="4c317-198">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="4c317-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="4c317-199">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="4c317-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4c317-200">Časové hodnoty, které jsou menší než nula nebo větší <xref:System.ArgumentException>nebo rovno 24 hodin bude vyvolat .</span><span class="sxs-lookup"><span data-stu-id="4c317-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="4c317-201">Vytváření parametrů</span><span class="sxs-lookup"><span data-stu-id="4c317-201">Creating Parameters</span></span>  
 <span data-ttu-id="4c317-202">Objekt můžete <xref:System.Data.SqlClient.SqlParameter> vytvořit pomocí jeho konstruktoru nebo jeho <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> přidáním `Add` do kolekce <xref:System.Data.SqlClient.SqlParameterCollection>voláním metody .</span><span class="sxs-lookup"><span data-stu-id="4c317-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="4c317-203">Metoda `Add` bude trvat jako vstupní argumenty konstruktoru nebo existující parametr objektu.</span><span class="sxs-lookup"><span data-stu-id="4c317-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="4c317-204">Další části v tomto tématu obsahují příklady, jak zadat parametry data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="4c317-205">Další příklady práce s parametry naleznete [v tématu Konfigurace parametrů a datových typů parametrů](../configuring-parameters-and-parameter-data-types.md) a parametrů [datového adaptéru](../dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4c317-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="4c317-206">Příklad data</span><span class="sxs-lookup"><span data-stu-id="4c317-206">Date Example</span></span>  
 <span data-ttu-id="4c317-207">Následující fragment kódu ukazuje, jak `date` zadat parametr.</span><span class="sxs-lookup"><span data-stu-id="4c317-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="4c317-208">Příklad času</span><span class="sxs-lookup"><span data-stu-id="4c317-208">Time Example</span></span>  
 <span data-ttu-id="4c317-209">Následující fragment kódu ukazuje, jak `time` zadat parametr.</span><span class="sxs-lookup"><span data-stu-id="4c317-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="4c317-210">Příklad Datetime2</span><span class="sxs-lookup"><span data-stu-id="4c317-210">Datetime2 Example</span></span>  
 <span data-ttu-id="4c317-211">Následující fragment kódu ukazuje, jak `datetime2` zadat parametr s částí data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="4c317-212">Příklad dateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="4c317-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="4c317-213">Následující fragment kódu ukazuje, jak `DateTimeOffSet` zadat parametr s datem, časem a posunem časového pásma 0.</span><span class="sxs-lookup"><span data-stu-id="4c317-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="4c317-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="4c317-214">AddWithValue</span></span>  
 <span data-ttu-id="4c317-215">Parametry můžete zadat také `AddWithValue` pomocí metody <xref:System.Data.SqlClient.SqlCommand>a , jak je znázorněno na následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="4c317-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="4c317-216">`AddWithValue` Metoda však neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.</span><span class="sxs-lookup"><span data-stu-id="4c317-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="4c317-217">Parametr `@date` může být `date`mapován na typ , `datetime`nebo `datetime2` datový typ na serveru.</span><span class="sxs-lookup"><span data-stu-id="4c317-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="4c317-218">Při práci s `datetime` novými datovými typy je <xref:System.Data.SqlDbType> nutné explicitně nastavit vlastnost parametru na datový typ instance.</span><span class="sxs-lookup"><span data-stu-id="4c317-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="4c317-219">Použití <xref:System.Data.SqlDbType.Variant> nebo implicitně zadání hodnot parametrů může způsobit `datetime` `smalldatetime` problémy se zpětnou kompatibilitou s datovými typy a.</span><span class="sxs-lookup"><span data-stu-id="4c317-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="4c317-220">V následující tabulce `SqlDbTypes` jsou uvedeny, které jsou odvozeny od kterých clr typy:</span><span class="sxs-lookup"><span data-stu-id="4c317-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="4c317-221">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="4c317-221">CLR type</span></span>|<span data-ttu-id="4c317-222">Odvozený sqldbtype</span><span class="sxs-lookup"><span data-stu-id="4c317-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="4c317-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="4c317-223">DateTime</span></span>|<span data-ttu-id="4c317-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="4c317-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="4c317-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="4c317-225">TimeSpan</span></span>|<span data-ttu-id="4c317-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="4c317-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="4c317-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="4c317-227">DateTimeOffset</span></span>|<span data-ttu-id="4c317-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="4c317-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="4c317-229">Načítání dat data a času</span><span class="sxs-lookup"><span data-stu-id="4c317-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="4c317-230">Následující tabulka popisuje metody, které se používají k načtení hodnot data a času serveru SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4c317-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="4c317-231">Metoda SqlClient</span><span class="sxs-lookup"><span data-stu-id="4c317-231">SqlClient method</span></span>|<span data-ttu-id="4c317-232">Popis</span><span class="sxs-lookup"><span data-stu-id="4c317-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="4c317-233">Načte zadanou hodnotu <xref:System.DateTime> sloupce jako strukturu.</span><span class="sxs-lookup"><span data-stu-id="4c317-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="4c317-234">Načte zadanou hodnotu <xref:System.DateTimeOffset> sloupce jako strukturu.</span><span class="sxs-lookup"><span data-stu-id="4c317-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="4c317-235">Vrátí typ, který je základní typ specifický pro zprostředkovatele pro pole.</span><span class="sxs-lookup"><span data-stu-id="4c317-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="4c317-236">Vrátí stejné typy `GetFieldType` jako pro nové typy dat a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="4c317-237">Načte hodnotu zadaného sloupce.</span><span class="sxs-lookup"><span data-stu-id="4c317-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="4c317-238">Vrátí stejné typy `GetValue` jako pro nové typy dat a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="4c317-239">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="4c317-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="4c317-240">Načte hodnotu sloupce <xref:System.Data.SqlTypes.SqlString>jako .</span><span class="sxs-lookup"><span data-stu-id="4c317-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="4c317-241">Dojde <xref:System.InvalidCastException> k, pokud data nelze vyjádřit `SqlString`jako .</span><span class="sxs-lookup"><span data-stu-id="4c317-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="4c317-242">Načte data sloupců `SqlDbType`jako výchozí .</span><span class="sxs-lookup"><span data-stu-id="4c317-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="4c317-243">Vrátí stejné typy `GetValue` jako pro nové typy dat a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="4c317-244">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="4c317-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="4c317-245">Načte hodnotu sloupce jako řetězec, pokud je typ systémová verze nastavena na SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="4c317-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="4c317-246">Dojde <xref:System.InvalidCastException> k, pokud data nelze vyjádřit jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="4c317-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="4c317-247">Načte zadanou hodnotu <xref:System.TimeSpan> sloupce jako strukturu.</span><span class="sxs-lookup"><span data-stu-id="4c317-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="4c317-248">Načte zadanou hodnotu sloupce jako základní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="4c317-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="4c317-249">Načte hodnoty sloupců v poli.</span><span class="sxs-lookup"><span data-stu-id="4c317-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="4c317-250"><xref:System.Data.DataTable> Vrátí, který popisuje metadata sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="4c317-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4c317-251">Nové datum a `SqlDbTypes` čas nejsou podporovány pro kód, který je spuštěn v procesu v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4c317-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="4c317-252">Výjimka bude vyvolána, pokud jeden z těchto typů je předán serveru.</span><span class="sxs-lookup"><span data-stu-id="4c317-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="4c317-253">Zadání hodnot data a času jako literály</span><span class="sxs-lookup"><span data-stu-id="4c317-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="4c317-254">Datové typy data a času můžete zadat pomocí různých formátů řetězců literálu, které sql server vyhodnocuje za běhu a převádí je na interní struktury data a času.</span><span class="sxs-lookup"><span data-stu-id="4c317-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="4c317-255">SQL Server rozpozná data a čas dat, která je uzavřena v jednoduchých uvozovkách (').</span><span class="sxs-lookup"><span data-stu-id="4c317-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="4c317-256">Následující příklady ukazují některé formáty:</span><span class="sxs-lookup"><span data-stu-id="4c317-256">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="4c317-257">Abecední formáty `'October 15, 2006'`kalendářních dat, například .</span><span class="sxs-lookup"><span data-stu-id="4c317-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="4c317-258">Číselné formáty kalendářních dat, například `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="4c317-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="4c317-259">Neoddělené formáty řetězců, `'20061015'`například , které by byly interpretovány jako 15.</span><span class="sxs-lookup"><span data-stu-id="4c317-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c317-260">Kompletní dokumentaci pro všechny formáty literálu řetězce a další funkce datových typů data a času naleznete v části SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="4c317-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="4c317-261">Časové hodnoty, které jsou menší než nula nebo větší <xref:System.ArgumentException>nebo rovno 24 hodin bude vyvolat .</span><span class="sxs-lookup"><span data-stu-id="4c317-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="4c317-262">Prostředky v knihách serveru SQL Server Online</span><span class="sxs-lookup"><span data-stu-id="4c317-262">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="4c317-263">Další informace o práci s hodnotami data a času na serveru SQL Server naleznete v následujících prostředcích v části SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="4c317-263">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="4c317-264">Téma</span><span class="sxs-lookup"><span data-stu-id="4c317-264">Topic</span></span>|<span data-ttu-id="4c317-265">Popis</span><span class="sxs-lookup"><span data-stu-id="4c317-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4c317-266">Datové typy a funkce data a času (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c317-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="4c317-267">Obsahuje přehled všech datových typů a funkcí data a času transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="4c317-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="4c317-268">[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="4c317-268">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="4c317-269">Obsahuje informace o datech a čase datových typů a funkcí a příklady jejich použití.</span><span class="sxs-lookup"><span data-stu-id="4c317-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="4c317-270">Datové typy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4c317-270">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="4c317-271">Popisuje systémové datové typy v serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4c317-271">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c317-272">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c317-272">See also</span></span>

- [<span data-ttu-id="4c317-273">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4c317-273">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="4c317-274">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="4c317-274">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="4c317-275">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4c317-275">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="4c317-276">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4c317-276">ADO.NET Overview</span></span>](../ado-net-overview.md)
