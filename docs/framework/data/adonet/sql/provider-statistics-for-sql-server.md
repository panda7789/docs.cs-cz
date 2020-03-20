---
title: Statistiky zprostředkovatelů na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 5e37a04ff731a99664d636e0d4175f99214c2646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174508"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="419be-102">Statistiky zprostředkovatelů na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="419be-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="419be-103">Počínaje rozhraním .NET Framework verze 2.0 podporuje zprostředkovatel dat rozhraní .NET Framework pro SQL Server statistiky za běhu.</span><span class="sxs-lookup"><span data-stu-id="419be-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="419be-104">Statistiku je nutné <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> povolit <xref:System.Data.SqlClient.SqlConnection> nastavením `True` vlastnosti objektu po vytvoření platného objektu připojení.</span><span class="sxs-lookup"><span data-stu-id="419be-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="419be-105">Po povolení statistiky, můžete zkontrolovat jako "snímek v <xref:System.Collections.IDictionary> čase" <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> načtením <xref:System.Data.SqlClient.SqlConnection> odkazu prostřednictvím metody objektu.</span><span class="sxs-lookup"><span data-stu-id="419be-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="419be-106">Můžete vytvořit výčet prostřednictvím seznamu jako sadu položek slovníku pár ů názvu/hodnoty.</span><span class="sxs-lookup"><span data-stu-id="419be-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="419be-107">Tyto dvojice název/hodnota jsou neuspořádané.</span><span class="sxs-lookup"><span data-stu-id="419be-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="419be-108">Kdykoli můžete volat metodu <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> objektu <xref:System.Data.SqlClient.SqlConnection> k obnovení čítačů.</span><span class="sxs-lookup"><span data-stu-id="419be-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="419be-109">Pokud shromažďování statistik nebyla povolena, není generována výjimka.</span><span class="sxs-lookup"><span data-stu-id="419be-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="419be-110">Kromě toho <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> pokud je <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> volána bez byly volány jako první, načtené hodnoty jsou počáteční hodnoty pro každou položku.</span><span class="sxs-lookup"><span data-stu-id="419be-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="419be-111">Pokud povolíte statistiky, spusťte aplikaci na chvíli a potom zakázat statistiky, načtené hodnoty bude odrážet hodnoty shromážděné až do bodu, kde byly zakázány statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="419be-112">Všechny shromážděné statistické hodnoty jsou pro připojení.</span><span class="sxs-lookup"><span data-stu-id="419be-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="419be-113">Dostupné statistické hodnoty</span><span class="sxs-lookup"><span data-stu-id="419be-113">Statistical Values Available</span></span>  
 <span data-ttu-id="419be-114">V současné době je k dispozici 18 různých položek od poskytovatele serveru Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="419be-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="419be-115">Počet položek k dispozici lze přistupovat prostřednictvím <xref:System.Collections.IDictionary> **Count** vlastnost <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>odkaz rozhraní vrácené .</span><span class="sxs-lookup"><span data-stu-id="419be-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="419be-116">Všechny čítače pro statistiky zprostředkovatele <xref:System.Int64> používají typ clr **(long** v jazyce C# a Visual Basic), který je 64 bitů široký.</span><span class="sxs-lookup"><span data-stu-id="419be-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="419be-117">Maximální hodnota datového typu **int64,** jak je definováno **int64. MaxValue** pole, is ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="419be-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="419be-118">Když hodnoty čítačů dosáhnou této maximální hodnoty, neměly by být již považovány za přesné.</span><span class="sxs-lookup"><span data-stu-id="419be-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="419be-119">To znamená, že **int64. MaxValue**-1((2^63)-2) je skutečně největší platnou hodnotu pro všechny statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="419be-120">Slovník se používá pro vrácení statistiky zprostředkovatele, protože počet, názvy a pořadí vrácené statistiky se může v budoucnu změnit.</span><span class="sxs-lookup"><span data-stu-id="419be-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="419be-121">Aplikace by neměly spoléhat na konkrétní hodnotu, která se nachází ve slovníku, ale místo toho by měly zkontrolovat, zda hodnota existuje a odpovídajícím způsobem větví.</span><span class="sxs-lookup"><span data-stu-id="419be-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="419be-122">Následující tabulka popisuje aktuální dostupné statistické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="419be-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="419be-123">Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány v místních verzích rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="419be-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="419be-124">Název klíče</span><span class="sxs-lookup"><span data-stu-id="419be-124">Key Name</span></span>|<span data-ttu-id="419be-125">Popis</span><span class="sxs-lookup"><span data-stu-id="419be-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="419be-126">Vrátí počet paketů tabulkového datového proudu (TDS) přijatých zprostředkovatelem ze serveru SQL Server poté, co aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="419be-127">Vrátí počet paketů TDS odeslaných na SQL Server zprostředkovatelem po povolení statistik.</span><span class="sxs-lookup"><span data-stu-id="419be-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="419be-128">Velké příkazy mohou vyžadovat více vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="419be-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="419be-129">Například pokud velký příkaz je odeslán na server a `ServerRoundtrips` vyžaduje šest paketů, `BuffersSent` je zvýšil o jeden a je zvýšil o šest.</span><span class="sxs-lookup"><span data-stu-id="419be-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="419be-130">Vrátí počet bajtů dat v paketech TDS přijatých zprostředkovatelem ze serveru SQL Server, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="419be-131">Vrátí počet bajtů dat odeslaných na SQL Server v paketech TDS poté, co aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="419be-132">Doba (v milisekundách), po které bylo připojení otevřeno po povolení statistik (celkový čas připojení, pokud byly před otevřením připojení povoleny statistiky).</span><span class="sxs-lookup"><span data-stu-id="419be-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="419be-133">Vrátí počet otevření kurzoru prostřednictvím připojení, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="419be-134">Všimněte si, že jen pro čtení/předávání pouze výsledky vrácené příkazy SELECT nejsou považovány za kurzory a proto nemají vliv na tento čítač.</span><span class="sxs-lookup"><span data-stu-id="419be-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="419be-135">Vrátí kumulativní množství času (v milisekundách), které zprostředkovatel strávil zpracováním po povolení statistiky, včetně času stráveného čekáním na odpovědi ze serveru a času stráveného prováděním kódu v samotném zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="419be-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="419be-136">Třídy, které obsahují kód časování jsou:</span><span class="sxs-lookup"><span data-stu-id="419be-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="419be-137">Sqlconnection</span><span class="sxs-lookup"><span data-stu-id="419be-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="419be-138">Sqlcommand</span><span class="sxs-lookup"><span data-stu-id="419be-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="419be-139">Sqldatareader</span><span class="sxs-lookup"><span data-stu-id="419be-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="419be-140">Sqldataadapter</span><span class="sxs-lookup"><span data-stu-id="419be-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="419be-141">Sqltransaction</span><span class="sxs-lookup"><span data-stu-id="419be-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="419be-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="419be-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="419be-143">Chcete-li zachovat členy kritické pro výkon co nejmenší, nejsou načasovány následující členy:</span><span class="sxs-lookup"><span data-stu-id="419be-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="419be-144">Sqldatareader</span><span class="sxs-lookup"><span data-stu-id="419be-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="419be-145">tento[] operátor (všechna přetížení)</span><span class="sxs-lookup"><span data-stu-id="419be-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="419be-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="419be-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="419be-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="419be-147">GetChar</span></span><br /><br /> <span data-ttu-id="419be-148">Doba platnosti getdate</span><span class="sxs-lookup"><span data-stu-id="419be-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="419be-149">Získat decimal</span><span class="sxs-lookup"><span data-stu-id="419be-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="419be-150">Získat dvojitou</span><span class="sxs-lookup"><span data-stu-id="419be-150">GetDouble</span></span><br /><br /> <span data-ttu-id="419be-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="419be-151">GetFloat</span></span><br /><br /> <span data-ttu-id="419be-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="419be-152">GetGuid</span></span><br /><br /> <span data-ttu-id="419be-153">ZískatInt16</span><span class="sxs-lookup"><span data-stu-id="419be-153">GetInt16</span></span><br /><br /> <span data-ttu-id="419be-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="419be-154">GetInt32</span></span><br /><br /> <span data-ttu-id="419be-155">ZískatInt64</span><span class="sxs-lookup"><span data-stu-id="419be-155">GetInt64</span></span><br /><br /> <span data-ttu-id="419be-156">GetName</span><span class="sxs-lookup"><span data-stu-id="419be-156">GetName</span></span><br /><br /> <span data-ttu-id="419be-157">Getordinal</span><span class="sxs-lookup"><span data-stu-id="419be-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="419be-158">GetSqlBinární</span><span class="sxs-lookup"><span data-stu-id="419be-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="419be-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="419be-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="419be-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="419be-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="419be-161">Doba aplikace GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="419be-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="419be-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="419be-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="419be-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="419be-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="419be-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="419be-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="419be-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="419be-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="419be-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="419be-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="419be-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="419be-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="419be-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="419be-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="419be-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="419be-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="419be-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="419be-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="419be-171">GetString</span><span class="sxs-lookup"><span data-stu-id="419be-171">GetString</span></span><br /><br /> <span data-ttu-id="419be-172">Isdbnull</span><span class="sxs-lookup"><span data-stu-id="419be-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="419be-173">Vrátí celkový počet příkazů INSERT, DELETE a UPDATE provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="419be-174">Vrátí celkový počet řádků ovlivněných příkazy INSERT, DELETE a UPDATE provedenými prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="419be-175">Vrátí kumulativní množství času (v milisekundách), které zprostředkovatel strávil čekáním na odpovědi ze serveru, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="419be-176">Vrátí počet připravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="419be-177">Vrátí počet příkazů připravených prostřednictvím připojení, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="419be-178">Vrátí počet příkazů SELECT provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="419be-179">To zahrnuje FETCH příkazy načíst řádky z kurzory a počet <xref:System.Data.SqlClient.SqlDataReader> select příkazy je aktualizován při dosažení konce a.</span><span class="sxs-lookup"><span data-stu-id="419be-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="419be-180">Vrátí počet řádků vybraných po aplikaci začal používat zprostředkovatele a povolil statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="419be-181">Tento čítač odráží všechny řádky generované příkazy SQL, i ty, které nebyly skutečně spotřebovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="419be-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="419be-182">Například zavření čtečky dat před čtením celé sady výsledků nebude mít vliv na počet.</span><span class="sxs-lookup"><span data-stu-id="419be-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="419be-183">To zahrnuje řádky načtené z kurzorů prostřednictvím příkazů FETCH.</span><span class="sxs-lookup"><span data-stu-id="419be-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="419be-184">Vrátí počet, kolikrát připojení odeslané příkazy na server a dostal odpověď zpět, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="419be-185">Vrátí počet sad výsledků, které byly použity poté, co aplikace začala používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="419be-186">Například to by zahrnovalo všechny sady výsledků vrácené klientovi.</span><span class="sxs-lookup"><span data-stu-id="419be-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="419be-187">Pro kurzory každá operace načtení nebo načtení bloku je považována za nezávislou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="419be-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="419be-188">Vrátí počet uživatelských transakcí spuštěných po spuštění aplikace pomocí zprostředkovatele a povolil a povolil statistiky, včetně vrácení zpět.</span><span class="sxs-lookup"><span data-stu-id="419be-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="419be-189">Pokud je spuštěno připojení s automatickým potvrzením, každý příkaz je považován za transakci.</span><span class="sxs-lookup"><span data-stu-id="419be-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="419be-190">Tento čítač zintálí počet transakcí, jakmile begin tran příkaz je proveden, bez ohledu na to, zda je transakce potvrzena nebo vrácena zpět později.</span><span class="sxs-lookup"><span data-stu-id="419be-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="419be-191">Vrátí počet nepřipravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.</span><span class="sxs-lookup"><span data-stu-id="419be-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="419be-192">Načítání hodnoty</span><span class="sxs-lookup"><span data-stu-id="419be-192">Retrieving a Value</span></span>  
 <span data-ttu-id="419be-193">Následující konzolová aplikace ukazuje, jak povolit statistiky připojení, načíst čtyři jednotlivé statistické hodnoty a zapsat je do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="419be-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="419be-194">Následující příklad používá ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="419be-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="419be-195">Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že databáze je nainstalována a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="419be-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="419be-196">Podle potřeby upravte připojovací řetězec pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="419be-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
### <a name="retrieving-all-values"></a><span data-ttu-id="419be-197">Načítání všech hodnot</span><span class="sxs-lookup"><span data-stu-id="419be-197">Retrieving All Values</span></span>  
 <span data-ttu-id="419be-198">Následující konzolová aplikace ukazuje, jak povolit statistiky připojení, načíst všechny dostupné statistické hodnoty pomocí čítače výčtu a zapsat je do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="419be-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="419be-199">Následující příklad používá ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="419be-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="419be-200">Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že databáze je nainstalována a k dispozici v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="419be-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="419be-201">Podle potřeby upravte připojovací řetězec pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="419be-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="419be-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="419be-202">See also</span></span>

- [<span data-ttu-id="419be-203">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="419be-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="419be-204">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="419be-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
