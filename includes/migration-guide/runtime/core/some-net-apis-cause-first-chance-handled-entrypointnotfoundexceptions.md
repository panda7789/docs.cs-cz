---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622041"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="3a37e-101">Některá rozhraní API .NET způsobují první šanci (zpracovává) EntryPointNotFoundExceptions</span><span class="sxs-lookup"><span data-stu-id="3a37e-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="3a37e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3a37e-102">Details</span></span>

<span data-ttu-id="3a37e-103">V .NET Framework 4,5, malý počet metod .NET začal s prvními možnostmi aktivována <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3a37e-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="3a37e-104">Tyto výjimky byly zpracovány v rámci .NET Framework, ale mohly by poškodit automatizaci testu, která neočekávala první pravděpodobnost výjimek.</span><span class="sxs-lookup"><span data-stu-id="3a37e-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="3a37e-105">Tato stejná rozhraní API přeruší některé scénáře ApiVerifier, pokud je povolená HighVersionLie.</span><span class="sxs-lookup"><span data-stu-id="3a37e-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3a37e-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="3a37e-106">Suggestion</span></span>

<span data-ttu-id="3a37e-107">Tato chyba se může vyhnout upgradem na .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="3a37e-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="3a37e-108">Alternativně lze automatizaci testů aktualizovat na nepřerušení při první popravděpodobném <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3a37e-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="3a37e-109">Name</span><span class="sxs-lookup"><span data-stu-id="3a37e-109">Name</span></span>    | <span data-ttu-id="3a37e-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3a37e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a37e-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3a37e-111">Scope</span></span>   |<span data-ttu-id="3a37e-112">Edge</span><span class="sxs-lookup"><span data-stu-id="3a37e-112">Edge</span></span>|
|<span data-ttu-id="3a37e-113">Verze</span><span class="sxs-lookup"><span data-stu-id="3a37e-113">Version</span></span>|<span data-ttu-id="3a37e-114">4.5</span><span class="sxs-lookup"><span data-stu-id="3a37e-114">4.5</span></span>|
|<span data-ttu-id="3a37e-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3a37e-115">Type</span></span>|<span data-ttu-id="3a37e-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3a37e-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a37e-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3a37e-117">Affected APIs</span></span>

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
