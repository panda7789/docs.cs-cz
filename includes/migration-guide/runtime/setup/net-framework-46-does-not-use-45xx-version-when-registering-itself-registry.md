---
ms.openlocfilehash: 09fb7a54fccd5cf37800483c64e2fa6a54681f11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621142"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="c8724-101">.NET Framework 4,6 nepoužívá při registraci sebe v registru verzi 4.5. x. x.</span><span class="sxs-lookup"><span data-stu-id="c8724-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

#### <a name="details"></a><span data-ttu-id="c8724-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c8724-102">Details</span></span>

<span data-ttu-id="c8724-103">Jak to může očekávat, klíč verze nastavený v registru (on <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> ) pro .NET Framework 4,6 začíná na ' 4,6 ', nikoli ' 4,5 '.</span><span class="sxs-lookup"><span data-stu-id="c8724-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="c8724-104">Aplikace, které jsou na těchto klíčích registru závislé na tom, aby věděli, které .NET Framework verze jsou nainstalované na počítači, by měly být aktualizované, aby zjistili, že 4,6 je nová možná verze a ta, která je kompatibilní s předchozími verzemi 4.5. x.</span><span class="sxs-lookup"><span data-stu-id="c8724-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c8724-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="c8724-105">Suggestion</span></span>

<span data-ttu-id="c8724-106">Aktualizujte aplikace zjišťováním pro instalaci .NET Framework 4,5, a to tak, že vyhledáte 4,5 klíče registru, abyste mohli taky přijmout 4,6.</span><span class="sxs-lookup"><span data-stu-id="c8724-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>

| <span data-ttu-id="c8724-107">Name</span><span class="sxs-lookup"><span data-stu-id="c8724-107">Name</span></span>    | <span data-ttu-id="c8724-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c8724-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c8724-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c8724-109">Scope</span></span>   |<span data-ttu-id="c8724-110">Edge</span><span class="sxs-lookup"><span data-stu-id="c8724-110">Edge</span></span>|
|<span data-ttu-id="c8724-111">Verze</span><span class="sxs-lookup"><span data-stu-id="c8724-111">Version</span></span>|<span data-ttu-id="c8724-112">4.6</span><span class="sxs-lookup"><span data-stu-id="c8724-112">4.6</span></span>|
|<span data-ttu-id="c8724-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c8724-113">Type</span></span>|<span data-ttu-id="c8724-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c8724-114">Runtime</span></span>|
