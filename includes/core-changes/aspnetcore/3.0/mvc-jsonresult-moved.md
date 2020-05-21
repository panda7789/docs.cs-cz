---
ms.openlocfilehash: 1356f3eee5e2d8090d7d96aafc07a19507a1aff1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721037"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="e633b-101">MVC: JsonResult se přesunula do Microsoft. AspNetCore. Mvc. Core.</span><span class="sxs-lookup"><span data-stu-id="e633b-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="e633b-102">`JsonResult`byl přesunut do `Microsoft.AspNetCore.Mvc.Core` sestavení.</span><span class="sxs-lookup"><span data-stu-id="e633b-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="e633b-103">Tento typ se používá pro definování v [Microsoft. AspNetCore. Mvc. formátovací modul. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span><span class="sxs-lookup"><span data-stu-id="e633b-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="e633b-104">Byl přidán atribut na úrovni sestavení [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) k `Microsoft.AspNetCore.Mvc.Formatters.Json` tomuto problému pro většinu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e633b-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="e633b-105">V aplikacích, které používají knihovny třetích stran, může dojít k problémům.</span><span class="sxs-lookup"><span data-stu-id="e633b-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e633b-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e633b-106">Version introduced</span></span>

<span data-ttu-id="e633b-107">3,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="e633b-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e633b-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="e633b-108">Old behavior</span></span>

<span data-ttu-id="e633b-109">Aplikace, která používá sestavení knihovny založené na 2,2, se úspěšně sestavuje.</span><span class="sxs-lookup"><span data-stu-id="e633b-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e633b-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="e633b-110">New behavior</span></span>

<span data-ttu-id="e633b-111">V aplikaci, která používá knihovnu založenou na 2,2, se kompilace nezdařila.</span><span class="sxs-lookup"><span data-stu-id="e633b-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="e633b-112">K dispozici je chyba obsahující variaci následujícího textu:</span><span class="sxs-lookup"><span data-stu-id="e633b-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="e633b-113">Příklad takového problému naleznete v tématu [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).</span><span class="sxs-lookup"><span data-stu-id="e633b-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e633b-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="e633b-114">Reason for change</span></span>

<span data-ttu-id="e633b-115">Změny na úrovni platformy pro složení ASP.NET Core, jak je popsáno v tématu [ASPNET/oznámení # 325](https://github.com/aspnet/Announcements/issues/325).</span><span class="sxs-lookup"><span data-stu-id="e633b-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e633b-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e633b-116">Recommended action</span></span>

<span data-ttu-id="e633b-117">Knihovny zkompilované proti verzi 2,2 nástroje `Microsoft.AspNetCore.Mvc.Formatters.Json` mohou být nutné znovu kompilovat, aby vyřešily problém pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="e633b-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="e633b-118">Pokud je to ovlivněno, obraťte se na autora knihovny.</span><span class="sxs-lookup"><span data-stu-id="e633b-118">If affected, contact the library author.</span></span> <span data-ttu-id="e633b-119">Požadavek na opětovnou kompilaci knihovny pro cílovou ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e633b-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="e633b-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e633b-120">Category</span></span>

<span data-ttu-id="e633b-121">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e633b-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e633b-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e633b-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
