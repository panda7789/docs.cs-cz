---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394301"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="028b1-101">Ochrana dat: DataProtection. AzureStorage používá nová rozhraní API Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="028b1-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="028b1-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> závisí na [Azure Storagech knihovnách](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="028b1-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="028b1-103">Tyto knihovny přejmenovaly jejich sestavení, balíčky a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="028b1-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="028b1-104">Počínaje ASP.NET Core 3,0 `Microsoft.AspNetCore.DataProtection.AzureStorage` používá nová @no__t -1-předem opravená rozhraní API a balíčky.</span><span class="sxs-lookup"><span data-stu-id="028b1-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="028b1-105">Pro otázky týkající se rozhraní Azure Storage API použijte <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="028b1-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="028b1-106">Diskuzi o tomto problému najdete v tématu [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="028b1-106">For discussion on this issue, see [aspnet/AspNetCore#8472](https://github.com/aspnet/AspNetCore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="028b1-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="028b1-107">Version introduced</span></span>

<span data-ttu-id="028b1-108">3.0</span><span class="sxs-lookup"><span data-stu-id="028b1-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="028b1-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="028b1-109">Old behavior</span></span>

<span data-ttu-id="028b1-110">Balíček odkazoval na balíček NuGet `WindowsAzure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="028b1-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="028b1-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="028b1-111">New behavior</span></span>

<span data-ttu-id="028b1-112">Balíček odkazuje na balíček NuGet `Microsoft.Azure.Storage.Blob`.</span><span class="sxs-lookup"><span data-stu-id="028b1-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="028b1-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="028b1-113">Reason for change</span></span>

<span data-ttu-id="028b1-114">Tato změna umožňuje `Microsoft.AspNetCore.DataProtection.AzureStorage` migrovat na Doporučené balíčky Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="028b1-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="028b1-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="028b1-115">Recommended action</span></span>

<span data-ttu-id="028b1-116">Pokud stále potřebujete používat starší rozhraní Azure Storage API s ASP.NET Core 3,0, přidejte přímou závislost do balíčku [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) .</span><span class="sxs-lookup"><span data-stu-id="028b1-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="028b1-117">Tento balíček se dá nainstalovat spolu s novými rozhraními API `Microsoft.Azure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="028b1-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="028b1-118">V mnoha případech upgrade zahrnuje pouze změnu příkazů `using` tak, aby používaly nové obory názvů:</span><span class="sxs-lookup"><span data-stu-id="028b1-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="028b1-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="028b1-119">Category</span></span>

<span data-ttu-id="028b1-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="028b1-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="028b1-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="028b1-121">Affected APIs</span></span>

<span data-ttu-id="028b1-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="028b1-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
