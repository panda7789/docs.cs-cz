---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617181"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="64c80-101">Metody MachineKey. Encode a MachineKey. dekódování jsou nyní zastaralé.</span><span class="sxs-lookup"><span data-stu-id="64c80-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="64c80-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="64c80-102">Details</span></span>

<span data-ttu-id="64c80-103">Tyto metody jsou nyní zastaralé.</span><span class="sxs-lookup"><span data-stu-id="64c80-103">These methods are now obsolete.</span></span> <span data-ttu-id="64c80-104">Kompilace kódu volající tyto metody vede k upozornění překladače.</span><span class="sxs-lookup"><span data-stu-id="64c80-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="64c80-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="64c80-105">Suggestion</span></span>

<span data-ttu-id="64c80-106">Doporučené alternativy jsou <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> a <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="64c80-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="64c80-107">Alternativně lze upozornění sestavení potlačit, nebo je lze zabránit pomocí staršího kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="64c80-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="64c80-108">Rozhraní API jsou pořád podporovaná.</span><span class="sxs-lookup"><span data-stu-id="64c80-108">The APIs are still supported.</span></span>

| <span data-ttu-id="64c80-109">Name</span><span class="sxs-lookup"><span data-stu-id="64c80-109">Name</span></span>    | <span data-ttu-id="64c80-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="64c80-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="64c80-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="64c80-111">Scope</span></span>   | <span data-ttu-id="64c80-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="64c80-112">Minor</span></span>       |
| <span data-ttu-id="64c80-113">Verze</span><span class="sxs-lookup"><span data-stu-id="64c80-113">Version</span></span> | <span data-ttu-id="64c80-114">4.5</span><span class="sxs-lookup"><span data-stu-id="64c80-114">4.5</span></span>         |
| <span data-ttu-id="64c80-115">Typ</span><span class="sxs-lookup"><span data-stu-id="64c80-115">Type</span></span>    | <span data-ttu-id="64c80-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="64c80-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="64c80-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="64c80-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
