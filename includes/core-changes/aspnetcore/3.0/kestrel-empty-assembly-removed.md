---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394378"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="735e0-101">Poštolek: Prázdná sestava HTTPS byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="735e0-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="735e0-102">Sestavení <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="735e0-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="735e0-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="735e0-103">Version introduced</span></span>

<span data-ttu-id="735e0-104">3.0</span><span class="sxs-lookup"><span data-stu-id="735e0-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="735e0-105">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="735e0-105">Reason for change</span></span>

<span data-ttu-id="735e0-106">V ASP.NET Core 2.1 `Microsoft.AspNetCore.Server.Kestrel.Https` byl obsah <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>přesunut do .</span><span class="sxs-lookup"><span data-stu-id="735e0-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="735e0-107">Tato změna byla provedena nerozdělitelné `[TypeForwardedTo]` způsobem pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="735e0-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="735e0-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="735e0-108">Recommended action</span></span>

- <span data-ttu-id="735e0-109">Knihovny odkazující `Microsoft.AspNetCore.Server.Kestrel.Https` na 2.0 by měly aktualizovat všechny ASP.NET základní závislosti na 2.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="735e0-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="735e0-110">V opačném případě se mohou přerušit při načtení do aplikace core 3.0 ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="735e0-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="735e0-111">Aplikace a knihovny zaměřené ASP.NET Core 2.1 a novější `Microsoft.AspNetCore.Server.Kestrel.Https` by měly odebrat všechny přímé odkazy na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="735e0-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="735e0-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="735e0-112">Category</span></span>

<span data-ttu-id="735e0-113">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="735e0-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="735e0-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="735e0-114">Affected APIs</span></span>

<span data-ttu-id="735e0-115">Žádný</span><span class="sxs-lookup"><span data-stu-id="735e0-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
