---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637194"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="12888-101">Identita: Přetížení metody AddDefaultUI bylo odebráno.</span><span class="sxs-lookup"><span data-stu-id="12888-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="12888-102">Počínaje ASP.NET Core 3.0, [identityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) přetížení metody již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="12888-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12888-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="12888-103">Version introduced</span></span>

<span data-ttu-id="12888-104">3.0</span><span class="sxs-lookup"><span data-stu-id="12888-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="12888-105">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="12888-105">Reason for change</span></span>

<span data-ttu-id="12888-106">Tato změna byla výsledkem přijetí funkce statické webové datové zdroje.</span><span class="sxs-lookup"><span data-stu-id="12888-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12888-107">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="12888-107">Recommended action</span></span>

<span data-ttu-id="12888-108">Volání <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> namísto přetížení, které trvá dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="12888-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="12888-109">Pokud používáte Bootstrap 3, přidejte také `<PropertyGroup>` následující řádek do prvku v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="12888-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="12888-110">Kategorie</span><span class="sxs-lookup"><span data-stu-id="12888-110">Category</span></span>

<span data-ttu-id="12888-111">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="12888-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12888-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="12888-112">Affected APIs</span></span>

[<span data-ttu-id="12888-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="12888-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
