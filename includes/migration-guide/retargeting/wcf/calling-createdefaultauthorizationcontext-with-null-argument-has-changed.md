---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615706"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="fa060-101">Volání CreateDefaultAuthorizationContext s argumentem null se změnilo.</span><span class="sxs-lookup"><span data-stu-id="fa060-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="fa060-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="fa060-102">Details</span></span>

<span data-ttu-id="fa060-103">Implementace <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> vrácená voláním <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> s argumentem s hodnotou null authorizationPolicies se změnila jeho implementace v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="fa060-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fa060-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="fa060-104">Suggestion</span></span>

<span data-ttu-id="fa060-105">Ve výjimečných případech můžou aplikace WCF, které používají vlastní ověřování, zobrazovat rozdíly v chování.</span><span class="sxs-lookup"><span data-stu-id="fa060-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="fa060-106">V takových případech je možné předchozí chování obnovit jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="fa060-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="fa060-107">Znovu zkompilujte aplikaci a Zaměřte se na starší verzi .NET Framework než 4,6.</span><span class="sxs-lookup"><span data-stu-id="fa060-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="fa060-108">Pro služby hostované službou IIS použijte `<httpRuntime targetFramework="x.x">` element k zacílení na starší verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa060-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="fa060-109">Přidejte následující řádek do `<appSettings>` části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="fa060-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="fa060-110">Name</span><span class="sxs-lookup"><span data-stu-id="fa060-110">Name</span></span>    | <span data-ttu-id="fa060-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fa060-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa060-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="fa060-112">Scope</span></span>   | <span data-ttu-id="fa060-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="fa060-113">Minor</span></span>       |
| <span data-ttu-id="fa060-114">Verze</span><span class="sxs-lookup"><span data-stu-id="fa060-114">Version</span></span> | <span data-ttu-id="fa060-115">4.6</span><span class="sxs-lookup"><span data-stu-id="fa060-115">4.6</span></span>         |
| <span data-ttu-id="fa060-116">Typ</span><span class="sxs-lookup"><span data-stu-id="fa060-116">Type</span></span>    | <span data-ttu-id="fa060-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="fa060-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fa060-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fa060-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
