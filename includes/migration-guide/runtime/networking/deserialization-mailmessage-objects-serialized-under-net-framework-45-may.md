---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620038"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="e2a8d-101">Deserializace objektů MailMessage serializovaných v .NET Framework 4,5 může selhat.</span><span class="sxs-lookup"><span data-stu-id="e2a8d-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="e2a8d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e2a8d-102">Details</span></span>

<span data-ttu-id="e2a8d-103">Počínaje .NET Framework 4,5 <xref:System.Web.Mail.MailMessage> mohou objekty obsahovat jiné znaky než ASCII.</span><span class="sxs-lookup"><span data-stu-id="e2a8d-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="e2a8d-104">V .NET Framework 4 jsou podporovány pouze znaky ASCII.</span><span class="sxs-lookup"><span data-stu-id="e2a8d-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="e2a8d-105"><xref:System.Web.Mail.MailMessage>objekty, které obsahují znaky jiné než ASCII a které jsou serializovány pod .NET Framework 4,5 nebo novější, nelze deserializovat v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e2a8d-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2a8d-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="e2a8d-106">Suggestion</span></span>

<span data-ttu-id="e2a8d-107">Ujistěte se, že váš kód poskytuje zpracování výjimek při deserializaci <xref:System.Web.Mail.MailMessage> objektu.</span><span class="sxs-lookup"><span data-stu-id="e2a8d-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="e2a8d-108">Name</span><span class="sxs-lookup"><span data-stu-id="e2a8d-108">Name</span></span>    | <span data-ttu-id="e2a8d-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e2a8d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2a8d-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e2a8d-110">Scope</span></span>   |<span data-ttu-id="e2a8d-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="e2a8d-111">Minor</span></span>|
|<span data-ttu-id="e2a8d-112">Verze</span><span class="sxs-lookup"><span data-stu-id="e2a8d-112">Version</span></span>|<span data-ttu-id="e2a8d-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e2a8d-113">4.5</span></span>|
|<span data-ttu-id="e2a8d-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e2a8d-114">Type</span></span>|<span data-ttu-id="e2a8d-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e2a8d-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2a8d-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e2a8d-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
