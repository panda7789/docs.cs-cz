---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803713"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="c0617-101">Změnil se název souboru protokolu vytvořené metodou ObjectContext.CreateDatabase tak, aby odpovídaly specifikace serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0617-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c0617-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c0617-102">Details</span></span>|<span data-ttu-id="c0617-103">Když <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda je volána buď přímo nebo pomocí Code First se zprostředkovatelem SqlClient a je hodnota AttachDBFilename připojovacího řetězce, vytvoří soubor protokolu s názvem filename_log.ldf místo filename.ldf (kde název_souboru je název soubor určený hodnotou AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="c0617-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="c0617-104">Tato změna zlepšuje ladění poskytnutím souboru protokolu s názvem podle specifikace serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0617-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="c0617-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c0617-105">Suggestion</span></span>|<span data-ttu-id="c0617-106">Pokud název souboru protokolu je důležité pro aplikace, aplikace se musí aktualizovat můžete očekávat formát názvu souboru standardní _log.ldf.</span><span class="sxs-lookup"><span data-stu-id="c0617-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="c0617-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c0617-107">Scope</span></span>|<span data-ttu-id="c0617-108">Edge</span><span class="sxs-lookup"><span data-stu-id="c0617-108">Edge</span></span>|
|<span data-ttu-id="c0617-109">Version</span><span class="sxs-lookup"><span data-stu-id="c0617-109">Version</span></span>|<span data-ttu-id="c0617-110">4.5</span><span class="sxs-lookup"><span data-stu-id="c0617-110">4.5</span></span>|
|<span data-ttu-id="c0617-111">Type</span><span class="sxs-lookup"><span data-stu-id="c0617-111">Type</span></span>|<span data-ttu-id="c0617-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c0617-112">Runtime</span></span>|
|<span data-ttu-id="c0617-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c0617-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
