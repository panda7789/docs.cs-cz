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
# <a name="date-and-time-data"></a><span data-ttu-id="c0b29-102">Kalendářní a časová data</span><span class="sxs-lookup"><span data-stu-id="c0b29-102">Date and Time Data</span></span>
<span data-ttu-id="c0b29-103">SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="c0b29-104">Nové typy dat zahrnují samostatné typy pro datum a čas a rozšířené datové typy s větším rozsahem, přesností a vědomím časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c0b29-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="c0b29-105">Počínaje verzí 3,5 .NET Framework Service Pack (SP) 1 .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>) poskytuje plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c0b29-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="c0b29-106">Abyste mohli používat tyto nové funkce s SqlClient, musíte nainstalovat .NET Framework 3,5 SP1 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="c0b29-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="c0b29-107">Verze SQL Server starších než SQL Server 2008 obsahovaly jenom dva typy dat pro práci s hodnotami data a času: `datetime` a `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="c0b29-108">Oba tyto datové typy obsahují jak hodnotu data, tak časovou hodnotu, což usnadňuje práci s pouze hodnotami data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="c0b29-109">Tyto datové typy také podporují data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v 1753.</span><span class="sxs-lookup"><span data-stu-id="c0b29-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="c0b29-110">Dalším omezením je, že tyto starší datové typy nejsou v časovém pásmu. díky tomu je obtížné pracovat s daty, která pocházejí z několika časových pásem.</span><span class="sxs-lookup"><span data-stu-id="c0b29-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="c0b29-111">Kompletní dokumentace pro SQL Server datové typy jsou k dispozici v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="c0b29-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="c0b29-112">V následující tabulce jsou uvedena témata o vstupní úrovni pro konkrétní verzi pro data data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="c0b29-113">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="c0b29-113">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="c0b29-114">[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c0b29-114">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="c0b29-115">Datové typy data a času zavedené v SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="c0b29-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="c0b29-116">Následující tabulka popisuje nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="c0b29-117">SQL Server datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b29-117">SQL Server data type</span></span>|<span data-ttu-id="c0b29-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b29-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="c0b29-119">Datový typ `date` má 1. ledna 01 do 31. prosince 9999 s přesností 1 den.</span><span class="sxs-lookup"><span data-stu-id="c0b29-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="c0b29-120">Výchozí hodnota je 1. ledna 1900.</span><span class="sxs-lookup"><span data-stu-id="c0b29-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="c0b29-121">Velikost úložiště je 3 bajty.</span><span class="sxs-lookup"><span data-stu-id="c0b29-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="c0b29-122">Datový typ `time` ukládá pouze hodnoty času na základě 24hodinovém času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="c0b29-123">Datový typ `time` má rozsah 00:00:00.0000000 až 23:59:59.9999999 s přesností 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="c0b29-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="c0b29-124">Výchozí hodnota je 00:00:00.0000000 (půlnoc).</span><span class="sxs-lookup"><span data-stu-id="c0b29-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="c0b29-125">Datový typ `time` podporuje uživatelem definovanou zlomkovou přesnost druhé a velikost úložiště se v závislosti na zadané přesnosti liší od 3 do 6 bajtů.</span><span class="sxs-lookup"><span data-stu-id="c0b29-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="c0b29-126">`datetime2` datový typ kombinuje rozsah a přesnost `date` a `time` datových typů do jediného datového typu.</span><span class="sxs-lookup"><span data-stu-id="c0b29-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="c0b29-127">Výchozí hodnoty a formáty řetězcového literálu jsou stejné jako definice v datových typech `date` a `time`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="c0b29-128">Datový typ `datetimeoffset` obsahuje všechny funkce `datetime2` s časovým posunem dalšího časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c0b29-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="c0b29-129">Posun časového pásma je reprezentován jako [+&#124;-] hh: mm.</span><span class="sxs-lookup"><span data-stu-id="c0b29-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="c0b29-130">HH je 2 číslice od 00 do 14, které reprezentují počet hodin v posunu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c0b29-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="c0b29-131">MM je 2 číslice od 00 do 59, které reprezentují počet dalších minut v posunu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c0b29-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="c0b29-132">Formáty času jsou podporovány až 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="c0b29-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="c0b29-133">Povinný symbol + nebo-označuje, zda je posunutí časového pásma přidáno nebo odečteno od času UTC (univerzální časová souřadnice nebo Greenwichský střední čas) k získání místního času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c0b29-134">Další informace o použití klíčového slova `Type System Version` naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="c0b29-135">Formát data a pořadí data</span><span class="sxs-lookup"><span data-stu-id="c0b29-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="c0b29-136">Způsob, jakým SQL Server analyzují hodnoty data a času, nezávisí pouze na typu verze systému a verzi serveru, ale také na výchozím jazykovém nastavení serveru a formátu.</span><span class="sxs-lookup"><span data-stu-id="c0b29-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="c0b29-137">Řetězec kalendářního data, který funguje pro formáty data v jednom jazyku, může být nerozpoznatelný, pokud je dotaz spuštěn pomocí připojení, které používá jiný jazyk a nastavení formátu data.</span><span class="sxs-lookup"><span data-stu-id="c0b29-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="c0b29-138">Příkaz jazyka Transact-SQL SET implicitně nastaví parametr DateFormat, který určuje pořadí částí data.</span><span class="sxs-lookup"><span data-stu-id="c0b29-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="c0b29-139">Pomocí příkazu Transact-SQL SET parametr DateFormat pro připojení můžete určit hodnoty data řazením částí data v pořadí MDY, DMY, YMD, není, MYD nebo DYM.</span><span class="sxs-lookup"><span data-stu-id="c0b29-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="c0b29-140">Pokud pro připojení nezadáte žádné parametr DateFormat, používá SQL Server výchozí jazyk přidružený k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="c0b29-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="c0b29-141">Například řetězec data "01/02/03" by byl interpretován jako MDY (2. ledna 2003) na serveru s nastavením jazyka USA angličtinu a jako DMY (1. února 2003) na serveru s nastavením jazyka britské angličtiny.</span><span class="sxs-lookup"><span data-stu-id="c0b29-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="c0b29-142">Rok je určen pomocí pravidla pro přerušení roku SQL Server, které definuje datum přerušení pro přiřazení hodnoty století.</span><span class="sxs-lookup"><span data-stu-id="c0b29-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="c0b29-143">Další informace najdete v tématu [možnost přerušení dvou číslic v roce](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span><span class="sxs-lookup"><span data-stu-id="c0b29-143">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0b29-144">Formát data není není podporován při převodu z formátu řetězce na `date`, `time`, `datetime2`nebo `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="c0b29-145">Další informace o tom, jak SQL Server interpretuje data data a času, najdete v tématu [použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="c0b29-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="c0b29-146">Datové typy a parametry typu datum/čas</span><span class="sxs-lookup"><span data-stu-id="c0b29-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="c0b29-147">Následující výčty byly přidány do <xref:System.Data.SqlDbType> pro podporu nových datových typů data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="c0b29-148">Můžete určit datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jednoho z předchozích <xref:System.Data.SqlDbType> výčtů.</span><span class="sxs-lookup"><span data-stu-id="c0b29-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span> 

> [!NOTE]
> <span data-ttu-id="c0b29-149">Vlastnost `DbType` `SqlParameter` nelze nastavit na `SqlDbType.Date`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="c0b29-150">Můžete také určit typ <xref:System.Data.SqlClient.SqlParameter> obecně nastavením vlastnosti <xref:System.Data.SqlClient.SqlParameter.DbType%2A> objektu `SqlParameter` na konkrétní hodnotu výčtu <xref:System.Data.DbType>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="c0b29-151">Následující hodnoty výčtu byly přidány do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datových typů:</span><span class="sxs-lookup"><span data-stu-id="c0b29-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="c0b29-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="c0b29-152">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="c0b29-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="c0b29-154">Tyto nové výčty doplňují výčty `Date`, `Time`a `DateTime`, které existovaly v dřívějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0b29-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c0b29-155">Typ poskytovatele .NET Framework dat objektu Parameter je odvozen z .NET Framework typu hodnoty objektu Parameter nebo z `DbType` objektu Parameter...</span><span class="sxs-lookup"><span data-stu-id="c0b29-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="c0b29-156">Nebyly zavedeny žádné nové datové typy <xref:System.Data.SqlTypes> pro podporu nových datových typů data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="c0b29-157">Následující tabulka popisuje mapování mezi datovými typy data a času SQL Server 2008 a datovými typy CLR.</span><span class="sxs-lookup"><span data-stu-id="c0b29-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="c0b29-158">SQL Server datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b29-158">SQL Server data type</span></span>|<span data-ttu-id="c0b29-159">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0b29-159">.NET Framework type</span></span>|<span data-ttu-id="c0b29-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="c0b29-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="c0b29-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="c0b29-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="c0b29-162">date</span><span class="sxs-lookup"><span data-stu-id="c0b29-162">date</span></span>|<span data-ttu-id="c0b29-163">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-163">System.DateTime</span></span>|<span data-ttu-id="c0b29-164">Datum</span><span class="sxs-lookup"><span data-stu-id="c0b29-164">Date</span></span>|<span data-ttu-id="c0b29-165">Datum</span><span class="sxs-lookup"><span data-stu-id="c0b29-165">Date</span></span>|  
|<span data-ttu-id="c0b29-166">time</span><span class="sxs-lookup"><span data-stu-id="c0b29-166">time</span></span>|<span data-ttu-id="c0b29-167">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c0b29-167">System.TimeSpan</span></span>|<span data-ttu-id="c0b29-168">Čas</span><span class="sxs-lookup"><span data-stu-id="c0b29-168">Time</span></span>|<span data-ttu-id="c0b29-169">Čas</span><span class="sxs-lookup"><span data-stu-id="c0b29-169">Time</span></span>|  
|<span data-ttu-id="c0b29-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="c0b29-170">datetime2</span></span>|<span data-ttu-id="c0b29-171">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-171">System.DateTime</span></span>|<span data-ttu-id="c0b29-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="c0b29-172">DateTime2</span></span>|<span data-ttu-id="c0b29-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="c0b29-173">DateTime2</span></span>|  
|<span data-ttu-id="c0b29-174">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-174">datetimeoffset</span></span>|<span data-ttu-id="c0b29-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-175">System.DateTimeOffset</span></span>|<span data-ttu-id="c0b29-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-176">DateTimeOffset</span></span>|<span data-ttu-id="c0b29-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="c0b29-178">datetime</span><span class="sxs-lookup"><span data-stu-id="c0b29-178">datetime</span></span>|<span data-ttu-id="c0b29-179">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-179">System.DateTime</span></span>|<span data-ttu-id="c0b29-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-180">DateTime</span></span>|<span data-ttu-id="c0b29-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-181">DateTime</span></span>|  
|<span data-ttu-id="c0b29-182">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="c0b29-182">smalldatetime</span></span>|<span data-ttu-id="c0b29-183">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-183">System.DateTime</span></span>|<span data-ttu-id="c0b29-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-184">DateTime</span></span>|<span data-ttu-id="c0b29-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="c0b29-186">Vlastnosti SqlParameter</span><span class="sxs-lookup"><span data-stu-id="c0b29-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="c0b29-187">Následující tabulka obsahuje popis `SqlParameter` vlastností, které jsou relevantní pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="c0b29-188">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c0b29-188">Property</span></span>|<span data-ttu-id="c0b29-189">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b29-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="c0b29-190">Získává nebo nastavuje, jestli je hodnota null.</span><span class="sxs-lookup"><span data-stu-id="c0b29-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="c0b29-191">Když odešlete hodnotu parametru s hodnotou null na server, je nutné zadat <xref:System.DBNull>místo `null` (`Nothing` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c0b29-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="c0b29-192">Další informace o hodnotách null databáze naleznete v tématu [zpracování hodnot null](handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="c0b29-192">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="c0b29-193">Získá nebo nastaví maximální počet číslic, které se použijí k reprezentaci hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c0b29-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="c0b29-194">Toto nastavení se ignoruje u datových typů data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="c0b29-195">Získá nebo nastaví počet desetinných míst, na které je vyřešena časová část hodnoty pro `Time`, `DateTime2`a `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="c0b29-196">Výchozí hodnota je 0, což znamená, že skutečné měřítko je odvozeno od hodnoty a odesláno na server.</span><span class="sxs-lookup"><span data-stu-id="c0b29-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="c0b29-197">Ignoruje se pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="c0b29-198">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="c0b29-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="c0b29-199">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="c0b29-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c0b29-200">Hodnoty času, které jsou menší než nula nebo větší než nebo rovny 24 hodinám, budou vyvolat <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="c0b29-201">Vytváření parametrů</span><span class="sxs-lookup"><span data-stu-id="c0b29-201">Creating Parameters</span></span>  
 <span data-ttu-id="c0b29-202">Objekt <xref:System.Data.SqlClient.SqlParameter> lze vytvořit pomocí jeho konstruktoru nebo jeho přidáním do <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním metody `Add` <xref:System.Data.SqlClient.SqlParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="c0b29-203">Metoda `Add` bude přebírat jako vstup buď argumentů konstruktoru, nebo existujícího objektu Parameter.</span><span class="sxs-lookup"><span data-stu-id="c0b29-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="c0b29-204">Následující části tohoto tématu obsahují příklady, jak zadat parametry data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="c0b29-205">Další příklady práce s parametry najdete v tématu [Konfigurace parametrů a datových typů parametrů](../configuring-parameters-and-parameter-data-types.md) a [parametrů DataAdapter](../dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c0b29-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="c0b29-206">Příklad data</span><span class="sxs-lookup"><span data-stu-id="c0b29-206">Date Example</span></span>  
 <span data-ttu-id="c0b29-207">Následující fragment kódu ukazuje, jak zadat parametr `date`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="c0b29-208">Příklad času</span><span class="sxs-lookup"><span data-stu-id="c0b29-208">Time Example</span></span>  
 <span data-ttu-id="c0b29-209">Následující fragment kódu ukazuje, jak zadat parametr `time`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="c0b29-210">Příklad Datetime2</span><span class="sxs-lookup"><span data-stu-id="c0b29-210">Datetime2 Example</span></span>  
 <span data-ttu-id="c0b29-211">Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částmi data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="c0b29-212">Datový příklad DateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="c0b29-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="c0b29-213">Následující fragment kódu ukazuje, jak zadat parametr `DateTimeOffSet` s datem, časem a posunem časového pásma 0.</span><span class="sxs-lookup"><span data-stu-id="c0b29-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="c0b29-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="c0b29-214">AddWithValue</span></span>  
 <span data-ttu-id="c0b29-215">Parametry lze také zadávat pomocí metody `AddWithValue` <xref:System.Data.SqlClient.SqlCommand>, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="c0b29-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="c0b29-216">Metoda `AddWithValue` však neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.</span><span class="sxs-lookup"><span data-stu-id="c0b29-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="c0b29-217">Parametr `@date` mohl na serveru namapovat na datový typ `date`, `datetime`nebo `datetime2`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="c0b29-218">Při práci s novými datovými typy `datetime` musíte explicitně nastavit vlastnost <xref:System.Data.SqlDbType> parametru na datový typ instance.</span><span class="sxs-lookup"><span data-stu-id="c0b29-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="c0b29-219">Použití <xref:System.Data.SqlDbType.Variant> nebo implicitně dodávání hodnot parametrů může způsobit problémy s zpětnou kompatibilitou s datovými typy `datetime` a `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="c0b29-220">Následující tabulka ukazuje, které `SqlDbTypes` jsou odvozeny z typů CLR:</span><span class="sxs-lookup"><span data-stu-id="c0b29-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="c0b29-221">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="c0b29-221">CLR type</span></span>|<span data-ttu-id="c0b29-222">Odvozená SqlDbType</span><span class="sxs-lookup"><span data-stu-id="c0b29-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="c0b29-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-223">DateTime</span></span>|<span data-ttu-id="c0b29-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="c0b29-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="c0b29-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c0b29-225">TimeSpan</span></span>|<span data-ttu-id="c0b29-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="c0b29-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="c0b29-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-227">DateTimeOffset</span></span>|<span data-ttu-id="c0b29-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c0b29-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="c0b29-229">Načítání dat data a času</span><span class="sxs-lookup"><span data-stu-id="c0b29-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="c0b29-230">Následující tabulka popisuje metody, které slouží k načtení hodnot data a času SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c0b29-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="c0b29-231">SqlClient – metoda</span><span class="sxs-lookup"><span data-stu-id="c0b29-231">SqlClient method</span></span>|<span data-ttu-id="c0b29-232">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b29-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="c0b29-233">Načte zadanou hodnotu sloupce jako strukturu <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="c0b29-234">Načte zadanou hodnotu sloupce jako strukturu <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="c0b29-235">Vrátí typ, který je pro pole základní typ specifický pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c0b29-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="c0b29-236">Vrátí stejné typy jako `GetFieldType` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="c0b29-237">Načte hodnotu zadaného sloupce.</span><span class="sxs-lookup"><span data-stu-id="c0b29-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="c0b29-238">Vrátí stejné typy jako `GetValue` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="c0b29-239">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="c0b29-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="c0b29-240">Načte hodnotu sloupce jako <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="c0b29-241">K <xref:System.InvalidCastException> dojde, pokud data nelze vyjádřit jako `SqlString`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="c0b29-242">Načte data sloupce jako výchozí `SqlDbType`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="c0b29-243">Vrátí stejné typy jako `GetValue` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="c0b29-244">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="c0b29-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="c0b29-245">Načte hodnotu sloupce jako řetězec, pokud je systémová verze typu nastavená na SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="c0b29-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="c0b29-246">K <xref:System.InvalidCastException> dojde, pokud data nelze vyjádřit jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b29-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="c0b29-247">Načte zadanou hodnotu sloupce jako strukturu <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="c0b29-248">Načte zadanou hodnotu sloupce jako svůj základní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="c0b29-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="c0b29-249">Načte hodnoty sloupce v poli.</span><span class="sxs-lookup"><span data-stu-id="c0b29-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="c0b29-250">Vrátí <xref:System.Data.DataTable>, který popisuje metadata sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="c0b29-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c0b29-251">Nové `SqlDbTypes` data a času nejsou podporovány pro kód, který provádí vnitroprocesové v procesu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0b29-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="c0b29-252">Pokud je jeden z těchto typů předán serveru, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c0b29-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="c0b29-253">Zadání hodnot data a času jako literálů</span><span class="sxs-lookup"><span data-stu-id="c0b29-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="c0b29-254">Datové typy data a času lze zadat pomocí různých různých formátů řetězcového literálu, které SQL Server poté vyhodnocovány v době běhu a jejich převodem do interních struktur data a času.</span><span class="sxs-lookup"><span data-stu-id="c0b29-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="c0b29-255">SQL Server rozpoznává data data a času uzavřená v jednoduchých uvozovkách (').</span><span class="sxs-lookup"><span data-stu-id="c0b29-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="c0b29-256">Následující příklady ukazují některé formáty:</span><span class="sxs-lookup"><span data-stu-id="c0b29-256">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="c0b29-257">Formáty abecedního data, například `'October 15, 2006'`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="c0b29-258">Číselné formáty data, například `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="c0b29-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="c0b29-259">Nesamostatné formáty řetězců, například `'20061015'`, které by byly interpretovány jako 15. října 2006, pokud používáte standardní formát data standardu ISO.</span><span class="sxs-lookup"><span data-stu-id="c0b29-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0b29-260">Kompletní dokumentaci pro všechny řetězcové literálové formáty a další funkce datových typů data a času můžete najít v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="c0b29-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="c0b29-261">Hodnoty času, které jsou menší než nula nebo větší než nebo rovny 24 hodinám, budou vyvolat <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c0b29-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="c0b29-262">Prostředky v SQL Server Knihy online</span><span class="sxs-lookup"><span data-stu-id="c0b29-262">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="c0b29-263">Další informace o práci s hodnotami data a času v SQL Server najdete v následujících zdrojích informací v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="c0b29-263">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="c0b29-264">Téma</span><span class="sxs-lookup"><span data-stu-id="c0b29-264">Topic</span></span>|<span data-ttu-id="c0b29-265">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b29-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c0b29-266">Datové typy a funkce data a času (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c0b29-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="c0b29-267">Poskytuje přehled všech datových typů a funkcí data a času v jazyce Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c0b29-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="c0b29-268">[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c0b29-268">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="c0b29-269">Poskytuje informace o datových typech a funkcích data a času a příklady jejich použití.</span><span class="sxs-lookup"><span data-stu-id="c0b29-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="c0b29-270">Datové typy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c0b29-270">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="c0b29-271">Popisuje systémové datové typy v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0b29-271">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0b29-272">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0b29-272">See also</span></span>

- [<span data-ttu-id="c0b29-273">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="c0b29-273">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="c0b29-274">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="c0b29-274">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="c0b29-275">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c0b29-275">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="c0b29-276">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c0b29-276">ADO.NET Overview</span></span>](../ado-net-overview.md)
