---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901941"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="2a4c1-101">MVC: JsonResult byl přesunut do microsoft.aspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="2a4c1-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="2a4c1-102">`JsonResult`přesunuta do `Microsoft.AspNetCore.Mvc.Core` sestavy.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="2a4c1-103">Tento typ byl definován v [souboru Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="2a4c1-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="2a4c1-104">Atribut [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) na úrovni sestavení `Microsoft.AspNetCore.Mvc.Formatters.Json` byl přidán k řešení tohoto problému pro většinu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="2a4c1-105">S aplikacemi, které používají knihovny třetích stran, se mohou vyskytnat problémy.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a4c1-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="2a4c1-106">Version introduced</span></span>

<span data-ttu-id="2a4c1-107">3.0 Náhled 6</span><span class="sxs-lookup"><span data-stu-id="2a4c1-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2a4c1-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="2a4c1-108">Old behavior</span></span>

<span data-ttu-id="2a4c1-109">Aplikace používající knihovnu založenou na 2,2 úspěšně vytvoří.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2a4c1-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="2a4c1-110">New behavior</span></span>

<span data-ttu-id="2a4c1-111">Aplikace používající knihovnu založenou na 2.2 se nezdaří kompilace.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="2a4c1-112">Je k dispozici chyba obsahující variantu následujícího textu:</span><span class="sxs-lookup"><span data-stu-id="2a4c1-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="2a4c1-113">Příklad takového problému naleznete v tématu [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="2a4c1-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2a4c1-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="2a4c1-114">Reason for change</span></span>

<span data-ttu-id="2a4c1-115">Změny na úrovni platformy ve složení ASP.NET Core, jak je popsáno na [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="2a4c1-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a4c1-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2a4c1-116">Recommended action</span></span>

<span data-ttu-id="2a4c1-117">Knihovny zkompilované proti verzi `Microsoft.AspNetCore.Mvc.Formatters.Json` 2.2 může být nutné překompilovat k řešení problému pro všechny spotřebitele.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="2a4c1-118">Pokud je to ovlivněno, obraťte se na autora knihovny.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-118">If affected, contact the library author.</span></span> <span data-ttu-id="2a4c1-119">Požádejte o rekompilaci knihovny, která bude cílit ASP.NET jádrem 3.0.</span><span class="sxs-lookup"><span data-stu-id="2a4c1-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="2a4c1-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2a4c1-120">Category</span></span>

<span data-ttu-id="2a4c1-121">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2a4c1-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a4c1-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2a4c1-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
