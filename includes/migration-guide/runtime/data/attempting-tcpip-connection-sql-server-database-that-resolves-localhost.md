---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621782"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="dd54b-101">Pokus o připojení TCP/IP k databázi SQL Server, která se překládá na `localhost` neúspěšné</span><span class="sxs-lookup"><span data-stu-id="dd54b-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

#### <a name="details"></a><span data-ttu-id="dd54b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dd54b-102">Details</span></span>

<span data-ttu-id="dd54b-103">V .NET Framework 4,6 a 4.6.1 se při pokusu o připojení TCP/IP k databázi SQL Server, která překládá na chybu <code>localhost</code> , nezdařila chyba, &quot; došlo k chybě související se sítí nebo instancí při navazování připojení k SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dd54b-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="dd54b-104">Server se nenašel nebo nebyl dostupný.</span><span class="sxs-lookup"><span data-stu-id="dd54b-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="dd54b-105">Ověřte, zda je název instance správný a zda je SQL Server nakonfigurovaná tak, aby povolovala vzdálená připojení.</span><span class="sxs-lookup"><span data-stu-id="dd54b-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="dd54b-106">(poskytovatel: síťová rozhraní SQL, chyba: 26 – Chyba při hledání zadaného serveru nebo instance)&quot;</span><span class="sxs-lookup"><span data-stu-id="dd54b-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dd54b-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="dd54b-107">Suggestion</span></span>

<span data-ttu-id="dd54b-108">Tento problém byl vyřešen a předchozí chování obnoveno ve .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="dd54b-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="dd54b-109">Pokud se chcete připojit k databázi SQL Server, na kterou se překládá <code>localhost</code> , upgradujte na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="dd54b-109">To connect to a SQL Server database that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="dd54b-110">Name</span><span class="sxs-lookup"><span data-stu-id="dd54b-110">Name</span></span>    | <span data-ttu-id="dd54b-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dd54b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dd54b-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="dd54b-112">Scope</span></span>   |<span data-ttu-id="dd54b-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="dd54b-113">Minor</span></span>|
|<span data-ttu-id="dd54b-114">Verze</span><span class="sxs-lookup"><span data-stu-id="dd54b-114">Version</span></span>|<span data-ttu-id="dd54b-115">4.6</span><span class="sxs-lookup"><span data-stu-id="dd54b-115">4.6</span></span>|
|<span data-ttu-id="dd54b-116">Typ</span><span class="sxs-lookup"><span data-stu-id="dd54b-116">Type</span></span>|<span data-ttu-id="dd54b-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="dd54b-117">Runtime</span></span>|
