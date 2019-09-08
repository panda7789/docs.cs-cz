---
title: Statistiky zprostředkovatelů na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b6fa4207531e86cbde8657d0c47596f22c886f89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791868"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="86231-102">Statistiky zprostředkovatelů na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="86231-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="86231-103">Počínaje verzí 2,0 .NET Framework .NET Framework Zprostředkovatel dat pro SQL Server podporuje statistiku runtime.</span><span class="sxs-lookup"><span data-stu-id="86231-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="86231-104">Chcete-li vytvořit platný objekt připojení <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> , je nutné <xref:System.Data.SqlClient.SqlConnection> povolit statistiku nastavením vlastnosti objektu na `True` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86231-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="86231-105">Po povolení statistik je můžete zkontrolovat jako "snímek v čase" načtením <xref:System.Collections.IDictionary> odkazu <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> prostřednictvím metody <xref:System.Data.SqlClient.SqlConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="86231-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="86231-106">Seznam můžete zobrazit jako sadu položek slovníku dvojice název/hodnota.</span><span class="sxs-lookup"><span data-stu-id="86231-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="86231-107">Tyto páry název/hodnota jsou neseřazené.</span><span class="sxs-lookup"><span data-stu-id="86231-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="86231-108">V každém okamžiku můžete zavolat <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu pro resetování čítačů.</span><span class="sxs-lookup"><span data-stu-id="86231-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="86231-109">Pokud není shromažďování statistických údajů povolené, výjimka se nevygeneruje.</span><span class="sxs-lookup"><span data-stu-id="86231-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="86231-110">Kromě toho, pokud <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> je volána, <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> aniž by byla volána jako první, jsou načtené hodnoty počátečními hodnotami pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="86231-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="86231-111">Pokud povolíte statistiku, spusťte aplikaci za chvíli a pak zakažte statistiku. načtené hodnoty budou odpovídat hodnotám shromážděným do okamžiku, kdy byly statistiky zakázány.</span><span class="sxs-lookup"><span data-stu-id="86231-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="86231-112">Všechny shromážděné statistické hodnoty jsou založené na jednotlivých připojeních.</span><span class="sxs-lookup"><span data-stu-id="86231-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="86231-113">Statistické hodnoty k dispozici</span><span class="sxs-lookup"><span data-stu-id="86231-113">Statistical Values Available</span></span>  
 <span data-ttu-id="86231-114">V současné době je od poskytovatele Microsoft SQL Server k dispozici 18 různých položek.</span><span class="sxs-lookup"><span data-stu-id="86231-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="86231-115">K dostupnému počtu položek lze získat přístup prostřednictvím <xref:System.Collections.IDictionary> vlastnosti **Count** odkazu <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>rozhraní, který vrátil.</span><span class="sxs-lookup"><span data-stu-id="86231-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="86231-116">Všechny čítače pro statistiku poskytovatele používají <xref:System.Int64> typ modulu CLR (**Long** in C# a Visual Basic), což je 64 bitů ve světě.</span><span class="sxs-lookup"><span data-stu-id="86231-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="86231-117">Maximální hodnota datového typu **Int64** , jak je definována hodnotou **Int64. Pole MaxValue** , je ((2 ^ 63)-1)).</span><span class="sxs-lookup"><span data-stu-id="86231-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="86231-118">Pokud hodnoty pro čítače dosáhnou této maximální hodnoty, neměly by se již považovat za přesné.</span><span class="sxs-lookup"><span data-stu-id="86231-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="86231-119">To znamená, že **Int64. MaxValue**-1 ((2 ^ 63)-2) je nejvýhodnější největší platná hodnota pro všechny statistiky.</span><span class="sxs-lookup"><span data-stu-id="86231-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86231-120">Slovník se používá pro vracení statistik poskytovatele, protože počet, názvy a pořadí vrácených statistik se může v budoucnu změnit.</span><span class="sxs-lookup"><span data-stu-id="86231-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="86231-121">Aplikace by neměly spoléhat na konkrétní hodnotu nalezenou ve slovníku, ale měla by se místo toho kontrolovat, zda je tato hodnota a odpovídajícím způsobem větev.</span><span class="sxs-lookup"><span data-stu-id="86231-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="86231-122">Následující tabulka popisuje aktuální statistické hodnoty k dispozici.</span><span class="sxs-lookup"><span data-stu-id="86231-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="86231-123">Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány mezi regionální verze .NET Framework Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86231-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="86231-124">Název klíče</span><span class="sxs-lookup"><span data-stu-id="86231-124">Key Name</span></span>|<span data-ttu-id="86231-125">Popis</span><span class="sxs-lookup"><span data-stu-id="86231-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="86231-126">Vrátí počet paketů protokolu TDS (Tabular data Stream) přijatých zprostředkovatelem od SQL Server poté, co aplikace začne používat zprostředkovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="86231-127">Vrátí počet paketů TDS odeslaných do SQL Server zprostředkovatelem po povolení statistiky.</span><span class="sxs-lookup"><span data-stu-id="86231-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="86231-128">Velké příkazy mohou vyžadovat více vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="86231-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="86231-129">Například pokud je na server odeslán velký příkaz a vyžaduje šest paketů, `ServerRoundtrips` je zvýšen o 1 a `BuffersSent` zvýšen o šest.</span><span class="sxs-lookup"><span data-stu-id="86231-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="86231-130">Vrátí počet bajtů dat v paketech TDS přijatých poskytovatelem z SQL Server, jakmile aplikace začne používat zprostředkovatele a má povolené statistiky.</span><span class="sxs-lookup"><span data-stu-id="86231-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="86231-131">Vrátí počet bajtů dat odeslaných do SQL Server v paketech TDS po spuštění aplikace pomocí poskytovatele a povolených statistik.</span><span class="sxs-lookup"><span data-stu-id="86231-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="86231-132">Množství času (v milisekundách), po které bylo připojení otevřeno po povolení statistiky (celková doba připojení, pokud byla statistika povolena před otevřením připojení).</span><span class="sxs-lookup"><span data-stu-id="86231-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="86231-133">Vrátí počet otevření kurzoru prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="86231-134">Všimněte si, že pouze výsledky jen pro čtení nebo dopředné pomocí příkazu SELECT nejsou považovány za kurzory, a proto nemají vliv na tento čítač.</span><span class="sxs-lookup"><span data-stu-id="86231-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="86231-135">Vrátí kumulativní množství času (v milisekundách), které poskytovatel strávil zpracováním po povolení statistik, včetně času stráveného čekáním na odpovědi ze serveru a času stráveného prováděním kódu v samotném zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="86231-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="86231-136">Třídy, které obsahují kód časování, jsou:</span><span class="sxs-lookup"><span data-stu-id="86231-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="86231-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="86231-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="86231-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="86231-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="86231-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="86231-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="86231-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="86231-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="86231-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="86231-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="86231-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="86231-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="86231-143">Chcete-li udržet co nejzávažnější členy co nejmenší, nevypršela platnost následujících členů:</span><span class="sxs-lookup"><span data-stu-id="86231-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="86231-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="86231-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="86231-145">Tento operátor [] (všechna přetížení)</span><span class="sxs-lookup"><span data-stu-id="86231-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="86231-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="86231-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="86231-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="86231-147">GetChar</span></span><br /><br /> <span data-ttu-id="86231-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="86231-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="86231-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="86231-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="86231-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="86231-150">GetDouble</span></span><br /><br /> <span data-ttu-id="86231-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="86231-151">GetFloat</span></span><br /><br /> <span data-ttu-id="86231-152">GetGUID –</span><span class="sxs-lookup"><span data-stu-id="86231-152">GetGuid</span></span><br /><br /> <span data-ttu-id="86231-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="86231-153">GetInt16</span></span><br /><br /> <span data-ttu-id="86231-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="86231-154">GetInt32</span></span><br /><br /> <span data-ttu-id="86231-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="86231-155">GetInt64</span></span><br /><br /> <span data-ttu-id="86231-156">GetName</span><span class="sxs-lookup"><span data-stu-id="86231-156">GetName</span></span><br /><br /> <span data-ttu-id="86231-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="86231-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="86231-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="86231-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="86231-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="86231-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="86231-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="86231-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="86231-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="86231-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="86231-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="86231-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="86231-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="86231-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="86231-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="86231-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="86231-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="86231-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="86231-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="86231-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="86231-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="86231-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="86231-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="86231-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="86231-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="86231-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="86231-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="86231-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="86231-171">GetString</span><span class="sxs-lookup"><span data-stu-id="86231-171">GetString</span></span><br /><br /> <span data-ttu-id="86231-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="86231-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="86231-173">Vrátí celkový počet příkazů INSERT, DELETE a UPDATE provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="86231-174">Vrátí celkový počet řádků ovlivněných příkazy INSERT, DELETE a UPDATE prováděné prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a má povolené statistiky.</span><span class="sxs-lookup"><span data-stu-id="86231-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="86231-175">Vrátí kumulativní množství času (v milisekundách), které poskytovatel stráví čekáním na odpovědi ze serveru, jakmile aplikace začne používat poskytovatele a má povolené statistiky.</span><span class="sxs-lookup"><span data-stu-id="86231-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="86231-176">Vrátí počet připravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="86231-177">Vrátí počet příkazů připravených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="86231-178">Vrátí počet příkazů SELECT provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="86231-179">To zahrnuje příkazy Fetch pro načtení řádků z kurzorů a počet příkazů SELECT je aktualizován po dosažení konce <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="86231-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="86231-180">Vrátí počet řádků vybraných po zahájení aplikace pomocí poskytovatele a povolených statistik.</span><span class="sxs-lookup"><span data-stu-id="86231-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="86231-181">Tento čítač odráží všechny řádky vygenerované příkazy SQL, a to i ty, které volající skutečně nevyužil.</span><span class="sxs-lookup"><span data-stu-id="86231-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="86231-182">Například zavření čtecího modulu dat před čtením celé sady výsledků by neovlivnilo počet.</span><span class="sxs-lookup"><span data-stu-id="86231-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="86231-183">To zahrnuje řádky načtené z kurzorů prostřednictvím příkazů FETCH.</span><span class="sxs-lookup"><span data-stu-id="86231-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="86231-184">Vrátí počet pokusů o připojení odeslaných příkazů serveru a odeslání odpovědi zpět, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="86231-185">Vrátí počet sad výsledků, které byly použity poté, co aplikace začala používat poskytovatele a má povolené statistiky.</span><span class="sxs-lookup"><span data-stu-id="86231-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="86231-186">Například by obsahovala sadu výsledků vrácenou klientovi.</span><span class="sxs-lookup"><span data-stu-id="86231-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="86231-187">Pro kurzory se každá operace Fetch nebo Block-Fetch považuje za nezávislou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="86231-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="86231-188">Vrátí počet uživatelských transakcí spuštěných po zahájení aplikace pomocí poskytovatele a povolených statistik, včetně vrácení zpět.</span><span class="sxs-lookup"><span data-stu-id="86231-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="86231-189">Pokud je připojení spuštěné s automatickým potvrzením, každý příkaz se považuje za transakci.</span><span class="sxs-lookup"><span data-stu-id="86231-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="86231-190">Tento čítač zvyšuje počet transakcí hned po provedení příkazu BEGIN TRAN, bez ohledu na to, zda je transakce potvrzena nebo vrácena zpět později.</span><span class="sxs-lookup"><span data-stu-id="86231-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="86231-191">Vrátí počet nepřipravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.</span><span class="sxs-lookup"><span data-stu-id="86231-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="86231-192">Načítání hodnoty</span><span class="sxs-lookup"><span data-stu-id="86231-192">Retrieving a Value</span></span>  
 <span data-ttu-id="86231-193">Následující aplikace konzoly ukazuje, jak povolit statistiku připojení, načíst čtyři jednotlivé statistické hodnoty a zapsat je do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="86231-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86231-194">Následující příklad používá ukázkovou databázi **AdventureWorks** , která je součástí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="86231-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="86231-195">Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že je databáze nainstalovaná a dostupná v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="86231-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="86231-196">Upravte připojovací řetězec podle potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="86231-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrieve it from a configuration file.  
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
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="86231-197">Načítání všech hodnot</span><span class="sxs-lookup"><span data-stu-id="86231-197">Retrieving All Values</span></span>  
 <span data-ttu-id="86231-198">Následující aplikace konzoly ukazuje, jak povolit statistiku připojení, načíst všechny dostupné statistické hodnoty pomocí enumerátoru a zapsat je do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="86231-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86231-199">Následující příklad používá ukázkovou databázi **AdventureWorks** , která je součástí SQL Server.</span><span class="sxs-lookup"><span data-stu-id="86231-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="86231-200">Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že je databáze nainstalovaná a dostupná v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="86231-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="86231-201">Upravte připojovací řetězec podle potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="86231-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrieve it from a configuration file.  
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
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="86231-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86231-202">See also</span></span>

- [<span data-ttu-id="86231-203">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86231-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="86231-204">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86231-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
