---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394345"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="52e00-101">Identita: Výchozí bootstrap verze ui změněna</span><span class="sxs-lookup"><span data-stu-id="52e00-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="52e00-102">Počínaje ASP.NET Core 3.0, Identity UI výchozí použití verze 4 Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="52e00-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="52e00-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="52e00-103">Version introduced</span></span>

<span data-ttu-id="52e00-104">3.0</span><span class="sxs-lookup"><span data-stu-id="52e00-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="52e00-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="52e00-105">Old behavior</span></span>

<span data-ttu-id="52e00-106">Volání `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody bylo stejné jako`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="52e00-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="52e00-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="52e00-107">New behavior</span></span>

<span data-ttu-id="52e00-108">Volání `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody je stejné jako`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="52e00-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="52e00-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="52e00-109">Reason for change</span></span>

<span data-ttu-id="52e00-110">Bootstrap 4 byl propuštěn během ASP.NET Core 3.0 časový rámec.</span><span class="sxs-lookup"><span data-stu-id="52e00-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="52e00-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="52e00-111">Recommended action</span></span>

<span data-ttu-id="52e00-112">Tato změna vás ovlivní, pokud použijete výchozí unové zobrazení identity a přičtete ho, `Startup.ConfigureServices` jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="52e00-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="52e00-113">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="52e00-113">Take one of the following actions:</span></span>

- <span data-ttu-id="52e00-114">Migrujte aplikaci a použijte Bootstrap 4 pomocí průvodce [migrací](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="52e00-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="52e00-115">Aktualizace `Startup.ConfigureServices` pro vynucení použití Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="52e00-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="52e00-116">Například:</span><span class="sxs-lookup"><span data-stu-id="52e00-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="52e00-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="52e00-117">Category</span></span>

<span data-ttu-id="52e00-118">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="52e00-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52e00-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="52e00-119">Affected APIs</span></span>

<span data-ttu-id="52e00-120">Žádný</span><span class="sxs-lookup"><span data-stu-id="52e00-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
