---
title: Statistiky zprostředkovatelů na SQL serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: d52c6bfdadf0a53ac4c5f62c37f1056c6702a82c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187069"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="7de5e-102">Statistiky zprostředkovatelů na SQL serveru</span><span class="sxs-lookup"><span data-stu-id="7de5e-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="7de5e-103">Od verze rozhraní .NET Framework verze 2.0, zprostředkovatele dat .NET Framework pro SQL Server podporuje běhové statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="7de5e-104">Je nutné povolit statistiky tak, že nastavíte <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu `True` po máte platné připojení objekt vytvořený.</span><span class="sxs-lookup"><span data-stu-id="7de5e-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="7de5e-105">Po statistiky jsou povolené, můžete zkontrolovat je jako "snímku v čase" načtením <xref:System.Collections.IDictionary> odkazovat prostřednictvím <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="7de5e-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="7de5e-106">Můžete zobrazit výčet prostřednictvím seznamu jako sada položek slovníku dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="7de5e-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="7de5e-107">Tyto páry název/hodnota Neseřazený.</span><span class="sxs-lookup"><span data-stu-id="7de5e-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="7de5e-108">Kdykoli můžete volat <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objekt resetovat počítadla.</span><span class="sxs-lookup"><span data-stu-id="7de5e-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="7de5e-109">Pokud statistiky shromažďování není povolený, výjimka se nevygeneroval.</span><span class="sxs-lookup"><span data-stu-id="7de5e-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="7de5e-110">Kromě toho pokud <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> je volána bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> s byla nejdříve volána, jsou hodnoty získané počáteční hodnoty pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="7de5e-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="7de5e-111">Pokud povolíte statistiky, spusťte aplikaci na dobu a potom zakázat statistiky, hodnoty získané bude odpovídat hodnotám shromážděných až do chvíle, kdy byly zakázány statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="7de5e-112">Na jednotlivá připojení jsou všechny statistické hodnoty shromážděné.</span><span class="sxs-lookup"><span data-stu-id="7de5e-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="7de5e-113">Statistické hodnoty, které jsou k dispozici</span><span class="sxs-lookup"><span data-stu-id="7de5e-113">Statistical Values Available</span></span>  
 <span data-ttu-id="7de5e-114">Aktuálně nejsou k dispozici od poskytovatele serveru Microsoft SQL Server 18 různých položek.</span><span class="sxs-lookup"><span data-stu-id="7de5e-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="7de5e-115">Počet položek, které jsou k dispozici je přístupná prostřednictvím **počet** vlastnost <xref:System.Collections.IDictionary> rozhraní vrácený odkaz <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="7de5e-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="7de5e-116">Všechny čítače pro statistiky zprostředkovatelů používat modul common language runtime <xref:System.Int64> typ (**dlouhé** v C# a Visual Basic), což je 64 bitů široké.</span><span class="sxs-lookup"><span data-stu-id="7de5e-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="7de5e-117">Maximální hodnota **int64** datový typ, podle definice **int64. Hodnota MaxValue** pole, je ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="7de5e-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="7de5e-118">Pokud hodnoty čítačů dosáhnou této maximální hodnotu, se mají už považovat přesné.</span><span class="sxs-lookup"><span data-stu-id="7de5e-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="7de5e-119">To znamená, že **int64. Hodnota MaxValue**-1((2^63)-2) je v podstatě největší platná hodnota pro všechny statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7de5e-120">Slovník se používá k vrácení statistiky zprostředkovatelů, protože číslo, názvy a pořadí vrácených statistik může v budoucnu změnit.</span><span class="sxs-lookup"><span data-stu-id="7de5e-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="7de5e-121">Neměli byste tedy spoléhat na určitou hodnotu se nenašel ve slovníku aplikace, ale místo toho zkontrolujte, zda hodnota je k dispozici a odpovídajícím způsobem větve.</span><span class="sxs-lookup"><span data-stu-id="7de5e-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="7de5e-122">Následující tabulka popisuje aktuální statistické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7de5e-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="7de5e-123">Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány do místní verze rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7de5e-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="7de5e-124">Název klíče</span><span class="sxs-lookup"><span data-stu-id="7de5e-124">Key Name</span></span>|<span data-ttu-id="7de5e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7de5e-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="7de5e-126">Vrátí počet datového proudu (protokolu TDS) paketů přijatých zprostředkovatele ze systému SQL Server po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="7de5e-127">Vrátí počet TDS paketům odeslaným do systému SQL Server zprostředkovatelem po statistiky byly povoleny.</span><span class="sxs-lookup"><span data-stu-id="7de5e-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="7de5e-128">Velké příkazů může vyžadovat více vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="7de5e-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="7de5e-129">Například, pokud velké příkaz odeslán do serveru a vyžaduje šest pakety `ServerRoundtrips` se zvýší o jedna a `BuffersSent` je zvýšen o šest.</span><span class="sxs-lookup"><span data-stu-id="7de5e-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="7de5e-130">Vrátí počet bajtů dat v paketech TDS přijatých zprostředkovatele ze systému SQL Server po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="7de5e-131">Vrátí počet bajtů dat odeslaných k systému SQL Server v paketech TDS po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="7de5e-132">Množství času (v milisekundách), které bylo připojení otevřené po statistiky byly povoleny (celková doba připojení, pokud statistiky byly povoleny před otevřením připojení).</span><span class="sxs-lookup"><span data-stu-id="7de5e-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="7de5e-133">Vrátí počet pokusů, které kurzor byl otevřen prostřednictvím připojení, jakmile aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="7de5e-134">Mějte na paměti, že – pouze pro předávání – jen pro čtení výsledky vrácené příkazy SELECT nejsou považovány za ukazatele a proto nemají vliv na tento čítač.</span><span class="sxs-lookup"><span data-stu-id="7de5e-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="7de5e-135">Vrátí souhrnně za dobu (v milisekundách), že zprostředkovatel strávil zpracování po povolili statistiky, včetně času strávenému čekáním odpovědi ze serveru, jakož i čas strávený prováděním kódu v samotného poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="7de5e-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="7de5e-136">Třídy, které obsahují kód časování jsou:</span><span class="sxs-lookup"><span data-stu-id="7de5e-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="7de5e-137">Připojení SqlConnection</span><span class="sxs-lookup"><span data-stu-id="7de5e-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="7de5e-138">Třídy SqlCommand</span><span class="sxs-lookup"><span data-stu-id="7de5e-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="7de5e-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="7de5e-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="7de5e-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="7de5e-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="7de5e-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="7de5e-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="7de5e-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="7de5e-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="7de5e-143">Pokud chcete zachovat výkon důležité členy co nejmenší, nejsou vypršel časový limit následující členy:</span><span class="sxs-lookup"><span data-stu-id="7de5e-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="7de5e-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="7de5e-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="7de5e-145">Tato [] – operátor (všechna přetížení)</span><span class="sxs-lookup"><span data-stu-id="7de5e-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="7de5e-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="7de5e-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="7de5e-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="7de5e-147">GetChar</span></span><br /><br /> <span data-ttu-id="7de5e-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="7de5e-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="7de5e-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="7de5e-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="7de5e-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="7de5e-150">GetDouble</span></span><br /><br /> <span data-ttu-id="7de5e-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="7de5e-151">GetFloat</span></span><br /><br /> <span data-ttu-id="7de5e-152">Getguid –</span><span class="sxs-lookup"><span data-stu-id="7de5e-152">GetGuid</span></span><br /><br /> <span data-ttu-id="7de5e-153">Getint16 –</span><span class="sxs-lookup"><span data-stu-id="7de5e-153">GetInt16</span></span><br /><br /> <span data-ttu-id="7de5e-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="7de5e-154">GetInt32</span></span><br /><br /> <span data-ttu-id="7de5e-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="7de5e-155">GetInt64</span></span><br /><br /> <span data-ttu-id="7de5e-156">GetName</span><span class="sxs-lookup"><span data-stu-id="7de5e-156">GetName</span></span><br /><br /> <span data-ttu-id="7de5e-157">Getordinal –</span><span class="sxs-lookup"><span data-stu-id="7de5e-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="7de5e-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="7de5e-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="7de5e-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="7de5e-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="7de5e-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="7de5e-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="7de5e-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="7de5e-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="7de5e-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="7de5e-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="7de5e-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="7de5e-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="7de5e-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="7de5e-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="7de5e-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="7de5e-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="7de5e-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="7de5e-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="7de5e-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="7de5e-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="7de5e-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="7de5e-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="7de5e-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="7de5e-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="7de5e-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="7de5e-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="7de5e-171">GetString</span><span class="sxs-lookup"><span data-stu-id="7de5e-171">GetString</span></span><br /><br /> <span data-ttu-id="7de5e-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="7de5e-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="7de5e-173">Vrátí celkový počet příkazů INSERT, odstranění a aktualizace provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="7de5e-174">Vrátí celkový počet řádky ovlivněné příkazy INSERT, odstranění a aktualizace provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="7de5e-175">Vrátí souhrnně za dobu (v milisekundách), který stráví poskytovateli čekání na odpovědi ze serveru po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="7de5e-176">Vrátí počet připravené příkazy provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="7de5e-177">Vrátí počet příkazů připravili prostřednictvím připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="7de5e-178">Vrátí počet příkazů SELECT provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="7de5e-179">Jedná se o NAČTENÍ příkazy načíst řádky z kurzory a počet pro příkazy SELECT se aktualizuje při ukončení <xref:System.Data.SqlClient.SqlDataReader> je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="7de5e-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="7de5e-180">Vrátí počet řádků, které vybraná aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="7de5e-181">Tento čítač zobrazuje všechny řádky generované příkazy SQL, včetně těch, které nejsou ve skutečnosti používané volající.</span><span class="sxs-lookup"><span data-stu-id="7de5e-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="7de5e-182">Například zavření čtecí modul dat před čtením úplná sada výsledků nebude mít vliv na počet.</span><span class="sxs-lookup"><span data-stu-id="7de5e-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="7de5e-183">To zahrnuje načtených z kurzory prostřednictvím příkazů načítání řádků.</span><span class="sxs-lookup"><span data-stu-id="7de5e-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="7de5e-184">Vrátí určený počet pokusů o připojení odesílat příkazy na serveru a obdržel odpověď zpět po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="7de5e-185">Vrátí počet výsledků sad, které již byly použity po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="7de5e-186">Například to bude zahrnovat všechny sadu výsledků, který je vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="7de5e-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="7de5e-187">Pro ukazatele považuje každé operace načítání nebo fetch bloku sady nezávislých výsledek.</span><span class="sxs-lookup"><span data-stu-id="7de5e-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="7de5e-188">Vrátí počet spuštění po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky, včetně vrácení zpět uživatelské transakce.</span><span class="sxs-lookup"><span data-stu-id="7de5e-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="7de5e-189">Pokud připojení je spuštěna s režim automatického potvrzení na, každý příkaz se považuje za transakci.</span><span class="sxs-lookup"><span data-stu-id="7de5e-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="7de5e-190">Tento čítač zvýší počet transakcí, poté, co je proveden příkaz BEGIN TRAN, bez ohledu na to, jestli transakce potvrzena nebo vrácena zpět později.</span><span class="sxs-lookup"><span data-stu-id="7de5e-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="7de5e-191">Vrátí počet neupravený příkazy provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.</span><span class="sxs-lookup"><span data-stu-id="7de5e-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="7de5e-192">Načítání hodnoty</span><span class="sxs-lookup"><span data-stu-id="7de5e-192">Retrieving a Value</span></span>  
 <span data-ttu-id="7de5e-193">Následující konzolové aplikace ukazuje, jak povolit statistické údaje o připojení, načíst čtyři hodnoty jednotlivých statistiky a zapíše je v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="7de5e-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7de5e-194">Následující příklad používá ukázku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7de5e-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="7de5e-195">Připojovací řetězec k dispozici ve vzorovém kódu předpokládá, že databáze je nainstalováný a dostupný na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="7de5e-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="7de5e-196">Úprava připojovacího řetězce podle potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="7de5e-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="7de5e-197">Načítání všech hodnot</span><span class="sxs-lookup"><span data-stu-id="7de5e-197">Retrieving All Values</span></span>  
 <span data-ttu-id="7de5e-198">Následující konzolové aplikace ukazuje, jak povolit statistické údaje o připojení, načíst všechny dostupné statistiky hodnoty pomocí čítače výčtu a zapisuje je do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="7de5e-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7de5e-199">Následující příklad používá ukázku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7de5e-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="7de5e-200">Připojovací řetězec k dispozici ve vzorovém kódu předpokládá, že databáze je nainstalováný a dostupný na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="7de5e-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="7de5e-201">Úprava připojovacího řetězce podle potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="7de5e-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7de5e-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="7de5e-202">See Also</span></span>  
 [<span data-ttu-id="7de5e-203">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7de5e-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="7de5e-204">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7de5e-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
