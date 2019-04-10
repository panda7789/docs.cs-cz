---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235384"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="e8880-101">Deserializace MailMessage objekty serializované v rozhraní .NET Framework 4.5 může selhat.</span><span class="sxs-lookup"><span data-stu-id="e8880-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e8880-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e8880-102">Details</span></span>|<span data-ttu-id="e8880-103">Od verze rozhraní .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objekty může obsahovat jiné znaky než ASCII.</span><span class="sxs-lookup"><span data-stu-id="e8880-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="e8880-104">V rozhraní .NET Framework 4 jsou podporovány pouze znaky ASCII.</span><span class="sxs-lookup"><span data-stu-id="e8880-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <xref:System.Web.Mail.MailMessage> <span data-ttu-id="e8880-105">objekty, které obsahují ne ASCII znaky a, které jsou serializovány v rozhraní .NET Framework 4.5 nebo novější, nemohou být deserializovány v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e8880-105">objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>|
|<span data-ttu-id="e8880-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e8880-106">Suggestion</span></span>|<span data-ttu-id="e8880-107">Ujistěte se, že váš kód obsahuje zpracování výjimek při deserializaci <xref:System.Web.Mail.MailMessage> objektu.</span><span class="sxs-lookup"><span data-stu-id="e8880-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>|
|<span data-ttu-id="e8880-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e8880-108">Scope</span></span>|<span data-ttu-id="e8880-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e8880-109">Minor</span></span>|
|<span data-ttu-id="e8880-110">Version</span><span class="sxs-lookup"><span data-stu-id="e8880-110">Version</span></span>|<span data-ttu-id="e8880-111">4.5</span><span class="sxs-lookup"><span data-stu-id="e8880-111">4.5</span></span>|
|<span data-ttu-id="e8880-112">Type</span><span class="sxs-lookup"><span data-stu-id="e8880-112">Type</span></span>|<span data-ttu-id="e8880-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e8880-113">Runtime</span></span>|
|<span data-ttu-id="e8880-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e8880-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
