---
title: Kalendářní a časová Data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 34d49416bb7d0da60624a1f60e4dbd01a1dff9cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584542"
---
# <a name="date-and-time-data"></a><span data-ttu-id="69885-102">Kalendářní a časová Data</span><span class="sxs-lookup"><span data-stu-id="69885-102">Date and Time Data</span></span>
<span data-ttu-id="69885-103">SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času.</span><span class="sxs-lookup"><span data-stu-id="69885-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="69885-104">Nové datové typy zahrnují rozšířené datové typy s větší rozsah, přesnost a časové pásmo a samostatné typy pro datum a čas.</span><span class="sxs-lookup"><span data-stu-id="69885-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="69885-105">Od verze rozhraní .NET Framework 3.5 Service Pack (SP) 1, zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje plnou podporu pro všechny nové funkce databázového stroje SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="69885-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="69885-106">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro použití těchto nových funkcí s SqlClient.</span><span class="sxs-lookup"><span data-stu-id="69885-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="69885-107">Verze systému SQL Server starších než SQL Server 2008 platili jen dva datové typy pro práci s hodnotami data a času: `datetime` a `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="69885-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="69885-108">Oba tyto typy dat obsahovat hodnotu data a hodnotu času, které je těžké pracovat pouze datum nebo pouze hodnoty času.</span><span class="sxs-lookup"><span data-stu-id="69885-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="69885-109">Tyto typy dat také podporují jenom data, ke kterým dochází po zavedení gregoriánského kalendáře v Anglii v 1753.</span><span class="sxs-lookup"><span data-stu-id="69885-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="69885-110">Další omezení je, že tyto starší typy dat nejsou časového pásma vědět, které je těžké pracovat s daty, která pochází z více časových pásem.</span><span class="sxs-lookup"><span data-stu-id="69885-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="69885-111">Úplnou dokumentaci pro datové typy serveru SQL Server je k dispozici v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="69885-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="69885-112">V následující tabulce jsou uvedeny základní témata specifické pro verzi pro data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="69885-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="69885-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="69885-114">Pomocí kalendářní a časová Data</span><span class="sxs-lookup"><span data-stu-id="69885-114">Using Date and Time Data</span></span>](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="69885-115">Datum a čas datové typy zavedena v systému SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="69885-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="69885-116">Následující tabulka popisuje nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="69885-117">Datový typ SQL serveru</span><span class="sxs-lookup"><span data-stu-id="69885-117">SQL Server data type</span></span>|<span data-ttu-id="69885-118">Popis</span><span class="sxs-lookup"><span data-stu-id="69885-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="69885-119">`date` Datový typ má rozsah od 1. ledna, 01 do 31. prosince 9999 s přesností na 1 den.</span><span class="sxs-lookup"><span data-stu-id="69885-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="69885-120">Výchozí hodnota je 1. ledna 1900.</span><span class="sxs-lookup"><span data-stu-id="69885-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="69885-121">Velikost úložiště je 3 bajtů.</span><span class="sxs-lookup"><span data-stu-id="69885-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="69885-122">`time` Datový typ ukládá časové hodnoty, podle 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="69885-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="69885-123">`time` Typ dat nabízí řadu 00:00:00.0000000 prostřednictvím 23:59:59.9999999 s přesností na 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="69885-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="69885-124">Výchozí hodnota je 00:00:00.0000000 (půlnoc).</span><span class="sxs-lookup"><span data-stu-id="69885-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="69885-125">`time` Podporuje uživatelem definované zlomková přesnost pro sekundy datový typ a velikost úložiště se liší od 3 do 6 bajtů podle Zadaná přesnost.</span><span class="sxs-lookup"><span data-stu-id="69885-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="69885-126">`datetime2` Datový typ kombinuje rozsah a přesnost `date` a `time` datové typy do jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="69885-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="69885-127">Výchozí hodnoty a řetězec literálu formáty jsou stejné jako s těmi definovanými ve `date` a `time` datové typy.</span><span class="sxs-lookup"><span data-stu-id="69885-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="69885-128">`datetimeoffset` Datového typu obsahuje všechny funkce `datetime2` s posunem další časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="69885-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="69885-129">Posun časového pásma je vyjádřena jako [+&#124;-] hh: mm.</span><span class="sxs-lookup"><span data-stu-id="69885-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="69885-130">HH jsou 2 číslic od 00 do 14, které představují počet hodin v posun časového pásma.</span><span class="sxs-lookup"><span data-stu-id="69885-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="69885-131">MM je 2 soustavě v rozsahu od 00 do 59 představující počet dalších minut v posun časového pásma.</span><span class="sxs-lookup"><span data-stu-id="69885-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="69885-132">Formáty času jsou podporovány na 100 nanosekund.</span><span class="sxs-lookup"><span data-stu-id="69885-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="69885-133">Povinné + nebo - znak označuje, zda je posun v časových pásmech přičíst nebo odečíst od času UTC (světový čas koordinovat nebo greenwichský střední čas) k získání místní čas.</span><span class="sxs-lookup"><span data-stu-id="69885-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="69885-134">Další informace o používání `Type System Version` – klíčové slovo, naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="69885-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="69885-135">Formát data a pořadí v datu</span><span class="sxs-lookup"><span data-stu-id="69885-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="69885-136">Jak analyzuje hodnoty data a času v systému SQL Server závisí nejen na verzi systému typu a verzi serveru, ale také na jazyk a formát výchozí nastavení serveru.</span><span class="sxs-lookup"><span data-stu-id="69885-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="69885-137">Řetězec data, může být nelze rozpoznat, pokud se dotaz provádí na připojení funguje pro formáty data z jednoho jazyka, který používá jiný jazyk a formát data nastavení.</span><span class="sxs-lookup"><span data-stu-id="69885-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="69885-138">Příkaz jazyka Transact-SQL příkaz SET LANGUAGE se implicitně nastaví parametr DATEFORMAT, který určuje pořadí částí data.</span><span class="sxs-lookup"><span data-stu-id="69885-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="69885-139">Příkaz nastavit parametr DATEFORMAT příkazů jazyka Transact-SQL můžete použít na připojení k rozlišení hodnot data podle pořadí částí data v objednávce MDR, DMY, RMD, typy, MYD nebo DYM.</span><span class="sxs-lookup"><span data-stu-id="69885-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="69885-140">Pokud nezadáte žádné parametr DATEFORMAT pro připojení, SQL Server používá výchozí jazyk přidružený k připojení.</span><span class="sxs-lookup"><span data-stu-id="69885-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="69885-141">Například řetězec data 01/02/03 "je interpretován jako formát MDR (2. ledna 2003) na serveru s nastavením jazyk angličtinu Spojených států a jako DMY (1. února 2003) na serveru s nastavením jazyka britské angličtiny.</span><span class="sxs-lookup"><span data-stu-id="69885-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="69885-142">Rok je určen pomocí systému SQL Server přerušení rok pravidla, která definuje než datum přerušení pro přiřazení hodnoty století.</span><span class="sxs-lookup"><span data-stu-id="69885-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="69885-143">Další informace najdete v tématu [dvě číslici roce přerušení možnost](https://go.microsoft.com/fwlink/?LinkId=120473) v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="69885-143">For more information, see [two digit year cutoff Option](https://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69885-144">Formát data typy není podporován při převodu z formátu řetězce na `date`, `time`, `datetime2`, nebo `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="69885-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="69885-145">Další informace o interpretace data a času v systému SQL Server najdete v tématu [pomocí kalendářní a časová Data](https://go.microsoft.com/fwlink/?LinkID=98361) SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="69885-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="69885-146">Datum/čas typy a parametry</span><span class="sxs-lookup"><span data-stu-id="69885-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="69885-147">Následující výčty jsou přidané do <xref:System.Data.SqlDbType> pro podporu nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="69885-148">Můžete zadat datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jednoho z předchozích <xref:System.Data.SqlDbType> výčty.</span><span class="sxs-lookup"><span data-stu-id="69885-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span> 

> [!NOTE]
> <span data-ttu-id="69885-149">Nelze nastavit `DbType` vlastnost `SqlParameter` k `SqlDbType.Date`.</span><span class="sxs-lookup"><span data-stu-id="69885-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="69885-150">Můžete také zadat typ <xref:System.Data.SqlClient.SqlParameter> obecně tak, že nastavíte <xref:System.Data.SqlClient.SqlParameter.DbType%2A> vlastnost `SqlParameter` objekt ke konkrétní <xref:System.Data.DbType> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="69885-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="69885-151">Následující hodnoty výčtu jsou přidané do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datové typy:</span><span class="sxs-lookup"><span data-stu-id="69885-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
-   <span data-ttu-id="69885-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="69885-152">DbType.DateTime2</span></span>  
  
-   <span data-ttu-id="69885-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="69885-154">Tyto nové výčty doplnit `Date`, `Time`, a `DateTime` výčty, které existovaly ve starších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69885-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="69885-155">Typ zprostředkovatele dat .NET Framework parametr objektu je odvozen z rozhraní .NET Framework typ hodnoty parametru objektu nebo z `DbType` parametr objektu.</span><span class="sxs-lookup"><span data-stu-id="69885-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="69885-156">Žádná nová <xref:System.Data.SqlTypes> byly uvedeny datové typy pro podporu nové datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="69885-157">Následující tabulka popisuje mapování mezi SQL Server 2008 datum a čas datových typů a datové typy CLR.</span><span class="sxs-lookup"><span data-stu-id="69885-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="69885-158">Datový typ SQL serveru</span><span class="sxs-lookup"><span data-stu-id="69885-158">SQL Server data type</span></span>|<span data-ttu-id="69885-159">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="69885-159">.NET Framework type</span></span>|<span data-ttu-id="69885-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="69885-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="69885-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="69885-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="69885-162">Datum</span><span class="sxs-lookup"><span data-stu-id="69885-162">date</span></span>|<span data-ttu-id="69885-163">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-163">System.DateTime</span></span>|<span data-ttu-id="69885-164">Datum</span><span class="sxs-lookup"><span data-stu-id="69885-164">Date</span></span>|<span data-ttu-id="69885-165">Datum</span><span class="sxs-lookup"><span data-stu-id="69885-165">Date</span></span>|  
|<span data-ttu-id="69885-166">čas</span><span class="sxs-lookup"><span data-stu-id="69885-166">time</span></span>|<span data-ttu-id="69885-167">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="69885-167">System.TimeSpan</span></span>|<span data-ttu-id="69885-168">Čas</span><span class="sxs-lookup"><span data-stu-id="69885-168">Time</span></span>|<span data-ttu-id="69885-169">Čas</span><span class="sxs-lookup"><span data-stu-id="69885-169">Time</span></span>|  
|<span data-ttu-id="69885-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="69885-170">datetime2</span></span>|<span data-ttu-id="69885-171">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-171">System.DateTime</span></span>|<span data-ttu-id="69885-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="69885-172">DateTime2</span></span>|<span data-ttu-id="69885-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="69885-173">DateTime2</span></span>|  
|<span data-ttu-id="69885-174">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-174">datetimeoffset</span></span>|<span data-ttu-id="69885-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-175">System.DateTimeOffset</span></span>|<span data-ttu-id="69885-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-176">DateTimeOffset</span></span>|<span data-ttu-id="69885-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="69885-178">datetime</span><span class="sxs-lookup"><span data-stu-id="69885-178">datetime</span></span>|<span data-ttu-id="69885-179">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-179">System.DateTime</span></span>|<span data-ttu-id="69885-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-180">DateTime</span></span>|<span data-ttu-id="69885-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-181">DateTime</span></span>|  
|<span data-ttu-id="69885-182">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="69885-182">smalldatetime</span></span>|<span data-ttu-id="69885-183">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-183">System.DateTime</span></span>|<span data-ttu-id="69885-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-184">DateTime</span></span>|<span data-ttu-id="69885-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="69885-186">Vlastnosti SqlParameter</span><span class="sxs-lookup"><span data-stu-id="69885-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="69885-187">Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="69885-188">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="69885-188">Property</span></span>|<span data-ttu-id="69885-189">Popis</span><span class="sxs-lookup"><span data-stu-id="69885-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="69885-190">Získá nebo nastaví, zda je hodnota s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="69885-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="69885-191">Pokud je hodnota null parametru posíláte na server, je třeba zadat <xref:System.DBNull>, spíše než `null` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="69885-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="69885-192">Další informace o databázi hodnoty Null, naleznete v tématu [zpracování hodnot Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="69885-192">For more information about database nulls, see [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="69885-193">Získá nebo nastaví maximální počet číslic, na které se používá k reprezentování hodnota.</span><span class="sxs-lookup"><span data-stu-id="69885-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="69885-194">Toto nastavení se ignoruje pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="69885-195">Získá nebo nastaví počet desetinných míst, na které je časová část hodnoty pro `Time`, `DateTime2`, a `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="69885-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="69885-196">Výchozí hodnota je 0, což znamená, že skutečné škálování je odvozen z hodnoty a odeslat na server.</span><span class="sxs-lookup"><span data-stu-id="69885-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="69885-197">Ignorovat pro datové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="69885-198">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="69885-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="69885-199">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="69885-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="69885-200">Vyvolá výjimku časové hodnoty, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="69885-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="69885-201">Vytváří se parametry</span><span class="sxs-lookup"><span data-stu-id="69885-201">Creating Parameters</span></span>  
 <span data-ttu-id="69885-202">Můžete vytvořit <xref:System.Data.SqlClient.SqlParameter> objektu pomocí jeho konstruktoru, nebo jejím přidáním na <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním `Add` metodu <xref:System.Data.SqlClient.SqlParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="69885-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="69885-203">`Add` Metoda vezme jako vstupní argumenty konstruktoru nebo existující objekt parametru.</span><span class="sxs-lookup"><span data-stu-id="69885-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="69885-204">Další části v tomto tématu obsahují příklady toho, jak zadat datum a čas parametry.</span><span class="sxs-lookup"><span data-stu-id="69885-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="69885-205">Další příklady práce s parametry, naleznete v tématu [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) a [parametry adaptéru dat](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="69885-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="69885-206">Příklad datum</span><span class="sxs-lookup"><span data-stu-id="69885-206">Date Example</span></span>  
 <span data-ttu-id="69885-207">Následující fragment kódu ukazuje, jak určit `date` parametru.</span><span class="sxs-lookup"><span data-stu-id="69885-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="69885-208">Příklad čas</span><span class="sxs-lookup"><span data-stu-id="69885-208">Time Example</span></span>  
 <span data-ttu-id="69885-209">Následující fragment kódu ukazuje, jak určit `time` parametru.</span><span class="sxs-lookup"><span data-stu-id="69885-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="69885-210">Příklad Datetime2</span><span class="sxs-lookup"><span data-stu-id="69885-210">Datetime2 Example</span></span>  
 <span data-ttu-id="69885-211">Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částmi datum a čas.</span><span class="sxs-lookup"><span data-stu-id="69885-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="69885-212">Příklad DateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="69885-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="69885-213">Následující fragment kódu ukazuje, jak určit `DateTimeOffSet` datum, čas a posun časového pásma z 0.</span><span class="sxs-lookup"><span data-stu-id="69885-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="69885-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="69885-214">AddWithValue</span></span>  
 <span data-ttu-id="69885-215">Parametry lze také zadat pomocí `AddWithValue` metodu <xref:System.Data.SqlClient.SqlCommand>, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="69885-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="69885-216">Ale `AddWithValue` metoda neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> parametru.</span><span class="sxs-lookup"><span data-stu-id="69885-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="69885-217">`@date` Parametr namapovat na `date`, `datetime`, nebo `datetime2` datový typ na serveru.</span><span class="sxs-lookup"><span data-stu-id="69885-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="69885-218">Při práci s novými `datetime` datové typy, musíte explicitně nastavit parametr <xref:System.Data.SqlDbType> vlastnost na datový typ instance.</span><span class="sxs-lookup"><span data-stu-id="69885-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="69885-219">Pomocí <xref:System.Data.SqlDbType.Variant> nebo implicitně zadáním hodnot parametrů může způsobit problémy se zpětnou kompatibilitu s `datetime` a `smalldatetime` datové typy.</span><span class="sxs-lookup"><span data-stu-id="69885-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="69885-220">Následující tabulka uvádí, které `SqlDbTypes` jsou odvozeny z jaké typy CLR:</span><span class="sxs-lookup"><span data-stu-id="69885-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="69885-221">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="69885-221">CLR type</span></span>|<span data-ttu-id="69885-222">Odvozené SqlDbType</span><span class="sxs-lookup"><span data-stu-id="69885-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="69885-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-223">DateTime</span></span>|<span data-ttu-id="69885-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="69885-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="69885-225">Časový interval</span><span class="sxs-lookup"><span data-stu-id="69885-225">TimeSpan</span></span>|<span data-ttu-id="69885-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="69885-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="69885-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-227">DateTimeOffset</span></span>|<span data-ttu-id="69885-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="69885-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="69885-229">Načítají se kalendářní a časová Data</span><span class="sxs-lookup"><span data-stu-id="69885-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="69885-230">Následující tabulka popisuje metody, které slouží k načtení hodnoty data a času v systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="69885-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="69885-231">SqlClient – metoda</span><span class="sxs-lookup"><span data-stu-id="69885-231">SqlClient method</span></span>|<span data-ttu-id="69885-232">Popis</span><span class="sxs-lookup"><span data-stu-id="69885-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="69885-233">Načte hodnotu zadaného sloupce jako <xref:System.DateTime> struktury.</span><span class="sxs-lookup"><span data-stu-id="69885-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="69885-234">Načte hodnotu zadaného sloupce jako <xref:System.DateTimeOffset> struktury.</span><span class="sxs-lookup"><span data-stu-id="69885-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="69885-235">Vrátí typ, který je základní typ pro pole specifické pro zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="69885-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="69885-236">Vrátí stejné typy jako `GetFieldType` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="69885-237">Načte hodnotu pro určený sloupec.</span><span class="sxs-lookup"><span data-stu-id="69885-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="69885-238">Vrátí stejné typy jako `GetValue` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="69885-239">Načte hodnoty v určeném poli.</span><span class="sxs-lookup"><span data-stu-id="69885-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="69885-240">Načte se hodnota sloupce jako <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="69885-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="69885-241"><xref:System.InvalidCastException> Nastane, pokud data nelze vyjádřen jako `SqlString`.</span><span class="sxs-lookup"><span data-stu-id="69885-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="69885-242">Načte data sloupce jako svou výchozí hodnotu `SqlDbType`.</span><span class="sxs-lookup"><span data-stu-id="69885-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="69885-243">Vrátí stejné typy jako `GetValue` pro nové typy data a času.</span><span class="sxs-lookup"><span data-stu-id="69885-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="69885-244">Načte hodnoty v určeném poli.</span><span class="sxs-lookup"><span data-stu-id="69885-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="69885-245">Pokud Type System Version nastavena na SQL Server 2005, načte se hodnota sloupce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="69885-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="69885-246"><xref:System.InvalidCastException> Nastane, pokud data nelze vyjádřen jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="69885-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="69885-247">Načte hodnotu zadaného sloupce jako <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="69885-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="69885-248">Načte hodnotu zadaného sloupce jako jeho základní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="69885-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="69885-249">Načte hodnoty sloupců v poli.</span><span class="sxs-lookup"><span data-stu-id="69885-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="69885-250">Vrátí <xref:System.Data.DataTable> , který popisuje metadata sady výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="69885-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="69885-251">Nové datum a čas `SqlDbTypes` nejsou podporovány pro kód, který je spouštěn v procesu v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="69885-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="69885-252">Bude vyvolána výjimka, pokud jeden z těchto typů je předán serveru.</span><span class="sxs-lookup"><span data-stu-id="69885-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="69885-253">Určení hodnoty data a času jako literály</span><span class="sxs-lookup"><span data-stu-id="69885-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="69885-254">Můžete určit datum a čas datové typy s použitím různých formátech různých řetězcového literálu, který SQL Server pak vyhodnotí za běhu, převod na datum/čas vnitřního struktury.</span><span class="sxs-lookup"><span data-stu-id="69885-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="69885-255">SQL Server rozpozná data pro datum a čas, který je uzavřen v jednoduchých uvozovkách (').</span><span class="sxs-lookup"><span data-stu-id="69885-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="69885-256">Následující příklady ukazují některé formáty:</span><span class="sxs-lookup"><span data-stu-id="69885-256">The following examples demonstrate some formats:</span></span>  
  
-   <span data-ttu-id="69885-257">Abecední datum formáty, jako například `'October 15, 2006'`.</span><span class="sxs-lookup"><span data-stu-id="69885-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
-   <span data-ttu-id="69885-258">Číselná data formátů, jako například `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="69885-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
-   <span data-ttu-id="69885-259">Oddělené formáty řetězců, jako například `'20061015'`, které by být interpretován jako 15. října 2006, pokud používáte formát data ISO.</span><span class="sxs-lookup"><span data-stu-id="69885-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69885-260">Úplnou dokumentaci najdete pro všechny formáty řetězcového literálu a dalších funkcí datové typy data a času v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="69885-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="69885-261">Vyvolá výjimku časové hodnoty, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="69885-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="69885-262">Prostředky v SQL Server 2008 Books Online</span><span class="sxs-lookup"><span data-stu-id="69885-262">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="69885-263">Další informace o práci s hodnotami data a času v systému SQL Server 2008 najdete v následujících zdrojích v SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="69885-263">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="69885-264">Téma</span><span class="sxs-lookup"><span data-stu-id="69885-264">Topic</span></span>|<span data-ttu-id="69885-265">Popis</span><span class="sxs-lookup"><span data-stu-id="69885-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="69885-266">Datum a čas Data typy a funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="69885-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="69885-267">Poskytuje přehled příkazů jazyka Transact-SQL data a času datové typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="69885-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="69885-268">Pomocí kalendářní a časová Data</span><span class="sxs-lookup"><span data-stu-id="69885-268">Using Date and Time Data</span></span>](https://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="69885-269">Poskytuje informace o datum a čas datové typy a funkce a příklady jejich použití.</span><span class="sxs-lookup"><span data-stu-id="69885-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="69885-270">Data Types (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="69885-270">Data Types (Transact-SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="69885-271">Popisuje datové typy systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="69885-271">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69885-272">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69885-272">See also</span></span>
- [<span data-ttu-id="69885-273">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="69885-273">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="69885-274">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="69885-274">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="69885-275">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69885-275">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="69885-276">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="69885-276">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
