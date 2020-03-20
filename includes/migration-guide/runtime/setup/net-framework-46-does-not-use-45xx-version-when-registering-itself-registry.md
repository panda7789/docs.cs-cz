---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858523"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="7e230-101">Rozhraní .NET Framework 4.6 nepoužívá verzi 4.5.x.x při registraci v registru</span><span class="sxs-lookup"><span data-stu-id="7e230-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7e230-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7e230-102">Details</span></span>|<span data-ttu-id="7e230-103">Jak by se dalo očekávat, klíč verze <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>nastavený v registru (na ) pro rozhraní .NET Framework 4.6 začíná na "4.6", nikoli na "4.5".</span><span class="sxs-lookup"><span data-stu-id="7e230-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="7e230-104">Aplikace, které jsou závislé na těchto klíčích registru, aby věděly, které verze rozhraní .NET Framework jsou nainstalovány v počítači, by měly být aktualizovány, aby pochopily, že 4.6 je nová možná verze a verze, která je kompatibilní s předchozími verzemi 4.5.x.</span><span class="sxs-lookup"><span data-stu-id="7e230-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="7e230-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="7e230-105">Suggestion</span></span>|<span data-ttu-id="7e230-106">Aktualizujte aplikace sondování pro instalaci rozhraní .NET Framework 4.5 hledáním klíčů registru 4.5, které také přijměte 4.6.</span><span class="sxs-lookup"><span data-stu-id="7e230-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="7e230-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="7e230-107">Scope</span></span>|<span data-ttu-id="7e230-108">Edge</span><span class="sxs-lookup"><span data-stu-id="7e230-108">Edge</span></span>|
|<span data-ttu-id="7e230-109">Version</span><span class="sxs-lookup"><span data-stu-id="7e230-109">Version</span></span>|<span data-ttu-id="7e230-110">4.6</span><span class="sxs-lookup"><span data-stu-id="7e230-110">4.6</span></span>|
|<span data-ttu-id="7e230-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7e230-111">Type</span></span>|<span data-ttu-id="7e230-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="7e230-112">Runtime</span></span>|
