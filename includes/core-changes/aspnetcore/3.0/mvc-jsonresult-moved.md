---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901941"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="331c0-101">MVC: JsonResult se přesunula do Microsoft. AspNetCore. Mvc. Core.</span><span class="sxs-lookup"><span data-stu-id="331c0-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="331c0-102">`JsonResult` přesunul do sestavení `Microsoft.AspNetCore.Mvc.Core`.</span><span class="sxs-lookup"><span data-stu-id="331c0-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="331c0-103">Tento typ se používá pro definování v [Microsoft. AspNetCore. Mvc. formátovací modul. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="331c0-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="331c0-104">Do `Microsoft.AspNetCore.Mvc.Formatters.Json` byl přidán atribut na úrovni sestavení [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) , který bude tento problém řešit pro většinu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="331c0-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="331c0-105">V aplikacích, které používají knihovny třetích stran, může dojít k problémům.</span><span class="sxs-lookup"><span data-stu-id="331c0-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="331c0-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="331c0-106">Version introduced</span></span>

<span data-ttu-id="331c0-107">3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="331c0-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="331c0-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="331c0-108">Old behavior</span></span>

<span data-ttu-id="331c0-109">Aplikace, která používá sestavení knihovny založené na 2,2, se úspěšně sestavuje.</span><span class="sxs-lookup"><span data-stu-id="331c0-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="331c0-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="331c0-110">New behavior</span></span>

<span data-ttu-id="331c0-111">V aplikaci, která používá knihovnu založenou na 2,2, se kompilace nezdařila.</span><span class="sxs-lookup"><span data-stu-id="331c0-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="331c0-112">K dispozici je chyba obsahující variaci následujícího textu:</span><span class="sxs-lookup"><span data-stu-id="331c0-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="331c0-113">Příklad takového problému naleznete v tématu [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="331c0-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="331c0-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="331c0-114">Reason for change</span></span>

<span data-ttu-id="331c0-115">Změny na úrovni platformy pro složení ASP.NET Core, jak je popsáno v tématu [ASPNET/oznámení # 325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="331c0-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="331c0-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="331c0-116">Recommended action</span></span>

<span data-ttu-id="331c0-117">Knihovny zkompilované proti verzi 2,2 `Microsoft.AspNetCore.Mvc.Formatters.Json` může být nutné znovu zkompilovat, aby se vyřešil problém pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="331c0-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="331c0-118">Pokud je to ovlivněno, obraťte se na autora knihovny.</span><span class="sxs-lookup"><span data-stu-id="331c0-118">If affected, contact the library author.</span></span> <span data-ttu-id="331c0-119">Požadavek na opětovnou kompilaci knihovny pro cílovou ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="331c0-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="331c0-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="331c0-120">Category</span></span>

<span data-ttu-id="331c0-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="331c0-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="331c0-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="331c0-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
