---
title: Statistiky Provider pro SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: f32b1c9f800a1ec2d80511cbbf46aba9840075d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365983"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="4a816-102">Statistiky Provider pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="4a816-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="4a816-103">Od verze rozhraní .NET Framework verze 2.0, zprostředkovatel dat .NET Framework pro SQL Server podporuje spuštění statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="4a816-104">Je nutné povolit statistiky nastavením <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> do objektu `True` po máte platné připojení objekt vytvořený.</span><span class="sxs-lookup"><span data-stu-id="4a816-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="4a816-105">Po statistiky jsou povolené, můžete zkontrolovat, je jako "snímek v čase" načtením <xref:System.Collections.IDictionary> odkazovat pomocí <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="4a816-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="4a816-106">Pomocí seznamu pro výčet jako sada položky slovníku dvojice název hodnota.</span><span class="sxs-lookup"><span data-stu-id="4a816-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="4a816-107">Tyto páry název/hodnota neuspořádaného.</span><span class="sxs-lookup"><span data-stu-id="4a816-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="4a816-108">Kdykoli můžete volat <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objekt, který chcete reset počítadla.</span><span class="sxs-lookup"><span data-stu-id="4a816-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="4a816-109">Pokud není povolený statistiky shromažďování, není vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="4a816-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="4a816-110">Kromě toho pokud <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> je volána bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> nutnosti nejprve zavolat, jsou hodnoty získané počáteční hodnoty pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="4a816-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="4a816-111">Pokud povolíte statistiky, spusťte aplikaci nějakou dobu a pak zakažte statistiky, hodnoty získané se projeví až do chvíle, kdy byly zakázány statistiky shromážděné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a816-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="4a816-112">Všechny statistické hodnoty získané jsou na základě jednotlivých připojení.</span><span class="sxs-lookup"><span data-stu-id="4a816-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="4a816-113">Statistické hodnoty, které jsou k dispozici</span><span class="sxs-lookup"><span data-stu-id="4a816-113">Statistical Values Available</span></span>  
 <span data-ttu-id="4a816-114">Aktuálně nejsou k dispozici od zprostředkovatele Microsoft SQL Server 18 různé položky.</span><span class="sxs-lookup"><span data-stu-id="4a816-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="4a816-115">Počet položek, které jsou k dispozici je přístupná prostřednictvím **počet** vlastnost <xref:System.Collections.IDictionary> rozhraní odkaz vrácený <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a816-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="4a816-116">Všechny čítače pro zprostředkovatele statistiky použít modul common language runtime <xref:System.Int64> typu (**dlouho** v C# a Visual Basic), což je 64bitová verze široké.</span><span class="sxs-lookup"><span data-stu-id="4a816-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="4a816-117">Maximální hodnota, která **int64** datového typu, podle definice **int64. MaxValue** pole, je ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="4a816-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="4a816-118">Pokud hodnoty čítačů dosáhnou tato maximální hodnota, se již nebude považovat za přesná.</span><span class="sxs-lookup"><span data-stu-id="4a816-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="4a816-119">To znamená, že **int64. MaxValue**-1((2^63)-2) je efektivně největší platnou hodnotu pro všechny statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a816-120">Slovník se používá k vrácení zprostředkovatele statistiky, protože může v budoucnu změnit počet, názvy a pořadí vrácených statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="4a816-121">Aplikace neměli spoléhat na určitou hodnotu se ve slovníku nalezena, ale měli místo toho zkontrolujte, jestli hodnota je k dispozici a odpovídajícím způsobem větev.</span><span class="sxs-lookup"><span data-stu-id="4a816-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="4a816-122">Následující tabulka popisuje aktuální statistické hodnoty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4a816-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="4a816-123">Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány mezi místní verze rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a816-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="4a816-124">Název klíče</span><span class="sxs-lookup"><span data-stu-id="4a816-124">Key Name</span></span>|<span data-ttu-id="4a816-125">Popis</span><span class="sxs-lookup"><span data-stu-id="4a816-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="4a816-126">Vrátí počet tabular data stream (TDS) paketů přijatých zprostředkovatele ze systému SQL Server po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="4a816-127">Vrátí počet paketů TDS odesílá do systému SQL Server zprostředkovatele poté, co byly povoleny statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="4a816-128">Velké příkazy může vyžadovat více vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4a816-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="4a816-129">Například, pokud velké příkaz odeslán do serveru a vyžaduje šesti pakety `ServerRoundtrips` se zvýší o jeden a `BuffersSent` se zvýší o šest.</span><span class="sxs-lookup"><span data-stu-id="4a816-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="4a816-130">Vrátí počet bajtů dat do TDS paketů přijatých zprostředkovatele ze systému SQL Server, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="4a816-131">Vrátí počet bajtů dat odeslaných k systému SQL Server v paketech TDS po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="4a816-132">Množství času (v milisekundách), které bylo připojení otevřené po povolili statistiky (celková doba připojení, pokud statistiky byly povoleny před otevřením připojení).</span><span class="sxs-lookup"><span data-stu-id="4a816-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="4a816-133">Vrátí počet opakovaných kurzoru byla otevřena prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="4a816-134">Všimněte si, že jen pro čtení jen nebo předání výsledky vrácené příkazů SELECT nejsou považovány za kurzory a proto neovlivní tento čítač.</span><span class="sxs-lookup"><span data-stu-id="4a816-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="4a816-135">Vrátí kumulativní množství času (v milisekundách), že má zprostředkovatel strávený zpracováváním po povolili statistiky, včetně doby čekání pro odpovědi ze serveru, jakož i čas strávený provádění kódu ve zprostředkovateli sám sebe.</span><span class="sxs-lookup"><span data-stu-id="4a816-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="4a816-136">Třídy, které zahrnují časování kódu jsou:</span><span class="sxs-lookup"><span data-stu-id="4a816-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="4a816-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="4a816-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="4a816-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="4a816-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="4a816-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="4a816-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="4a816-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="4a816-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="4a816-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="4a816-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="4a816-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="4a816-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="4a816-143">Pokud chcete zachovat výkon kritické členy co nejmenší, nejsou vypršel časový limit následující členy:</span><span class="sxs-lookup"><span data-stu-id="4a816-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="4a816-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="4a816-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="4a816-145">Tento [] – operátor (všechny přetížení)</span><span class="sxs-lookup"><span data-stu-id="4a816-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="4a816-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="4a816-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="4a816-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="4a816-147">GetChar</span></span><br /><br /> <span data-ttu-id="4a816-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="4a816-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="4a816-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="4a816-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="4a816-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="4a816-150">GetDouble</span></span><br /><br /> <span data-ttu-id="4a816-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="4a816-151">GetFloat</span></span><br /><br /> <span data-ttu-id="4a816-152">Getguid –</span><span class="sxs-lookup"><span data-stu-id="4a816-152">GetGuid</span></span><br /><br /> <span data-ttu-id="4a816-153">Getint16 –</span><span class="sxs-lookup"><span data-stu-id="4a816-153">GetInt16</span></span><br /><br /> <span data-ttu-id="4a816-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="4a816-154">GetInt32</span></span><br /><br /> <span data-ttu-id="4a816-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="4a816-155">GetInt64</span></span><br /><br /> <span data-ttu-id="4a816-156">GetName</span><span class="sxs-lookup"><span data-stu-id="4a816-156">GetName</span></span><br /><br /> <span data-ttu-id="4a816-157">Getordinal –</span><span class="sxs-lookup"><span data-stu-id="4a816-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="4a816-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="4a816-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="4a816-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="4a816-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="4a816-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="4a816-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="4a816-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="4a816-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="4a816-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="4a816-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="4a816-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="4a816-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="4a816-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="4a816-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="4a816-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="4a816-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="4a816-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="4a816-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="4a816-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="4a816-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="4a816-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="4a816-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="4a816-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="4a816-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="4a816-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="4a816-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="4a816-171">GetString –</span><span class="sxs-lookup"><span data-stu-id="4a816-171">GetString</span></span><br /><br /> <span data-ttu-id="4a816-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="4a816-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="4a816-173">Vrátí celkový počet příkazy INSERT, odstranění a aktualizaci provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="4a816-174">Vrátí celkový počet řádků, které jsou ovlivněné příkazy INSERT, odstranění a aktualizaci provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="4a816-175">Vrátí kumulativní množství času (v milisekundách), který zprostředkovatel stráví čekáním na odpovědi ze serveru, jakmile aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="4a816-176">Vrátí počet připravené příkazů provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="4a816-177">Vrátí počet prohlášení připravený prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="4a816-178">Vrátí počet příkazů SELECT provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="4a816-179">To zahrnuje příkazech NAČTENÍ načíst řádky z kurzory a počet příkazů SELECT se aktualizuje po konci <xref:System.Data.SqlClient.SqlDataReader> je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="4a816-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="4a816-180">Vrátí počet řádků, které jsou vybrané, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="4a816-181">Tento čítač zobrazuje všechny řádky generované příkazy SQL, i ty, které nejsou ve skutečnosti uplatníte volající.</span><span class="sxs-lookup"><span data-stu-id="4a816-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="4a816-182">Například zavření čtecí modul dat než si přečtete celou sadu výsledků neovlivní počet.</span><span class="sxs-lookup"><span data-stu-id="4a816-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="4a816-183">To zahrnuje řádky načítají kurzory prostřednictvím příkazech NAČTENÍ.</span><span class="sxs-lookup"><span data-stu-id="4a816-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="4a816-184">Vrátí počet připojení odeslat příkazy na server a obdržel odpověď zpět po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="4a816-185">Vrátí počet výsledků sad, které již byly použity, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="4a816-186">Například to bude zahrnovat všechny sadu výsledků vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="4a816-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="4a816-187">Pro kurzory považuje za každé operace načtení nebo bloku fetch sadu nezávislé výsledek.</span><span class="sxs-lookup"><span data-stu-id="4a816-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="4a816-188">Vrátí počet spuštění po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistické údaje, včetně odvolání uživatelské transakce.</span><span class="sxs-lookup"><span data-stu-id="4a816-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="4a816-189">Pokud je službou potvrzení automaticky na připojení, považuje za každý příkaz transakce.</span><span class="sxs-lookup"><span data-stu-id="4a816-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="4a816-190">Tento čítač zvýší počet transakcí, jakmile se spustí příkaz BEGIN TRAN, bez ohledu na to, jestli je transakce potvrzena nebo vrátit později.</span><span class="sxs-lookup"><span data-stu-id="4a816-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="4a816-191">Vrátí počet neupravený příkazy spustit prostřednictvím připojení, jakmile aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.</span><span class="sxs-lookup"><span data-stu-id="4a816-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="4a816-192">Načítání hodnoty</span><span class="sxs-lookup"><span data-stu-id="4a816-192">Retrieving a Value</span></span>  
 <span data-ttu-id="4a816-193">Následující aplikace konzoly ukazuje, jak povolit statistické údaje o připojení, načtěte čtyři hodnoty jednotlivých statistiky a zapisuje je do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4a816-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a816-194">Následující příklad používá vzorku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4a816-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="4a816-195">V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4a816-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="4a816-196">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="4a816-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
### <a name="retrieving-all-values"></a><span data-ttu-id="4a816-197">Načítání všechny hodnoty</span><span class="sxs-lookup"><span data-stu-id="4a816-197">Retrieving All Values</span></span>  
 <span data-ttu-id="4a816-198">Následující aplikace konzoly ukazuje, jak povolit statistické údaje o připojení, načíst všechny hodnoty k dispozici statistiky použití enumerátor a jejich zápis do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4a816-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a816-199">Následující příklad používá vzorku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4a816-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="4a816-200">V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4a816-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="4a816-201">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="4a816-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a816-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a816-202">See Also</span></span>  
 [<span data-ttu-id="4a816-203">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a816-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="4a816-204">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="4a816-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
