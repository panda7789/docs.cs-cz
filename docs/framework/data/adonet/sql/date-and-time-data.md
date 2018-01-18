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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a146cf50639351479d42bff684ea7db21ecf5d3b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="date-and-time-data"></a><span data-ttu-id="2a9d9-102">Datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="2a9d9-102">Date and Time Data</span></span>
<span data-ttu-id="2a9d9-103">SQL Server 2008 zavádí nové datové typy pro zpracování informací o datu a času.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="2a9d9-104">Nové typy dat zahrnují rozšířené datové typy s větší rozsah, přesnost a časové pásmo a samostatné typy pro datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="2a9d9-105">Počínaje verzí rozhraní .NET Framework 3.5 Service Pack (SP) 1, zprostředkovatel dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje úplnou podporu pro všechny nové funkce databázového stroje SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="2a9d9-106">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) pro použití s SqlClient tyto nové funkce.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="2a9d9-107">Verze systému SQL Server starších než SQL Server 2008 pouze měl dvě datové typy pro práci s hodnotami data a času: `datetime` a `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="2a9d9-108">Oba tyto typy dat obsahovat hodnoty data a hodnotu čas, takže je obtížné pracovat pouze data nebo pouze hodnoty času.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="2a9d9-109">Tyto datové typy navíc podporují jenom data, ke kterým došlo po zavedení gregoriánský kalendář v Anglii v 1753.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="2a9d9-110">Další omezení je, že tyto starší datové typy nejsou časových pásem vědět, který ztěžuje pro práci s daty, která pochází z více časových pásem.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="2a9d9-111">Kompletní dokumentaci pro datové typy systému SQL Server je k dispozici v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="2a9d9-112">Následující tabulka uvádí základní témata specifické pro verzi pro data a času.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="2a9d9-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="2a9d9-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="2a9d9-114">Použitím datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="2a9d9-114">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="2a9d9-115">Datum a čas datové typy zavedená v systému SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="2a9d9-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="2a9d9-116">Následující tabulka popisuje nové datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="2a9d9-117">Typ dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="2a9d9-117">SQL Server data type</span></span>|<span data-ttu-id="2a9d9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2a9d9-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="2a9d9-119">`date` Datový typ má rozsah 1. ledna 01 do 31. prosince 9999 s přesností na 1 den.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="2a9d9-120">Výchozí hodnota je 1. ledna 1900.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="2a9d9-121">Velikost úložiště je 3 bajtů.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="2a9d9-122">`time` Datový typ ukládá pouze hodnoty času ve 24hodinovém formátu.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="2a9d9-123">`time` Datový typ má rozsah 00:00:00.0000000 prostřednictvím 23:59:59.9999999 s přesností na 100 nanosekundách.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="2a9d9-124">Výchozí hodnota je 00:00:00.0000000 (půlnoc).</span><span class="sxs-lookup"><span data-stu-id="2a9d9-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="2a9d9-125">`time` Uživatelem definované zlomková přesnost pro sekundy podporuje datový typ a velikost úložiště se liší od 3 do 6 bajtů, podle Zadaná přesnost.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="2a9d9-126">`datetime2` Datový typ kombinuje rozsah a přesnost `date` a `time` typy dat do jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="2a9d9-127">Výchozí hodnoty a formáty literálu řetězce jsou stejné jako názvům definovaným v `date` a `time` datové typy.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="2a9d9-128">`datetimeoffset` Datový typ má všechny funkce `datetime2` s posunem další časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="2a9d9-129">Posun v časových pásmech je reprezentován jako [+ &#124;-] hh: mm.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="2a9d9-130">HH jsou 2 číslic od 00 do 14, které představují počtem hodin za posun časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="2a9d9-131">MM je 2 číslic od 00 do 59 představující počet minut, další v posun časového pásma.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="2a9d9-132">Podporované jsou formáty času na 100 nanosekundách.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="2a9d9-133">Povinné + nebo - přihlašovací Určuje, zda je posun v časových pásmech přidány nebo odečten od času UTC (Universal Time koordinovat nebo greenwichský střední čas) k získání místního času.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2a9d9-134">Další informace o používání `Type System Version` – klíčové slovo, najdete v části <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="2a9d9-135">Formát data a pořadí v datu</span><span class="sxs-lookup"><span data-stu-id="2a9d9-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="2a9d9-136">Jak analyzuje hodnoty data a času v systému SQL Server závisí nejen na verzi systému typ a verze serveru, ale také na jazyk a formát výchozí nastavení serveru.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="2a9d9-137">Řetězec datum, může nerozpoznatelný, pokud dotaz proveden prostřednictvím funguje pro formátování data z jednoho jazyka, který používá jiný jazyk a formát data nastavení.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="2a9d9-138">Příkaz jazyka Transact-SQL nastavit implicitně nastaví parametr DATEFORMAT, která určuje pořadí částí data.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="2a9d9-139">Příkaz nastavit parametr DATEFORMAT Transact-SQL můžete použít na připojení k rozlišení hodnot data podle částí data v formát MDR, DMY, RMD, RDM, MYD nebo DYM pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="2a9d9-140">Pokud nezadáte žádné parametr DATEFORMAT pro připojení, SQL Server používá výchozí jazyk přidružené k připojení.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="2a9d9-141">Například datum řetězec "01/02/03" by byl interpretován jako formát MDR (2. ledna 2003) na serveru s nastavením jazyka angličtinu Spojených států a jako DMY (1 února 2003) na serveru s nastavením jazyka britské angličtině.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="2a9d9-142">Pomocí pravidla konečného roku systému SQL Server, který definuje datum přerušení pro přiřazení hodnoty století je určen v roce.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="2a9d9-143">Další informace najdete v tématu [dvě číslice roku konečného možnost](http://go.microsoft.com/fwlink/?LinkId=120473) v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-143">For more information, see [two digit year cutoff Option](http://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a9d9-144">Formát data RDM nepodporuje při převodu z formátu řetězce na `date`, `time`, `datetime2`, nebo `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="2a9d9-145">Další informace o interpretace data a času v systému SQL Server najdete v tématu [pomocí datum a čas Data](http://go.microsoft.com/fwlink/?LinkID=98361) v SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](http://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="2a9d9-146">Datum a čas datové typy a parametry</span><span class="sxs-lookup"><span data-stu-id="2a9d9-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="2a9d9-147">Můžete zadat datový typ <xref:System.Data.SqlClient.SqlParameter> pomocí jedné z <xref:System.Data.SqlDbType> výčty.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-147">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the <xref:System.Data.SqlDbType> enumerations.</span></span> <span data-ttu-id="2a9d9-148">Přidané následující výčty <xref:System.Data.SqlDbType> pro podporu nových typů dat Datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-148">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  
  
 <span data-ttu-id="2a9d9-149">Můžete také zadat typ <xref:System.Data.SqlClient.SqlParameter> obecně nastavením <xref:System.Data.SqlClient.SqlParameter.DbType%2A> vlastnost `SqlParameter` objekt, který má určitý <xref:System.Data.DbType> hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-149">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="2a9d9-150">Následující hodnoty výčtu jsou přidané do <xref:System.Data.DbType> pro podporu `datetime2` a `datetimeoffset` datové typy:</span><span class="sxs-lookup"><span data-stu-id="2a9d9-150">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
-   <span data-ttu-id="2a9d9-151">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="2a9d9-151">DbType.DateTime2</span></span>  
  
-   <span data-ttu-id="2a9d9-152">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-152">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="2a9d9-153">Tyto nové výčty doplnit `Date`, `Time`, a `DateTime` výčty, které existovaly v dřívějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-153">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2a9d9-154">Typ zprostředkovatele dat .NET Framework objektu parametr je odvozeno z rozhraní .NET Framework typ hodnoty parametru objektu, nebo z `DbType` parametr objektu.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-154">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="2a9d9-155">Nové <xref:System.Data.SqlTypes> byly zavedeny datové typy pro podporu nových typů dat Datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-155">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="2a9d9-156">Následující tabulka popisuje mapování mezi datem systému SQL Server 2008 a časové datové typy a datové typy CLR.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-156">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="2a9d9-157">Typ dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="2a9d9-157">SQL Server data type</span></span>|<span data-ttu-id="2a9d9-158">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2a9d9-158">.NET Framework type</span></span>|<span data-ttu-id="2a9d9-159">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="2a9d9-159">System.Data.SqlDbType</span></span>|<span data-ttu-id="2a9d9-160">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="2a9d9-160">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="2a9d9-161">Datum</span><span class="sxs-lookup"><span data-stu-id="2a9d9-161">date</span></span>|<span data-ttu-id="2a9d9-162">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-162">System.DateTime</span></span>|<span data-ttu-id="2a9d9-163">Datum</span><span class="sxs-lookup"><span data-stu-id="2a9d9-163">Date</span></span>|<span data-ttu-id="2a9d9-164">Datum</span><span class="sxs-lookup"><span data-stu-id="2a9d9-164">Date</span></span>|  
|<span data-ttu-id="2a9d9-165">čas</span><span class="sxs-lookup"><span data-stu-id="2a9d9-165">time</span></span>|<span data-ttu-id="2a9d9-166">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="2a9d9-166">System.TimeSpan</span></span>|<span data-ttu-id="2a9d9-167">Čas</span><span class="sxs-lookup"><span data-stu-id="2a9d9-167">Time</span></span>|<span data-ttu-id="2a9d9-168">Čas</span><span class="sxs-lookup"><span data-stu-id="2a9d9-168">Time</span></span>|  
|<span data-ttu-id="2a9d9-169">datetime2</span><span class="sxs-lookup"><span data-stu-id="2a9d9-169">datetime2</span></span>|<span data-ttu-id="2a9d9-170">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-170">System.DateTime</span></span>|<span data-ttu-id="2a9d9-171">DateTime2</span><span class="sxs-lookup"><span data-stu-id="2a9d9-171">DateTime2</span></span>|<span data-ttu-id="2a9d9-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="2a9d9-172">DateTime2</span></span>|  
|<span data-ttu-id="2a9d9-173">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-173">datetimeoffset</span></span>|<span data-ttu-id="2a9d9-174">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-174">System.DateTimeOffset</span></span>|<span data-ttu-id="2a9d9-175">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-175">DateTimeOffset</span></span>|<span data-ttu-id="2a9d9-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-176">DateTimeOffset</span></span>|  
|<span data-ttu-id="2a9d9-177">Data a času</span><span class="sxs-lookup"><span data-stu-id="2a9d9-177">datetime</span></span>|<span data-ttu-id="2a9d9-178">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-178">System.DateTime</span></span>|<span data-ttu-id="2a9d9-179">DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-179">DateTime</span></span>|<span data-ttu-id="2a9d9-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-180">DateTime</span></span>|  
|<span data-ttu-id="2a9d9-181">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-181">smalldatetime</span></span>|<span data-ttu-id="2a9d9-182">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-182">System.DateTime</span></span>|<span data-ttu-id="2a9d9-183">DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-183">DateTime</span></span>|<span data-ttu-id="2a9d9-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-184">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="2a9d9-185">Vlastnosti SqlParameter</span><span class="sxs-lookup"><span data-stu-id="2a9d9-185">SqlParameter Properties</span></span>  
 <span data-ttu-id="2a9d9-186">Následující tabulka popisuje `SqlParameter` vlastnosti, které jsou relevantní pro datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-186">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="2a9d9-187">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2a9d9-187">Property</span></span>|<span data-ttu-id="2a9d9-188">Popis</span><span class="sxs-lookup"><span data-stu-id="2a9d9-188">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="2a9d9-189">Získá nebo nastaví, zda je hodnota Null.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-189">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="2a9d9-190">Hodnota null parametru odešlete na server, je nutné zadat <xref:System.DBNull>, místo `null` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2a9d9-190">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="2a9d9-191">Další informace o hodnoty Null databáze najdete v tématu [zpracování hodnot Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="2a9d9-191">For more information about database nulls, see [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="2a9d9-192">Získá nebo nastaví maximální počet číslic, na které se používá k reprezentování hodnota.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-192">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="2a9d9-193">Toto nastavení je ignorováno pro datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-193">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="2a9d9-194">Získá nebo nastaví počet desetinných míst, na které se pro čas část hodnoty `Time`, `DateTime2`, a `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-194">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="2a9d9-195">Výchozí hodnota je 0, což znamená, že je skutečný měřítka odvodit z hodnoty a odesílá na server.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-195">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="2a9d9-196">Ignorovat pro datové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-196">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="2a9d9-197">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-197">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="2a9d9-198">Získá nebo nastaví hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-198">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2a9d9-199">Vyvolá výjimku hodnoty času, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-199">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="2a9d9-200">Vytváření parametrů</span><span class="sxs-lookup"><span data-stu-id="2a9d9-200">Creating Parameters</span></span>  
 <span data-ttu-id="2a9d9-201">Můžete vytvořit <xref:System.Data.SqlClient.SqlParameter> objekt pomocí jeho konstruktoru, nebo jejím přidáním na <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekce voláním `Add` metodu <xref:System.Data.SqlClient.SqlParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-201">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="2a9d9-202">`Add` Metoda bude trvat jako vstupní argumenty konstruktoru nebo existujícího objektu parametr.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-202">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="2a9d9-203">Další části v tomto tématu obsahují příklady, jak určit datum a čas parametry.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-203">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="2a9d9-204">Další příklady práce s parametry, najdete v části [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) a [DataAdapter parametry](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2a9d9-204">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="2a9d9-205">Příklad datum</span><span class="sxs-lookup"><span data-stu-id="2a9d9-205">Date Example</span></span>  
 <span data-ttu-id="2a9d9-206">Následující fragment kódu ukazuje, jak určit `date` parametr.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-206">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="2a9d9-207">Příklad čas</span><span class="sxs-lookup"><span data-stu-id="2a9d9-207">Time Example</span></span>  
 <span data-ttu-id="2a9d9-208">Následující fragment kódu ukazuje, jak určit `time` parametr.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-208">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="2a9d9-209">Příklad Datetime2</span><span class="sxs-lookup"><span data-stu-id="2a9d9-209">Datetime2 Example</span></span>  
 <span data-ttu-id="2a9d9-210">Následující fragment kódu ukazuje, jak určit `datetime2` parametr s částí datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-210">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="2a9d9-211">Příklad DateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="2a9d9-211">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="2a9d9-212">Následující fragment kódu ukazuje, jak určit `DateTimeOffSet` parametr s datum, čas a posun časového pásma 0.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-212">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="2a9d9-213">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="2a9d9-213">AddWithValue</span></span>  
 <span data-ttu-id="2a9d9-214">Můžete také zadat parametry pomocí `AddWithValue` metodu <xref:System.Data.SqlClient.SqlCommand>, jak ukazuje následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-214">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="2a9d9-215">Ale `AddWithValue` metoda neumožňuje zadat <xref:System.Data.SqlClient.SqlParameter.DbType%2A> nebo <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> pro parametr.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-215">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="2a9d9-216">`@date` Může parametr mapovat `date`, `datetime`, nebo `datetime2` datový typ na serveru.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-216">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="2a9d9-217">Při práci s novým `datetime` datové typy, musíte explicitně nastavit parametr <xref:System.Data.SqlDbType> vlastnost, která má datový typ instance.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-217">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="2a9d9-218">Pomocí <xref:System.Data.SqlDbType.Variant> nebo implicitně zadávání hodnot parametru může způsobit problémy s zpětnou kompatibilitu s `datetime` a `smalldatetime` datové typy.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-218">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="2a9d9-219">Následující tabulka uvádí, které `SqlDbTypes` jsou odvozené z které typy CLR:</span><span class="sxs-lookup"><span data-stu-id="2a9d9-219">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="2a9d9-220">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="2a9d9-220">CLR type</span></span>|<span data-ttu-id="2a9d9-221">Inferred SqlDbType</span><span class="sxs-lookup"><span data-stu-id="2a9d9-221">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="2a9d9-222">DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-222">DateTime</span></span>|<span data-ttu-id="2a9d9-223">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="2a9d9-223">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="2a9d9-224">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="2a9d9-224">TimeSpan</span></span>|<span data-ttu-id="2a9d9-225">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="2a9d9-225">SqlDbType.Time</span></span>|  
|<span data-ttu-id="2a9d9-226">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-226">DateTimeOffset</span></span>|<span data-ttu-id="2a9d9-227">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="2a9d9-227">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="2a9d9-228">Načítání datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="2a9d9-228">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="2a9d9-229">Následující tabulka popisuje metody, které slouží k načtení hodnoty data a času v systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-229">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="2a9d9-230">SqlClient – metoda</span><span class="sxs-lookup"><span data-stu-id="2a9d9-230">SqlClient method</span></span>|<span data-ttu-id="2a9d9-231">Popis</span><span class="sxs-lookup"><span data-stu-id="2a9d9-231">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="2a9d9-232">Načte hodnotu zadaného sloupce jako <xref:System.DateTime> struktury.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-232">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="2a9d9-233">Načte hodnotu zadaného sloupce jako <xref:System.DateTimeOffset> struktury.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-233">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="2a9d9-234">Vrátí typ, který je základní typ specifický pro zprostředkovatele pro pole.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-234">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="2a9d9-235">Vrátí stejné typy jako `GetFieldType` pro nové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-235">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="2a9d9-236">Načte hodnotu pro určený sloupec.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-236">Retrieves the value of the specified column.</span></span> <span data-ttu-id="2a9d9-237">Vrátí stejné typy jako `GetValue` pro nové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-237">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="2a9d9-238">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-238">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="2a9d9-239">Načte hodnotu sloupce jako <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-239">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="2a9d9-240"><xref:System.InvalidCastException> Dat nemůže být vyjádřena jako v případě `SqlString`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-240">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="2a9d9-241">Načte data pro sloupec jako jeho výchozí `SqlDbType`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-241">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="2a9d9-242">Vrátí stejné typy jako `GetValue` pro nové typy datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-242">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="2a9d9-243">Načte hodnoty v zadaném poli.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-243">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="2a9d9-244">Načte hodnotu sloupce jako řetězec, pokud na verzi systému typ nastavena na systém SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-244">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="2a9d9-245"><xref:System.InvalidCastException> v případě dat nemůže být vyjádřena jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-245">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="2a9d9-246">Načte hodnotu zadaného sloupce jako <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-246">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="2a9d9-247">Načte hodnotu zadaného sloupce jako jeho základní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-247">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="2a9d9-248">Načte hodnoty ve sloupcích v matici.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-248">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="2a9d9-249">Vrátí <xref:System.Data.DataTable> metadata sady výsledků dotazu, který popisuje.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-249">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2a9d9-250">Nové datum a čas `SqlDbTypes` nejsou podporovány pro kód, který spouští v procesu v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-250">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="2a9d9-251">Pokud jeden z těchto typů je předán na server, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-251">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="2a9d9-252">Zadání hodnoty data a času jako literály.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-252">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="2a9d9-253">Můžete určit datum a čas typy dat pomocí různých formátech různých řetězcového literálu, kdy SQL Server pak vyhodnotí za běhu, jejich převedení na struktury interní data a času.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-253">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="2a9d9-254">SQL Server rozpoznal datum a čas data, která je uzavřen v jednoduchých uvozovkách (').</span><span class="sxs-lookup"><span data-stu-id="2a9d9-254">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="2a9d9-255">Následující příklady ukazují, některé formáty:</span><span class="sxs-lookup"><span data-stu-id="2a9d9-255">The following examples demonstrate some formats:</span></span>  
  
-   <span data-ttu-id="2a9d9-256">Abecední datum formátů, jako například `'October 15, 2006'`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-256">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
-   <span data-ttu-id="2a9d9-257">Číselná data formátů, jako například `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-257">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
-   <span data-ttu-id="2a9d9-258">Oddělené formáty řetězců, jako například `'20061015'`, který by byl interpretován jako 15. října 2006, pokud používáte formát data standardu ISO.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-258">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a9d9-259">Kompletní dokumentaci můžete najít pro všechny formáty řetězcového literálu a další funkce data a času datových typů v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-259">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="2a9d9-260">Vyvolá výjimku hodnoty času, které jsou menší než nula nebo větší než nebo roven 24 hodin <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-260">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="2a9d9-261">Prostředky v Online knihách SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="2a9d9-261">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="2a9d9-262">Další informace o práci se hodnoty data a času v systému SQL Server 2008 najdete v následujících zdrojích v SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-262">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="2a9d9-263">Téma</span><span class="sxs-lookup"><span data-stu-id="2a9d9-263">Topic</span></span>|<span data-ttu-id="2a9d9-264">Popis</span><span class="sxs-lookup"><span data-stu-id="2a9d9-264">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2a9d9-265">Datum a čas datové typy a funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a9d9-265">Date and Time Data Types and Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="2a9d9-266">Poskytuje přehled o Transact-SQL data a času datové typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-266">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="2a9d9-267">Použitím datum a čas dat</span><span class="sxs-lookup"><span data-stu-id="2a9d9-267">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="2a9d9-268">Poskytuje informace o datu a času datové typy a funkce a příklady jejich používání.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-268">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="2a9d9-269">Datové typy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a9d9-269">Data Types (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="2a9d9-270">Popisuje typy dat systému SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2a9d9-270">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a9d9-271">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a9d9-271">See Also</span></span>  
 [<span data-ttu-id="2a9d9-272">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="2a9d9-272">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="2a9d9-273">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="2a9d9-273">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="2a9d9-274">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2a9d9-274">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="2a9d9-275">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2a9d9-275">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
