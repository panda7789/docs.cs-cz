---
ms.openlocfilehash: 241184d61d718fedfea396260e739d2dbc05c305
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620002"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="4eef0-101">SqlConnection se už nemůže připojit k SQL Server 1997 nebo databázím pomocí adaptéru VIA.</span><span class="sxs-lookup"><span data-stu-id="4eef0-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="4eef0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4eef0-102">Details</span></span>

<span data-ttu-id="4eef0-103">Připojení k databázím SQL Server s využitím [protokolu s adaptérem virtuálního rozhraní (Via)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) už nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="4eef0-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="4eef0-104">Protokol používaný pro připojení k databázi SQL Server je viditelný v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="4eef0-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="4eef0-105">PŘES připojení bude obsahovat prostřednictvím: &lt; servername &gt; .</span><span class="sxs-lookup"><span data-stu-id="4eef0-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="4eef0-106">Pokud se tato aplikace připojuje k SQL prostřednictvím jiného protokolu než přes (TCP: nebo NP:), neobjeví se žádná neprůlomová změna.</span><span class="sxs-lookup"><span data-stu-id="4eef0-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="4eef0-107">Připojení k SQL Server 7 (1997) už navíc nejsou podporovaná.</span><span class="sxs-lookup"><span data-stu-id="4eef0-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4eef0-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="4eef0-108">Suggestion</span></span>

<span data-ttu-id="4eef0-109">Protokol VIA je zastaralý, proto by se měl použít alternativní protokol pro připojení k databázím SQL.</span><span class="sxs-lookup"><span data-stu-id="4eef0-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="4eef0-110">Nejčastěji používaný protokol je TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="4eef0-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="4eef0-111">Další informace o připojení přes protokol TCP/IP najdete v tématu [Povolení protokolu TCP/IP pro instanci databáze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4eef0-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="4eef0-112">Pokud je databáze k databázi dostupná pouze v intranetu, protokol sdílených kanálů může poskytovat lepší výkon, pokud je síť pomalá.</span><span class="sxs-lookup"><span data-stu-id="4eef0-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="4eef0-113">Name</span><span class="sxs-lookup"><span data-stu-id="4eef0-113">Name</span></span>    | <span data-ttu-id="4eef0-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4eef0-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4eef0-115">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4eef0-115">Scope</span></span>   |<span data-ttu-id="4eef0-116">Edge</span><span class="sxs-lookup"><span data-stu-id="4eef0-116">Edge</span></span>|
|<span data-ttu-id="4eef0-117">Verze</span><span class="sxs-lookup"><span data-stu-id="4eef0-117">Version</span></span>|<span data-ttu-id="4eef0-118">4.5</span><span class="sxs-lookup"><span data-stu-id="4eef0-118">4.5</span></span>|
|<span data-ttu-id="4eef0-119">Typ</span><span class="sxs-lookup"><span data-stu-id="4eef0-119">Type</span></span>|<span data-ttu-id="4eef0-120">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4eef0-120">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4eef0-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4eef0-121">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)></li></ul>|
