---
ms.openlocfilehash: 08c16f261338148619de2e484c73046b9d9a6bfe
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858523"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="124ab-101">Rozhraní .NET Framework 4.6 nepoužívá verzi 4.5.x.x při registraci v registru</span><span class="sxs-lookup"><span data-stu-id="124ab-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="124ab-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="124ab-102">Details</span></span>|<span data-ttu-id="124ab-103">Jak očekávat, klíč verze nastaven v registru (na <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pro rozhraní .NET Framework 4.6 začíná řetězcem "4.6", ne "4.5".</span><span class="sxs-lookup"><span data-stu-id="124ab-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="124ab-104">K tomu, že 4.6 je nová verze je to možné, a ten, který je kompatibilní s předchozím 4.5.x uvolní se musí aktualizovat aplikace, které závisí na těchto klíčů registru vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="124ab-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="124ab-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="124ab-105">Suggestion</span></span>|<span data-ttu-id="124ab-106">Aktualizace aplikace zjišťování pro rozhraní .NET Framework 4.5 nainstalujte tím, že hledají 4.5 klíčů registru také přijímat 4.6.</span><span class="sxs-lookup"><span data-stu-id="124ab-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="124ab-107">Scope</span><span class="sxs-lookup"><span data-stu-id="124ab-107">Scope</span></span>|<span data-ttu-id="124ab-108">Edge</span><span class="sxs-lookup"><span data-stu-id="124ab-108">Edge</span></span>|
|<span data-ttu-id="124ab-109">Version</span><span class="sxs-lookup"><span data-stu-id="124ab-109">Version</span></span>|<span data-ttu-id="124ab-110">4.6</span><span class="sxs-lookup"><span data-stu-id="124ab-110">4.6</span></span>|
|<span data-ttu-id="124ab-111">type</span><span class="sxs-lookup"><span data-stu-id="124ab-111">Type</span></span>|<span data-ttu-id="124ab-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="124ab-112">Runtime</span></span>|

