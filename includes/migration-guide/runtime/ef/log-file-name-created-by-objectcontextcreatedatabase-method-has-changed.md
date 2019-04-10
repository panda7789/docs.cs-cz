---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235391"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="a1c9d-101">Změnil se název souboru protokolu vytvořené metodou ObjectContext.CreateDatabase tak, aby odpovídaly specifikace serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="a1c9d-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a1c9d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a1c9d-102">Details</span></span>|<span data-ttu-id="a1c9d-103">Když <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda je volána buď přímo nebo pomocí Code First se zprostředkovatelem SqlClient a je hodnota AttachDBFilename připojovacího řetězce, vytvoří soubor protokolu s názvem filename_log.ldf místo filename.ldf (kde název_souboru je název soubor určený hodnotou AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="a1c9d-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="a1c9d-104">Tato změna zlepšuje ladění poskytnutím souboru protokolu s názvem podle specifikace serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a1c9d-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="a1c9d-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="a1c9d-105">Suggestion</span></span>|<span data-ttu-id="a1c9d-106">Pokud název souboru protokolu je důležité pro aplikace, aplikace se musí aktualizovat můžete očekávat formát názvu souboru standardní _log.ldf.</span><span class="sxs-lookup"><span data-stu-id="a1c9d-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="a1c9d-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a1c9d-107">Scope</span></span>|<span data-ttu-id="a1c9d-108">Edge</span><span class="sxs-lookup"><span data-stu-id="a1c9d-108">Edge</span></span>|
|<span data-ttu-id="a1c9d-109">Version</span><span class="sxs-lookup"><span data-stu-id="a1c9d-109">Version</span></span>|<span data-ttu-id="a1c9d-110">4.5</span><span class="sxs-lookup"><span data-stu-id="a1c9d-110">4.5</span></span>|
|<span data-ttu-id="a1c9d-111">Type</span><span class="sxs-lookup"><span data-stu-id="a1c9d-111">Type</span></span>|<span data-ttu-id="a1c9d-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="a1c9d-112">Runtime</span></span>|
|<span data-ttu-id="a1c9d-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a1c9d-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
