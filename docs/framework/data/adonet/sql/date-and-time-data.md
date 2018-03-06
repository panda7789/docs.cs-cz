---
title: "Datum a čas dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 904b941a274cdd31485d35cf2d025f869638d448
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2018
---
# <a name="date-and-time-data"></a><span data-ttu-id="ac55d-102">Datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="ac55d-102">Date and Time Data</span></span>
<span data-ttu-id="ac55d-103">SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času.</span><span class="sxs-lookup"><span data-stu-id="ac55d-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="ac55d-104">Nové typy dat zahrnují rozšířené datové typy s větší rozsah, přesnost a časové pásmo a samostatné typy pro datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="ac55d-105">Počínaje verzí rozhraní .NET Framework 3.5 Service Pack (SP) 1, zprostředkovatel dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje úplnou podporu pro všechny nové funkce databázového stroje SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ac55d-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="ac55d-106">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro použití s SqlClient tyto nové funkce.</span><span class="sxs-lookup"><span data-stu-id="ac55d-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="ac55d-107">Verze systému SQL Server starších než SQL Server 2008 pouze měl dvě datové typy pro práci s hodnotami data a času: `datetime` a `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="ac55d-108">Oba tyto typy dat obsahovat hodnoty data a hodnotu čas, takže je obtížné pracovat pouze data nebo pouze hodnoty času.</span><span class="sxs-lookup"><span data-stu-id="ac55d-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="ac55d-109">Tyto datové typy navíc podporují jenom data, ke kterým došlo po zavedení gregoriánský kalendář v Anglii v 1753.</span><span class="sxs-lookup"><span data-stu-id="ac55d-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="ac55d-110">Další omezení je, že tyto starší datové typy nejsou časových pásem vědět, který ztěžuje pro práci s daty, která pochází z více časových pásem.</span><span class="sxs-lookup"><span data-stu-id="ac55d-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="ac55d-111">Kompletní dokumentaci pro datové typy systému SQL Server je k dispozici v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="ac55d-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="ac55d-112">Následující tabulka uvádí základní témata specifické pro verzi pro data a času.</span><span class="sxs-lookup"><span data-stu-id="ac55d-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="ac55d-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="ac55d-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="ac55d-114">Použitím datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="ac55d-114">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="ac55d-115">Datum a čas datové typy zavedená v systému SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="ac55d-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="ac55d-116">Následující tabulka popisuje nové datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="ac55d-117">Typ dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="ac55d-117">SQL Server data type</span></span>|<span data-ttu-id="ac55d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ac55d-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="ac55d-119">`date` Datový typ má rozsah 1. ledna 01 do 31. prosince 9999 s přesností na 1 den.</span><span class="sxs-lookup"><span data-stu-id="ac55d-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="ac55d-120">Výchozí hodnota je 1. ledna 1900.</span><span class="sxs-lookup"><span data-stu-id="ac55d-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="ac55d-121">Velikost úložiště je 3 bajtů.</span><span class="sxs-lookup"><span data-stu-id="ac55d-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="ac55d-122">`time` Datový typ ukládá pouze hodnoty času ve 24hodinovém formátu.</span><span class="sxs-lookup"><span data-stu-id="ac55d-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="ac55d-123">`time` Datový typ má rozsah 00:00:00.0000000 prostřednictvím 23:59:59.9999999 s přesností na 100 nanosekundách.</span><span class="sxs-lookup"><span data-stu-id="ac55d-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="ac55d-124">Výchozí hodnota je 00:00:00.0000000 (půlnoc).</span><span class="sxs-lookup"><span data-stu-id="ac55d-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="ac55d-125">`time` Uživatelem definované zlomková přesnost pro sekundy podporuje datový typ a velikost úložiště se liší od 3 do 6 bajtů, podle Zadaná přesnost.</span><span class="sxs-lookup"><span data-stu-id="ac55d-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="ac55d-126">`datetime2` Datový typ kombinuje rozsah a přesnost `date` a `time` typy dat do jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="ac55d-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="ac55d-127">Výchozí hodnoty a formáty literálu řetězce jsou stejné jako názvům definovaným v `date` a `time` datové typy.</span><span class="sxs-lookup"><span data-stu-id="ac55d-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="ac55d-128">`datetimeoffset` Datový typ má všechny funkce `datetime2` s posunem další časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="ac55d-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="ac55d-129">Posun v časových pásmech je reprezentován jako [+ &#124;-] hh: mm.</span><span class="sxs-lookup"><span data-stu-id="ac55d-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="ac55d-130">HH jsou 2 číslic od 00 do 14, které představují počtem hodin za posun časového pásma.</span><span class="sxs-lookup"><span data-stu-id="ac55d-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="ac55d-131">MM je 2 číslic od 00 do 59 představující počet minut, další v posun časového pásma.</span><span class="sxs-lookup"><span data-stu-id="ac55d-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="ac55d-132">Podporované jsou formáty času na 100 nanosekundách.</span><span class="sxs-lookup"><span data-stu-id="ac55d-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="ac55d-133">Povinné + nebo - přihlašovací Určuje, zda je posun v časových pásmech přidány nebo odečten od času UTC (Universal Time koordinovat nebo greenwichský střední čas) k získání místního času.</span><span class="sxs-lookup"><span data-stu-id="ac55d-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ac55d-134">Další informace o používání `Type System Version` – klíčové slovo, najdete v části <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac55d-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="ac55d-135">Formát data a pořadí v datu</span><span class="sxs-lookup"><span data-stu-id="ac55d-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="ac55d-136">Jak analyzuje hodnoty data a času v systému SQL Server závisí nejen na verzi systému typ a verze serveru, ale také na jazyk a formát výchozí nastavení serveru.</span><span class="sxs-lookup"><span data-stu-id="ac55d-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="ac55d-137">Řetězec datum, může nerozpoznatelný, pokud dotaz proveden prostřednictvím funguje pro formátování data z jednoho jazyka, který používá jiný jazyk a formát data nastavení.</span><span class="sxs-lookup"><span data-stu-id="ac55d-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="ac55d-138">Příkaz jazyka Transact-SQL nastavit implicitně nastaví parametr DATEFORMAT, která určuje pořadí částí data.</span><span class="sxs-lookup"><span data-stu-id="ac55d-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="ac55d-139">Příkaz nastavit parametr DATEFORMAT Transact-SQL můžete použít na připojení k rozlišení hodnot data podle částí data v formát MDR, DMY, RMD, RDM, MYD nebo DYM pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="ac55d-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="ac55d-140">Pokud nezadáte žádné parametr DATEFORMAT pro připojení, SQL Server používá výchozí jazyk přidružené k připojení.</span><span class="sxs-lookup"><span data-stu-id="ac55d-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="ac55d-141">Například datum řetězec "01/02/03" by byl interpretován jako formát MDR (2. ledna 2003) na serveru s nastavením jazyka angličtinu Spojených států a jako DMY (1 února 2003) na serveru s nastavením jazyka britské angličtině.</span><span class="sxs-lookup"><span data-stu-id="ac55d-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="ac55d-142">Pomocí pravidla konečného roku systému SQL Server, který definuje datum přerušení pro přiřazení hodnoty století je určen v roce.</span><span class="sxs-lookup"><span data-stu-id="ac55d-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="ac55d-143">Další informace najdete v tématu [dvě číslice roku konečného možnost](http://go.microsoft.com/fwlink/?LinkId=120473) v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="ac55d-143">For more information, see [two digit year cutoff Option](http://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac55d-144">Formát data RDM nepodporuje při převodu z formátu řetězce na `date`, `time`, `datetime2`, nebo `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="ac55d-145">Další informace o interpretace data a času v systému SQL Server najdete v tématu [pomocí datum a čas Data](http://go.microsoft.com/fwlink/?LinkID=98361) v SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="ac55d-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](http://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="ac55d-146">Datum a čas datové typy a parametry</span><span class="sxs-lookup"><span data-stu-id="ac55d-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="ac55d-147">Přidané následující výčty <xref:System.Data.SqlDbType> pro podporu nových typů dat Datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="ac55d-148">Můžete zadat datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jedné z předchozí <xref:System.Data.SqlDbType> výčty.</span><span class="sxs-lookup"><span data-stu-id="ac55d-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span> 

> [!NOTE]
> <span data-ttu-id="ac55d-149">Nelze nastavit `DbType` vlastnost `SqlParameter` k `SqlDbType.Date`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="ac55d-150">Můžete také zadat typ <xref:System.Data.SqlClient.SqlParameter> obecně nastavením <xref:System.Data.SqlClient.SqlParameter.DbType%2A> vlastnost `SqlParameter` objekt, který má určitý <xref:System.Data.DbType> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="ac55d-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="ac55d-151">Následující hodnoty výčtu jsou přidané do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datové typy:</span><span class="sxs-lookup"><span data-stu-id="ac55d-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
-   <span data-ttu-id="ac55d-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="ac55d-152">DbType.DateTime2</span></span>  
  
-   <span data-ttu-id="ac55d-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="ac55d-154">Tyto nové výčty doplnit `Date`, `Time`, a `DateTime` výčty, které existovaly v dřívějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac55d-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ac55d-155">Typ zprostředkovatele dat .NET Framework objektu parametr je odvozeno z rozhraní .NET Framework typ hodnoty parametru objektu, nebo z `DbType` parametr objektu.</span><span class="sxs-lookup"><span data-stu-id="ac55d-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="ac55d-156">Nové <xref:System.Data.SqlTypes> byly zavedeny datové typy pro podporu nových typů dat Datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="ac55d-157">Následující tabulka popisuje mapování mezi datem systému SQL Server 2008 a časové datové typy a datové typy CLR.</span><span class="sxs-lookup"><span data-stu-id="ac55d-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="ac55d-158">Typ dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="ac55d-158">SQL Server data type</span></span>|<span data-ttu-id="ac55d-159">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ac55d-159">.NET Framework type</span></span>|<span data-ttu-id="ac55d-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="ac55d-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="ac55d-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="ac55d-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="ac55d-162">Datum</span><span class="sxs-lookup"><span data-stu-id="ac55d-162">date</span></span>|<span data-ttu-id="ac55d-163">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-163">System.DateTime</span></span>|<span data-ttu-id="ac55d-164">Datum</span><span class="sxs-lookup"><span data-stu-id="ac55d-164">Date</span></span>|<span data-ttu-id="ac55d-165">Datum</span><span class="sxs-lookup"><span data-stu-id="ac55d-165">Date</span></span>|  
|<span data-ttu-id="ac55d-166">čas</span><span class="sxs-lookup"><span data-stu-id="ac55d-166">time</span></span>|<span data-ttu-id="ac55d-167">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="ac55d-167">System.TimeSpan</span></span>|<span data-ttu-id="ac55d-168">Čas</span><span class="sxs-lookup"><span data-stu-id="ac55d-168">Time</span></span>|<span data-ttu-id="ac55d-169">Čas</span><span class="sxs-lookup"><span data-stu-id="ac55d-169">Time</span></span>|  
|<span data-ttu-id="ac55d-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="ac55d-170">datetime2</span></span>|<span data-ttu-id="ac55d-171">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-171">System.DateTime</span></span>|<span data-ttu-id="ac55d-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="ac55d-172">DateTime2</span></span>|<span data-ttu-id="ac55d-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="ac55d-173">DateTime2</span></span>|  
|<span data-ttu-id="ac55d-174">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-174">datetimeoffset</span></span>|<span data-ttu-id="ac55d-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-175">System.DateTimeOffset</span></span>|<span data-ttu-id="ac55d-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-176">DateTimeOffset</span></span>|<span data-ttu-id="ac55d-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="ac55d-178">Data a času</span><span class="sxs-lookup"><span data-stu-id="ac55d-178">datetime</span></span>|<span data-ttu-id="ac55d-179">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-179">System.DateTime</span></span>|<span data-ttu-id="ac55d-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-180">DateTime</span></span>|<span data-ttu-id="ac55d-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-181">DateTime</span></span>|  
|<span data-ttu-id="ac55d-182">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="ac55d-182">smalldatetime</span></span>|<span data-ttu-id="ac55d-183">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-183">System.DateTime</span></span>|<span data-ttu-id="ac55d-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-184">DateTime</span></span>|<span data-ttu-id="ac55d-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="ac55d-186">Vlastnosti SqlParameter</span><span class="sxs-lookup"><span data-stu-id="ac55d-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="ac55d-187">Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="ac55d-188">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ac55d-188">Property</span></span>|<span data-ttu-id="ac55d-189">Popis</span><span class="sxs-lookup"><span data-stu-id="ac55d-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="ac55d-190">Získá nebo nastaví, zda je hodnota Null.</span><span class="sxs-lookup"><span data-stu-id="ac55d-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="ac55d-191">Hodnota null parametru odešlete na server, je nutné zadat <xref:System.DBNull>, místo `null` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ac55d-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="ac55d-192">Další informace o hodnoty Null databáze najdete v tématu [zpracování hodnot Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="ac55d-192">For more information about database nulls, see [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="ac55d-193">Získá nebo nastaví maximální počet číslic, na které se používá k reprezentování hodnota.</span><span class="sxs-lookup"><span data-stu-id="ac55d-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="ac55d-194">Toto nastavení je ignorováno pro datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="ac55d-195">Získá nebo nastaví počet desetinných míst, na které se pro čas část hodnoty `Time`, `DateTime2`, a `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="ac55d-196">Výchozí hodnota je 0, což znamená, že je skutečný měřítka odvodit z hodnoty a odesílá na server.</span><span class="sxs-lookup"><span data-stu-id="ac55d-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="ac55d-197">Ignorovat pro datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="ac55d-198">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="ac55d-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="ac55d-199">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="ac55d-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ac55d-200">Vyvolá výjimku hodnoty času, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ac55d-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="ac55d-201">Vytváření parametrů</span><span class="sxs-lookup"><span data-stu-id="ac55d-201">Creating Parameters</span></span>  
 <span data-ttu-id="ac55d-202">Můžete vytvořit <xref:System.Data.SqlClient.SqlParameter> objekt pomocí jeho konstruktoru, nebo jejím přidáním na <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním `Add` metodu <xref:System.Data.SqlClient.SqlParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="ac55d-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="ac55d-203">`Add` Metoda bude trvat jako vstupní argumenty konstruktoru nebo existujícího objektu parametr.</span><span class="sxs-lookup"><span data-stu-id="ac55d-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="ac55d-204">Další části v tomto tématu obsahují příklady, jak určit datum a čas parametry.</span><span class="sxs-lookup"><span data-stu-id="ac55d-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="ac55d-205">Další příklady práce s parametry, najdete v části [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) a [DataAdapter parametry](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ac55d-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="ac55d-206">Příklad datum</span><span class="sxs-lookup"><span data-stu-id="ac55d-206">Date Example</span></span>  
 <span data-ttu-id="ac55d-207">Následující fragment kódu ukazuje, jak určit `date` parametr.</span><span class="sxs-lookup"><span data-stu-id="ac55d-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="ac55d-208">Příklad čas</span><span class="sxs-lookup"><span data-stu-id="ac55d-208">Time Example</span></span>  
 <span data-ttu-id="ac55d-209">Následující fragment kódu ukazuje, jak určit `time` parametr.</span><span class="sxs-lookup"><span data-stu-id="ac55d-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="ac55d-210">Příklad Datetime2</span><span class="sxs-lookup"><span data-stu-id="ac55d-210">Datetime2 Example</span></span>  
 <span data-ttu-id="ac55d-211">Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částí datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="ac55d-212">Příklad DateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="ac55d-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="ac55d-213">Následující fragment kódu ukazuje, jak určit `DateTimeOffSet` parametr s datum, čas a posun časového pásma 0.</span><span class="sxs-lookup"><span data-stu-id="ac55d-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="ac55d-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="ac55d-214">AddWithValue</span></span>  
 <span data-ttu-id="ac55d-215">Můžete také zadat parametry pomocí `AddWithValue` metodu <xref:System.Data.SqlClient.SqlCommand>, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="ac55d-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="ac55d-216">Ale `AddWithValue` metoda neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.</span><span class="sxs-lookup"><span data-stu-id="ac55d-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="ac55d-217">`@date` Může parametr mapovat `date`, `datetime`, nebo `datetime2` datový typ na serveru.</span><span class="sxs-lookup"><span data-stu-id="ac55d-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="ac55d-218">Při práci s novým `datetime` datové typy, musíte explicitně nastavit parametr <xref:System.Data.SqlDbType> vlastnost, která má datový typ instance.</span><span class="sxs-lookup"><span data-stu-id="ac55d-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="ac55d-219">Pomocí <xref:System.Data.SqlDbType.Variant> nebo implicitně zadávání hodnot parametru může způsobit problémy s zpětnou kompatibilitu s `datetime` a `smalldatetime` datové typy.</span><span class="sxs-lookup"><span data-stu-id="ac55d-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="ac55d-220">Následující tabulka uvádí, které `SqlDbTypes` jsou odvozené z které typy CLR:</span><span class="sxs-lookup"><span data-stu-id="ac55d-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="ac55d-221">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="ac55d-221">CLR type</span></span>|<span data-ttu-id="ac55d-222">Inferred SqlDbType</span><span class="sxs-lookup"><span data-stu-id="ac55d-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="ac55d-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-223">DateTime</span></span>|<span data-ttu-id="ac55d-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="ac55d-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="ac55d-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="ac55d-225">TimeSpan</span></span>|<span data-ttu-id="ac55d-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="ac55d-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="ac55d-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-227">DateTimeOffset</span></span>|<span data-ttu-id="ac55d-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="ac55d-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="ac55d-229">Načítání datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="ac55d-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="ac55d-230">Následující tabulka popisuje metody, které slouží k načtení hodnoty data a času v systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ac55d-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="ac55d-231">SqlClient – metoda</span><span class="sxs-lookup"><span data-stu-id="ac55d-231">SqlClient method</span></span>|<span data-ttu-id="ac55d-232">Popis</span><span class="sxs-lookup"><span data-stu-id="ac55d-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="ac55d-233">Načte hodnotu zadaného sloupce jako <xref:System.DateTime> struktury.</span><span class="sxs-lookup"><span data-stu-id="ac55d-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="ac55d-234">Načte hodnotu zadaného sloupce jako <xref:System.DateTimeOffset> struktury.</span><span class="sxs-lookup"><span data-stu-id="ac55d-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="ac55d-235">Vrátí typ, který je základní typ specifický pro zprostředkovatele pro pole.</span><span class="sxs-lookup"><span data-stu-id="ac55d-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="ac55d-236">Vrátí stejné typy jako `GetFieldType` pro nové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="ac55d-237">Načte hodnotu pro určený sloupec.</span><span class="sxs-lookup"><span data-stu-id="ac55d-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="ac55d-238">Vrátí stejné typy jako `GetValue` pro nové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="ac55d-239">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="ac55d-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="ac55d-240">Načte hodnotu sloupce jako <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="ac55d-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="ac55d-241"><xref:System.InvalidCastException> Dat nemůže být vyjádřena jako v případě `SqlString`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="ac55d-242">Načte data pro sloupec jako jeho výchozí `SqlDbType`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="ac55d-243">Vrátí stejné typy jako `GetValue` pro nové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="ac55d-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="ac55d-244">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="ac55d-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="ac55d-245">Načte hodnotu sloupce jako řetězec, pokud na verzi systému typ nastavena na systém SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="ac55d-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="ac55d-246"><xref:System.InvalidCastException> v případě dat nemůže být vyjádřena jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac55d-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="ac55d-247">Načte hodnotu zadaného sloupce jako <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="ac55d-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="ac55d-248">Načte hodnotu zadaného sloupce jako jeho základní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="ac55d-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="ac55d-249">Načte hodnoty ve sloupcích v matici.</span><span class="sxs-lookup"><span data-stu-id="ac55d-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="ac55d-250">Vrátí <xref:System.Data.DataTable> metadata sady výsledků dotazu, který popisuje.</span><span class="sxs-lookup"><span data-stu-id="ac55d-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ac55d-251">Nové datum a čas `SqlDbTypes` nejsou podporovány pro kód, který spouští v procesu v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac55d-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="ac55d-252">Pokud jeden z těchto typů je předán na server, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ac55d-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="ac55d-253">Zadání hodnoty data a času jako literály.</span><span class="sxs-lookup"><span data-stu-id="ac55d-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="ac55d-254">Můžete určit datum a čas typy dat pomocí různých formátech různých řetězcového literálu, kdy SQL Server pak vyhodnotí za běhu, jejich převedení na struktury interní data a času.</span><span class="sxs-lookup"><span data-stu-id="ac55d-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="ac55d-255">SQL Server rozpoznal datum a čas data, která je uzavřen v jednoduchých uvozovkách (').</span><span class="sxs-lookup"><span data-stu-id="ac55d-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="ac55d-256">Následující příklady ukazují, některé formáty:</span><span class="sxs-lookup"><span data-stu-id="ac55d-256">The following examples demonstrate some formats:</span></span>  
  
-   <span data-ttu-id="ac55d-257">Abecední datum formátů, jako například `'October 15, 2006'`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
-   <span data-ttu-id="ac55d-258">Číselná data formátů, jako například `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="ac55d-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
-   <span data-ttu-id="ac55d-259">Oddělené formáty řetězců, jako například `'20061015'`, který by byl interpretován jako 15. října 2006, pokud používáte formát data standardu ISO.</span><span class="sxs-lookup"><span data-stu-id="ac55d-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac55d-260">Kompletní dokumentaci můžete najít pro všechny formáty řetězcového literálu a další funkce data a času datových typů v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="ac55d-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="ac55d-261">Vyvolá výjimku hodnoty času, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ac55d-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="ac55d-262">Prostředky v Online knihách SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="ac55d-262">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="ac55d-263">Další informace o práci se hodnoty data a času v systému SQL Server 2008 najdete v následujících zdrojích v SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="ac55d-263">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="ac55d-264">Téma</span><span class="sxs-lookup"><span data-stu-id="ac55d-264">Topic</span></span>|<span data-ttu-id="ac55d-265">Popis</span><span class="sxs-lookup"><span data-stu-id="ac55d-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ac55d-266">Datum a čas datové typy a funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ac55d-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="ac55d-267">Poskytuje přehled o Transact-SQL data a času datové typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="ac55d-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="ac55d-268">Použitím datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="ac55d-268">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="ac55d-269">Poskytuje informace o datu a času datové typy a funkce a příklady jejich používání.</span><span class="sxs-lookup"><span data-stu-id="ac55d-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="ac55d-270">Datové typy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ac55d-270">Data Types (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="ac55d-271">Popisuje typy dat systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ac55d-271">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac55d-272">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac55d-272">See Also</span></span>  
 [<span data-ttu-id="ac55d-273">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="ac55d-273">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="ac55d-274">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="ac55d-274">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="ac55d-275">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ac55d-275">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="ac55d-276">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ac55d-276">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
