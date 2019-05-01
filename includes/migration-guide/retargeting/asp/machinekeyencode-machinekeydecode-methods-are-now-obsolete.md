---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088475"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="64201-101">MachineKey.Encode a MachineKey.Decode metody jsou nyní zastaralé</span><span class="sxs-lookup"><span data-stu-id="64201-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="64201-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="64201-102">Details</span></span>|<span data-ttu-id="64201-103">Tyto metody jsou nyní zastaralé.</span><span class="sxs-lookup"><span data-stu-id="64201-103">These methods are now obsolete.</span></span> <span data-ttu-id="64201-104">Kompilace kódu volající tyto metody vede k upozornění překladače.</span><span class="sxs-lookup"><span data-stu-id="64201-104">Compilation of code that calls these methods produces a compiler warning.</span></span>|
|<span data-ttu-id="64201-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="64201-105">Suggestion</span></span>|<span data-ttu-id="64201-106">Doporučené alternativy jsou <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> a <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="64201-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="64201-107">Alternativně lze potlačit upozornění sestavení nebo lze se vyhnout pomocí staršího kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="64201-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="64201-108">Rozhraní API jsou stále podporovány.</span><span class="sxs-lookup"><span data-stu-id="64201-108">The APIs are still supported.</span></span>|
|<span data-ttu-id="64201-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="64201-109">Scope</span></span>|<span data-ttu-id="64201-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="64201-110">Minor</span></span>|
|<span data-ttu-id="64201-111">Version</span><span class="sxs-lookup"><span data-stu-id="64201-111">Version</span></span>|<span data-ttu-id="64201-112">4.5</span><span class="sxs-lookup"><span data-stu-id="64201-112">4.5</span></span>|
|<span data-ttu-id="64201-113">Type</span><span class="sxs-lookup"><span data-stu-id="64201-113">Type</span></span>|<span data-ttu-id="64201-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="64201-114">Retargeting</span></span>|
|<span data-ttu-id="64201-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="64201-115">Affected APIs</span></span>|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
