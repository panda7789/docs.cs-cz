---
title: Kalendářní a časová data
description: Přečtěte si o datových typech pro zpracování informací o datu a čase v Zprostředkovatel dat .NET Framework pro SQL Server.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 9345e995dcb1179e7d0a86f62737f9fda5889f42
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286491"
---
# <a name="date-and-time-data"></a><span data-ttu-id="06380-103">Kalendářní a časová data</span><span class="sxs-lookup"><span data-stu-id="06380-103">Date and Time Data</span></span>
<span data-ttu-id="06380-104">SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času.</span><span class="sxs-lookup"><span data-stu-id="06380-104">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="06380-105">Nové typy dat zahrnují samostatné typy pro datum a čas a rozšířené datové typy s větším rozsahem, přesností a vědomím časového pásma.</span><span class="sxs-lookup"><span data-stu-id="06380-105">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="06380-106">Počínaje verzí 3,5 .NET Framework Service Pack (SP) 1, .NET Framework Zprostředkovatel dat pro SQL Server ( <xref:System.Data.SqlClient> ) poskytuje plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="06380-106">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="06380-107">Abyste mohli používat tyto nové funkce s SqlClient, musíte nainstalovat .NET Framework 3,5 SP1 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="06380-107">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="06380-108">Verze SQL Server starších než SQL Server 2008 obsahovaly jenom dva typy dat pro práci s hodnotami data a času: `datetime` a `smalldatetime` .</span><span class="sxs-lookup"><span data-stu-id="06380-108">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="06380-109">Oba tyto datové typy obsahují jak hodnotu data, tak časovou hodnotu, což usnadňuje práci s pouze hodnotami data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-109">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="06380-110">Tyto datové typy také podporují data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v 1753.</span><span class="sxs-lookup"><span data-stu-id="06380-110">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="06380-111">Dalším omezením je, že tyto starší datové typy nejsou v časovém pásmu. díky tomu je obtížné pracovat s daty, která pocházejí z několika časových pásem.</span><span class="sxs-lookup"><span data-stu-id="06380-111">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="06380-112">Kompletní dokumentace pro SQL Server datové typy jsou k dispozici v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="06380-112">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="06380-113">V následující tabulce jsou uvedena témata o vstupní úrovni pro konkrétní verzi pro data data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-113">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="06380-114">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="06380-114">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="06380-115">[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="06380-115">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="06380-116">Datové typy data a času zavedené v SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="06380-116">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="06380-117">Následující tabulka popisuje nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-117">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="06380-118">SQL Server datový typ</span><span class="sxs-lookup"><span data-stu-id="06380-118">SQL Server data type</span></span>|<span data-ttu-id="06380-119">Popis</span><span class="sxs-lookup"><span data-stu-id="06380-119">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="06380-120">`date`Datový typ je v rozsahu od 1. ledna 01 do 31. prosince 9999 s přesností 1 den.</span><span class="sxs-lookup"><span data-stu-id="06380-120">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="06380-121">Výchozí hodnota je 1. ledna 1900.</span><span class="sxs-lookup"><span data-stu-id="06380-121">The default value is January 1, 1900.</span></span> <span data-ttu-id="06380-122">Velikost úložiště je 3 bajty.</span><span class="sxs-lookup"><span data-stu-id="06380-122">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="06380-123">`time`Datový typ ukládá pouze hodnoty času na základě 24hodinovém času.</span><span class="sxs-lookup"><span data-stu-id="06380-123">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="06380-124">`time`Datový typ má rozsah 00:00:00.0000000 až 23:59:59.9999999 s přesností 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="06380-124">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="06380-125">Výchozí hodnota je 00:00:00.0000000 (půlnoc).</span><span class="sxs-lookup"><span data-stu-id="06380-125">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="06380-126">`time`Datový typ podporuje uživatelem definovanou zlomkovou přesnost druhé a velikost úložiště se v závislosti na zadané přesnosti liší od 3 do 6 bajtů.</span><span class="sxs-lookup"><span data-stu-id="06380-126">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="06380-127">`datetime2`Datový typ kombinuje rozsah a přesnost `date` `time` datových typů a do jediného datového typu.</span><span class="sxs-lookup"><span data-stu-id="06380-127">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="06380-128">Výchozí hodnoty a formáty řetězcového literálu jsou stejné jako definice v `date` `time` datových typech a.</span><span class="sxs-lookup"><span data-stu-id="06380-128">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="06380-129">`datetimeoffset`Datový typ obsahuje všechny funkce `datetime2` s dalším posunem časového pásma.</span><span class="sxs-lookup"><span data-stu-id="06380-129">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="06380-130">Posun časového pásma je reprezentován jako [+&#124;-] HH: MM.</span><span class="sxs-lookup"><span data-stu-id="06380-130">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="06380-131">HH je 2 číslice od 00 do 14, které reprezentují počet hodin v posunu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="06380-131">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="06380-132">MM je 2 číslice od 00 do 59, které reprezentují počet dalších minut v posunu časového pásma.</span><span class="sxs-lookup"><span data-stu-id="06380-132">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="06380-133">Formáty času jsou podporovány až 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="06380-133">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="06380-134">Povinný symbol + nebo-označuje, zda je posunutí časového pásma přidáno nebo odečteno od času UTC (univerzální časová souřadnice nebo Greenwichský střední čas) k získání místního času.</span><span class="sxs-lookup"><span data-stu-id="06380-134">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="06380-135">Další informace o použití `Type System Version` klíčového slova naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> .</span><span class="sxs-lookup"><span data-stu-id="06380-135">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="06380-136">Formát data a pořadí data</span><span class="sxs-lookup"><span data-stu-id="06380-136">Date Format and Date Order</span></span>  
 <span data-ttu-id="06380-137">Způsob, jakým SQL Server analyzují hodnoty data a času, nezávisí pouze na typu verze systému a verzi serveru, ale také na výchozím jazykovém nastavení serveru a formátu.</span><span class="sxs-lookup"><span data-stu-id="06380-137">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="06380-138">Řetězec kalendářního data, který funguje pro formáty data v jednom jazyku, může být nerozpoznatelný, pokud je dotaz spuštěn pomocí připojení, které používá jiný jazyk a nastavení formátu data.</span><span class="sxs-lookup"><span data-stu-id="06380-138">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="06380-139">Příkaz jazyka Transact-SQL SET implicitně nastaví parametr DateFormat, který určuje pořadí částí data.</span><span class="sxs-lookup"><span data-stu-id="06380-139">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="06380-140">Pomocí příkazu Transact-SQL SET parametr DateFormat pro připojení můžete určit hodnoty data řazením částí data v pořadí MDY, DMY, YMD, není, MYD nebo DYM.</span><span class="sxs-lookup"><span data-stu-id="06380-140">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="06380-141">Pokud pro připojení nezadáte žádné parametr DateFormat, používá SQL Server výchozí jazyk přidružený k tomuto připojení.</span><span class="sxs-lookup"><span data-stu-id="06380-141">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="06380-142">Například řetězec data "01/02/03" by byl interpretován jako MDY (2. ledna 2003) na serveru s nastavením jazyka USA angličtinu a jako DMY (1. února 2003) na serveru s nastavením jazyka britské angličtiny.</span><span class="sxs-lookup"><span data-stu-id="06380-142">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="06380-143">Rok je určen pomocí pravidla pro přerušení roku SQL Server, které definuje datum přerušení pro přiřazení hodnoty století.</span><span class="sxs-lookup"><span data-stu-id="06380-143">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="06380-144">Další informace najdete v tématu [možnost přerušení dvou číslic v roce](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span><span class="sxs-lookup"><span data-stu-id="06380-144">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06380-145">Formát data není není podporován při převodu z formátu řetězce na `date` ,, `time` `datetime2` nebo `datetimeoffset` .</span><span class="sxs-lookup"><span data-stu-id="06380-145">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="06380-146">Další informace o tom, jak SQL Server interpretuje data data a času, najdete v tématu [použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="06380-146">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="06380-147">Datové typy a parametry typu datum/čas</span><span class="sxs-lookup"><span data-stu-id="06380-147">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="06380-148">Následující výčty byly přidány do <xref:System.Data.SqlDbType> pro podporu nových datových typů data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-148">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="06380-149">Můžete zadat datový typ pro pomocí <xref:System.Data.SqlClient.SqlParameter> jednoho z předchozích <xref:System.Data.SqlDbType> výčtů.</span><span class="sxs-lookup"><span data-stu-id="06380-149">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span>

> [!NOTE]
> <span data-ttu-id="06380-150">Vlastnost nelze nastavit `DbType` `SqlParameter` na hodnotu `SqlDbType.Date` .</span><span class="sxs-lookup"><span data-stu-id="06380-150">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="06380-151">Můžete také určit typ obecného typu nastavením <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter.DbType%2A> vlastnosti `SqlParameter` objektu na konkrétní <xref:System.Data.DbType> hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="06380-151">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="06380-152">Následující hodnoty výčtu byly přidány do <xref:System.Data.DbType> pro podporu `datetime2` `datetimeoffset` datových typů a:</span><span class="sxs-lookup"><span data-stu-id="06380-152">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="06380-153">DbType. DateTime2</span><span class="sxs-lookup"><span data-stu-id="06380-153">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="06380-154">DbType. DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-154">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="06380-155">Tyto nové výčty doplňují `Date` `Time` výčty, a, `DateTime` které existovaly v dřívějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06380-155">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="06380-156">Typ zprostředkovatele dat .NET Framework objektu parametru je odvozen z .NET Frameworkho typu hodnoty objektu Parameter nebo z `DbType` objektu Parameter.</span><span class="sxs-lookup"><span data-stu-id="06380-156">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="06380-157">Nebyly <xref:System.Data.SqlTypes> zavedeny žádné nové datové typy pro podporu nových datových typů data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-157">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="06380-158">Následující tabulka popisuje mapování mezi datovými typy data a času SQL Server 2008 a datovými typy CLR.</span><span class="sxs-lookup"><span data-stu-id="06380-158">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="06380-159">SQL Server datový typ</span><span class="sxs-lookup"><span data-stu-id="06380-159">SQL Server data type</span></span>|<span data-ttu-id="06380-160">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06380-160">.NET Framework type</span></span>|<span data-ttu-id="06380-161">System. data. SqlDbType</span><span class="sxs-lookup"><span data-stu-id="06380-161">System.Data.SqlDbType</span></span>|<span data-ttu-id="06380-162">System. data. DbType</span><span class="sxs-lookup"><span data-stu-id="06380-162">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="06380-163">date</span><span class="sxs-lookup"><span data-stu-id="06380-163">date</span></span>|<span data-ttu-id="06380-164">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-164">System.DateTime</span></span>|<span data-ttu-id="06380-165">Datum</span><span class="sxs-lookup"><span data-stu-id="06380-165">Date</span></span>|<span data-ttu-id="06380-166">Datum</span><span class="sxs-lookup"><span data-stu-id="06380-166">Date</span></span>|  
|<span data-ttu-id="06380-167">time</span><span class="sxs-lookup"><span data-stu-id="06380-167">time</span></span>|<span data-ttu-id="06380-168">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="06380-168">System.TimeSpan</span></span>|<span data-ttu-id="06380-169">Čas</span><span class="sxs-lookup"><span data-stu-id="06380-169">Time</span></span>|<span data-ttu-id="06380-170">Čas</span><span class="sxs-lookup"><span data-stu-id="06380-170">Time</span></span>|  
|<span data-ttu-id="06380-171">datetime2</span><span class="sxs-lookup"><span data-stu-id="06380-171">datetime2</span></span>|<span data-ttu-id="06380-172">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-172">System.DateTime</span></span>|<span data-ttu-id="06380-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="06380-173">DateTime2</span></span>|<span data-ttu-id="06380-174">DateTime2</span><span class="sxs-lookup"><span data-stu-id="06380-174">DateTime2</span></span>|  
|<span data-ttu-id="06380-175">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-175">datetimeoffset</span></span>|<span data-ttu-id="06380-176">System. DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-176">System.DateTimeOffset</span></span>|<span data-ttu-id="06380-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-177">DateTimeOffset</span></span>|<span data-ttu-id="06380-178">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-178">DateTimeOffset</span></span>|  
|<span data-ttu-id="06380-179">datetime</span><span class="sxs-lookup"><span data-stu-id="06380-179">datetime</span></span>|<span data-ttu-id="06380-180">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-180">System.DateTime</span></span>|<span data-ttu-id="06380-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-181">DateTime</span></span>|<span data-ttu-id="06380-182">DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-182">DateTime</span></span>|  
|<span data-ttu-id="06380-183">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="06380-183">smalldatetime</span></span>|<span data-ttu-id="06380-184">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-184">System.DateTime</span></span>|<span data-ttu-id="06380-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-185">DateTime</span></span>|<span data-ttu-id="06380-186">DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-186">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="06380-187">Vlastnosti SqlParameter</span><span class="sxs-lookup"><span data-stu-id="06380-187">SqlParameter Properties</span></span>  
 <span data-ttu-id="06380-188">Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-188">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="06380-189">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="06380-189">Property</span></span>|<span data-ttu-id="06380-190">Popis</span><span class="sxs-lookup"><span data-stu-id="06380-190">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="06380-191">Získává nebo nastavuje, jestli je hodnota null.</span><span class="sxs-lookup"><span data-stu-id="06380-191">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="06380-192">Když odešlete hodnotu parametru s hodnotou null na server, je nutné zadat <xref:System.DBNull> místo `null` ( `Nothing` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="06380-192">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="06380-193">Další informace o hodnotách null databáze naleznete v tématu [zpracování hodnot null](handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="06380-193">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="06380-194">Získá nebo nastaví maximální počet číslic, které se použijí k reprezentaci hodnoty.</span><span class="sxs-lookup"><span data-stu-id="06380-194">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="06380-195">Toto nastavení se ignoruje u datových typů data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-195">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="06380-196">Získá nebo nastaví počet desetinných míst, na které se vyřeší časová část hodnoty pro `Time` , `DateTime2` a `DateTimeOffset` .</span><span class="sxs-lookup"><span data-stu-id="06380-196">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="06380-197">Výchozí hodnota je 0, což znamená, že skutečné měřítko je odvozeno od hodnoty a odesláno na server.</span><span class="sxs-lookup"><span data-stu-id="06380-197">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="06380-198">Ignoruje se pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-198">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="06380-199">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="06380-199">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="06380-200">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="06380-200">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="06380-201">Hodnoty času, které jsou menší než nula nebo větší než nebo rovny 24 hodinám, budou vyvolat <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="06380-201">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="06380-202">Vytváření parametrů</span><span class="sxs-lookup"><span data-stu-id="06380-202">Creating Parameters</span></span>  
 <span data-ttu-id="06380-203">Můžete vytvořit <xref:System.Data.SqlClient.SqlParameter> objekt pomocí jeho konstruktoru nebo jeho přidáním do <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním `Add` metody <xref:System.Data.SqlClient.SqlParameterCollection> .</span><span class="sxs-lookup"><span data-stu-id="06380-203">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="06380-204">`Add`Metoda provede jako vstup buď argumenty konstruktoru, nebo existující objekt parametru.</span><span class="sxs-lookup"><span data-stu-id="06380-204">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="06380-205">Následující části tohoto tématu obsahují příklady, jak zadat parametry data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-205">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="06380-206">Další příklady práce s parametry najdete v tématu [Konfigurace parametrů a datových typů parametrů](../configuring-parameters-and-parameter-data-types.md) a [parametrů DataAdapter](../dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="06380-206">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="06380-207">Příklad data</span><span class="sxs-lookup"><span data-stu-id="06380-207">Date Example</span></span>  
 <span data-ttu-id="06380-208">Následující fragment kódu ukazuje, jak zadat `date` parametr.</span><span class="sxs-lookup"><span data-stu-id="06380-208">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="06380-209">Příklad času</span><span class="sxs-lookup"><span data-stu-id="06380-209">Time Example</span></span>  
 <span data-ttu-id="06380-210">Následující fragment kódu ukazuje, jak zadat `time` parametr.</span><span class="sxs-lookup"><span data-stu-id="06380-210">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="06380-211">Příklad Datetime2</span><span class="sxs-lookup"><span data-stu-id="06380-211">Datetime2 Example</span></span>  
 <span data-ttu-id="06380-212">Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částmi data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-212">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="06380-213">Datový příklad DateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="06380-213">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="06380-214">Následující fragment kódu ukazuje, jak zadat `DateTimeOffSet` parametr s datem, časem a posunem časového pásma 0.</span><span class="sxs-lookup"><span data-stu-id="06380-214">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="06380-215">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="06380-215">AddWithValue</span></span>  
 <span data-ttu-id="06380-216">Parametry lze také zadávat pomocí `AddWithValue` metody <xref:System.Data.SqlClient.SqlCommand> , jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="06380-216">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="06380-217">`AddWithValue`Metoda ale neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.</span><span class="sxs-lookup"><span data-stu-id="06380-217">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="06380-218">`@date`Parametr může být namapován na `date` `datetime` datový typ, nebo `datetime2` na serveru.</span><span class="sxs-lookup"><span data-stu-id="06380-218">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="06380-219">Při práci s novými `datetime` datovými typy musíte explicitně nastavit <xref:System.Data.SqlDbType> vlastnost parametru na datový typ instance.</span><span class="sxs-lookup"><span data-stu-id="06380-219">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="06380-220">Použití <xref:System.Data.SqlDbType.Variant> nebo implicitní zadání hodnot parametrů může způsobit problémy s zpětnou kompatibilitou s `datetime` `smalldatetime` datovými typy a.</span><span class="sxs-lookup"><span data-stu-id="06380-220">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="06380-221">Následující tabulka ukazuje, které `SqlDbTypes` typy CLR jsou odvozeny:</span><span class="sxs-lookup"><span data-stu-id="06380-221">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="06380-222">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="06380-222">CLR type</span></span>|<span data-ttu-id="06380-223">Odvozená SqlDbType</span><span class="sxs-lookup"><span data-stu-id="06380-223">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="06380-224">DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-224">DateTime</span></span>|<span data-ttu-id="06380-225">SqlDbType. DateTime</span><span class="sxs-lookup"><span data-stu-id="06380-225">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="06380-226">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="06380-226">TimeSpan</span></span>|<span data-ttu-id="06380-227">SqlDbType. time</span><span class="sxs-lookup"><span data-stu-id="06380-227">SqlDbType.Time</span></span>|  
|<span data-ttu-id="06380-228">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-228">DateTimeOffset</span></span>|<span data-ttu-id="06380-229">SqlDbType. DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06380-229">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="06380-230">Načítání dat data a času</span><span class="sxs-lookup"><span data-stu-id="06380-230">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="06380-231">Následující tabulka popisuje metody, které slouží k načtení hodnot data a času SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="06380-231">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="06380-232">SqlClient – metoda</span><span class="sxs-lookup"><span data-stu-id="06380-232">SqlClient method</span></span>|<span data-ttu-id="06380-233">Popis</span><span class="sxs-lookup"><span data-stu-id="06380-233">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="06380-234">Načte zadanou hodnotu sloupce jako <xref:System.DateTime> strukturu.</span><span class="sxs-lookup"><span data-stu-id="06380-234">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="06380-235">Načte zadanou hodnotu sloupce jako <xref:System.DateTimeOffset> strukturu.</span><span class="sxs-lookup"><span data-stu-id="06380-235">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="06380-236">Vrátí typ, který je pro pole základní typ specifický pro poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="06380-236">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="06380-237">Vrátí stejné typy jako `GetFieldType` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-237">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="06380-238">Načte hodnotu zadaného sloupce.</span><span class="sxs-lookup"><span data-stu-id="06380-238">Retrieves the value of the specified column.</span></span> <span data-ttu-id="06380-239">Vrátí stejné typy jako `GetValue` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-239">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="06380-240">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="06380-240">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="06380-241">Načte hodnotu sloupce jako <xref:System.Data.SqlTypes.SqlString> .</span><span class="sxs-lookup"><span data-stu-id="06380-241">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="06380-242"><xref:System.InvalidCastException>Dojde k tomu v případě, že data nelze vyjádřit jako `SqlString` .</span><span class="sxs-lookup"><span data-stu-id="06380-242">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="06380-243">Načte data sloupce jako výchozí `SqlDbType` .</span><span class="sxs-lookup"><span data-stu-id="06380-243">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="06380-244">Vrátí stejné typy jako `GetValue` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-244">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="06380-245">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="06380-245">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="06380-246">Načte hodnotu sloupce jako řetězec, pokud je systémová verze typu nastavená na SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="06380-246">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="06380-247"><xref:System.InvalidCastException>Dojde k tomu v případě, že data nelze vyjádřit jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="06380-247">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="06380-248">Načte zadanou hodnotu sloupce jako <xref:System.TimeSpan> strukturu.</span><span class="sxs-lookup"><span data-stu-id="06380-248">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="06380-249">Načte zadanou hodnotu sloupce jako svůj základní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="06380-249">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="06380-250">Načte hodnoty sloupce v poli.</span><span class="sxs-lookup"><span data-stu-id="06380-250">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="06380-251">Vrátí <xref:System.Data.DataTable> , který popisuje metadata sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="06380-251">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="06380-252">Nové datum a čas `SqlDbTypes` nejsou podporovány pro kód, který je spuštěn v procesu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="06380-252">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="06380-253">Pokud je jeden z těchto typů předán serveru, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="06380-253">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="06380-254">Zadání hodnot data a času jako literálů</span><span class="sxs-lookup"><span data-stu-id="06380-254">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="06380-255">Datové typy data a času lze zadat pomocí různých různých formátů řetězcového literálu, které SQL Server poté vyhodnocovány v době běhu a jejich převodem do interních struktur data a času.</span><span class="sxs-lookup"><span data-stu-id="06380-255">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="06380-256">SQL Server rozpoznává data data a času uzavřená v jednoduchých uvozovkách (').</span><span class="sxs-lookup"><span data-stu-id="06380-256">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="06380-257">Následující příklady ukazují některé formáty:</span><span class="sxs-lookup"><span data-stu-id="06380-257">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="06380-258">Formáty abecedního data, například `'October 15, 2006'` .</span><span class="sxs-lookup"><span data-stu-id="06380-258">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="06380-259">Číselné formáty kalendářních dat, například `'10/15/2006'` .</span><span class="sxs-lookup"><span data-stu-id="06380-259">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="06380-260">Neoddělené formáty řetězců, například `'20061015'` , které by byly interpretovány jako 15. října 2006, pokud používáte standardní formát data standardu ISO.</span><span class="sxs-lookup"><span data-stu-id="06380-260">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06380-261">Kompletní dokumentaci pro všechny řetězcové literálové formáty a další funkce datových typů data a času můžete najít v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="06380-261">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="06380-262">Hodnoty času, které jsou menší než nula nebo větší než nebo rovny 24 hodinám, budou vyvolat <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="06380-262">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="06380-263">Prostředky v SQL Server Knihy online</span><span class="sxs-lookup"><span data-stu-id="06380-263">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="06380-264">Další informace o práci s hodnotami data a času v SQL Server najdete v následujících zdrojích informací v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="06380-264">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="06380-265">Téma</span><span class="sxs-lookup"><span data-stu-id="06380-265">Topic</span></span>|<span data-ttu-id="06380-266">Popis</span><span class="sxs-lookup"><span data-stu-id="06380-266">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="06380-267">Datové typy a funkce data a času (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06380-267">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="06380-268">Poskytuje přehled všech datových typů a funkcí data a času v jazyce Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="06380-268">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="06380-269">[Použití dat data a času](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="06380-269">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="06380-270">Poskytuje informace o datových typech a funkcích data a času a příklady jejich použití.</span><span class="sxs-lookup"><span data-stu-id="06380-270">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="06380-271">Datové typy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06380-271">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="06380-272">Popisuje systémové datové typy v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="06380-272">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06380-273">Viz také</span><span class="sxs-lookup"><span data-stu-id="06380-273">See also</span></span>

- [<span data-ttu-id="06380-274">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="06380-274">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="06380-275">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="06380-275">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="06380-276">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="06380-276">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="06380-277">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="06380-277">ADO.NET Overview</span></span>](../ado-net-overview.md)
