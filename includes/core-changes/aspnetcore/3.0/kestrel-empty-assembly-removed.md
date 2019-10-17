---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394378"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="f89bb-101">Kestrel: bylo odebráno prázdné sestavení HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f89bb-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="f89bb-102">Bylo odebráno sestavení <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="f89bb-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f89bb-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f89bb-103">Version introduced</span></span>

<span data-ttu-id="f89bb-104">3.0</span><span class="sxs-lookup"><span data-stu-id="f89bb-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f89bb-105">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f89bb-105">Reason for change</span></span>

<span data-ttu-id="f89bb-106">V ASP.NET Core 2,1 byl obsah `Microsoft.AspNetCore.Server.Kestrel.Https` přesunut do <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="f89bb-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="f89bb-107">Tato změna byla provedena neukončujícím způsobem pomocí atributů `[TypeForwardedTo]`.</span><span class="sxs-lookup"><span data-stu-id="f89bb-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f89bb-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f89bb-108">Recommended action</span></span>

- <span data-ttu-id="f89bb-109">Knihovny odkazující `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 by měly aktualizovat všechny závislosti ASP.NET Core na 2,1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f89bb-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="f89bb-110">V opačném případě mohou při načtení do aplikace ASP.NET Core 3,0 dojít k přerušení.</span><span class="sxs-lookup"><span data-stu-id="f89bb-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="f89bb-111">Aplikace a knihovny cílené na ASP.NET Core 2,1 a novější by měly odebrat všechny přímé odkazy na balíček NuGet `Microsoft.AspNetCore.Server.Kestrel.Https`.</span><span class="sxs-lookup"><span data-stu-id="f89bb-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="f89bb-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f89bb-112">Category</span></span>

<span data-ttu-id="f89bb-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f89bb-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f89bb-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f89bb-114">Affected APIs</span></span>

<span data-ttu-id="f89bb-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="f89bb-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
