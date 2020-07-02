---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617209"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="d3680-101">Analýza System. URI dodržuje specifikaci RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="d3680-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="d3680-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d3680-102">Details</span></span>

<span data-ttu-id="d3680-103">Analýza identifikátoru URI se změnila několika způsoby v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="d3680-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="d3680-104">Všimněte si ale, že tyto změny ovlivní jenom cílení kódu .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="d3680-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="d3680-105">Pokud jsou v binárním cíli .NET Framework 4,0, bude zjištěno staré chování.</span><span class="sxs-lookup"><span data-stu-id="d3680-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="d3680-106">Změny analýzy identifikátorů URI v .NET Framework 4,5 zahrnují:</span><span class="sxs-lookup"><span data-stu-id="d3680-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="d3680-107">Analýza identifikátoru URI provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="d3680-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="d3680-108">Normalizovaná forma kódu Unicode C bude provedena pouze v části hostitele identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="d3680-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="d3680-109">Neplatné mailto: identifikátory URI teď způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3680-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="d3680-110">Koncové tečky na konci segmentu cesty jsou nyní zachované.</span><span class="sxs-lookup"><span data-stu-id="d3680-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="d3680-111">`file://`Identifikátory URI neřídí `?` znak.</span><span class="sxs-lookup"><span data-stu-id="d3680-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="d3680-112">Řídicí znaky Unicode `U+0080` prostřednictvím `U+009F` se nepodporují.</span><span class="sxs-lookup"><span data-stu-id="d3680-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="d3680-113">Čárky `,` nebo nejsou `%2c` automaticky bez řídicích znaků.</span><span class="sxs-lookup"><span data-stu-id="d3680-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d3680-114">Návrh</span><span class="sxs-lookup"><span data-stu-id="d3680-114">Suggestion</span></span>

<span data-ttu-id="d3680-115">Pokud jsou nezbytné sémantiky analýzy identifikátorů URI .NET Framework 4,0 (často nejsou), mohou být použity při cílení na .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="d3680-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="d3680-116">To lze provést pomocí nástroje <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> na sestavení nebo prostřednictvím uživatelského rozhraní systému projektu sady Visual Studio na stránce vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="d3680-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="d3680-117">Name</span><span class="sxs-lookup"><span data-stu-id="d3680-117">Name</span></span>    | <span data-ttu-id="d3680-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d3680-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d3680-119">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d3680-119">Scope</span></span>   | <span data-ttu-id="d3680-120">Hlavní</span><span class="sxs-lookup"><span data-stu-id="d3680-120">Major</span></span>       |
| <span data-ttu-id="d3680-121">Verze</span><span class="sxs-lookup"><span data-stu-id="d3680-121">Version</span></span> | <span data-ttu-id="d3680-122">4.5</span><span class="sxs-lookup"><span data-stu-id="d3680-122">4.5</span></span>         |
| <span data-ttu-id="d3680-123">Typ</span><span class="sxs-lookup"><span data-stu-id="d3680-123">Type</span></span>    | <span data-ttu-id="d3680-124">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="d3680-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d3680-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d3680-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
