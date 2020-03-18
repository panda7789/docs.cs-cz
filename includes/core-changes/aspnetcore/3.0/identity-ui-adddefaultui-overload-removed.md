---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522646"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="d7df2-101">Identita: Přetížení metody AddDefaultUI bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="d7df2-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="d7df2-102">Počínaje ASP.NET Core 3.0, <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> přetížení metody již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d7df2-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d7df2-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="d7df2-103">Version introduced</span></span>

<span data-ttu-id="d7df2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d7df2-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d7df2-105">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d7df2-105">Reason for change</span></span>

<span data-ttu-id="d7df2-106">Tato změna byla výsledkem přijetí funkce statické webové datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="d7df2-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d7df2-107">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d7df2-107">Recommended action</span></span>

<span data-ttu-id="d7df2-108">Volání <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> místo přetížení.</span><span class="sxs-lookup"><span data-stu-id="d7df2-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="d7df2-109">Pokud používáte Bootstrap 3, přidejte také `<PropertyGroup>` následující řádek do prvku v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="d7df2-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="d7df2-110">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d7df2-110">Category</span></span>

<span data-ttu-id="d7df2-111">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d7df2-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d7df2-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d7df2-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
