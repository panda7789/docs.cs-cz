---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620020"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="71985-101">Název souboru protokolu vytvořený metodou ObjectContext. CreateDatabase se změnil tak, aby odpovídal SQL Server specifikacím.</span><span class="sxs-lookup"><span data-stu-id="71985-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="71985-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="71985-102">Details</span></span>

<span data-ttu-id="71985-103">Pokud <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> je metoda volána přímo nebo pomocí Code First se zprostředkovatelem SqlClient a hodnotou AttachDBFilename v připojovacím řetězci, vytvoří soubor protokolu s názvem filename_log. ldf namísto filename. ldf (kde filename je název souboru určeného hodnotou AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="71985-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="71985-104">Tato změna zlepšuje ladění poskytnutím souboru protokolu s názvem podle specifikace serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="71985-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="71985-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="71985-105">Suggestion</span></span>

<span data-ttu-id="71985-106">Pokud je název souboru protokolu pro aplikaci důležitý, měla by být aplikace aktualizována tak, aby byla očekávána standardní _log formát názvu souboru. ldf.</span><span class="sxs-lookup"><span data-stu-id="71985-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="71985-107">Name</span><span class="sxs-lookup"><span data-stu-id="71985-107">Name</span></span>    | <span data-ttu-id="71985-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="71985-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="71985-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="71985-109">Scope</span></span>   |<span data-ttu-id="71985-110">Edge</span><span class="sxs-lookup"><span data-stu-id="71985-110">Edge</span></span>|
|<span data-ttu-id="71985-111">Verze</span><span class="sxs-lookup"><span data-stu-id="71985-111">Version</span></span>|<span data-ttu-id="71985-112">4.5</span><span class="sxs-lookup"><span data-stu-id="71985-112">4.5</span></span>|
|<span data-ttu-id="71985-113">Typ</span><span class="sxs-lookup"><span data-stu-id="71985-113">Type</span></span>|<span data-ttu-id="71985-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="71985-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71985-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="71985-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
