---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394345"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="b9a53-101">Identita: výchozí počáteční verze uživatelského rozhraní se změnila.</span><span class="sxs-lookup"><span data-stu-id="b9a53-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="b9a53-102">Počínaje ASP.NET Core 3,0 se v uživatelském rozhraní identity standardně používá verze 4 Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="b9a53-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b9a53-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b9a53-103">Version introduced</span></span>

<span data-ttu-id="b9a53-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b9a53-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b9a53-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="b9a53-105">Old behavior</span></span>

<span data-ttu-id="b9a53-106">Volání metody `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` bylo stejné jako `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`.</span><span class="sxs-lookup"><span data-stu-id="b9a53-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b9a53-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="b9a53-107">New behavior</span></span>

<span data-ttu-id="b9a53-108">Volání metody `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` je stejné jako `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`.</span><span class="sxs-lookup"><span data-stu-id="b9a53-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b9a53-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="b9a53-109">Reason for change</span></span>

<span data-ttu-id="b9a53-110">Služba Bootstrap 4 byla vydána během období ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b9a53-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9a53-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b9a53-111">Recommended action</span></span>

<span data-ttu-id="b9a53-112">Tuto změnu ovlivníte, pokud použijete výchozí uživatelské rozhraní identity a přidáte ho do `Startup.ConfigureServices`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b9a53-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="b9a53-113">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b9a53-113">Take one of the following actions:</span></span>

- <span data-ttu-id="b9a53-114">Migrujte aplikaci tak, aby používala Bootstrap 4 pomocí jejich [Průvodce migrací](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="b9a53-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="b9a53-115">Aktualizujte `Startup.ConfigureServices`, aby se vynutilo použití spouštěcí rutiny 3.</span><span class="sxs-lookup"><span data-stu-id="b9a53-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="b9a53-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b9a53-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="b9a53-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b9a53-117">Category</span></span>

<span data-ttu-id="b9a53-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b9a53-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9a53-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b9a53-119">Affected APIs</span></span>

<span data-ttu-id="b9a53-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="b9a53-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
