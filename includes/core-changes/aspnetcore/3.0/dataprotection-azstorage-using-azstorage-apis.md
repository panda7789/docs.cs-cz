---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394301"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="4c577-101">Ochrana dat: DataProtection. AzureStorage používá nová rozhraní API Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="4c577-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="4c577-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> závisí na [Azure Storagech knihovnách](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="4c577-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="4c577-103">Tyto knihovny přejmenovaly jejich sestavení, balíčky a obory názvů.</span><span class="sxs-lookup"><span data-stu-id="4c577-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="4c577-104">Počínaje ASP.NET Core 3,0 `Microsoft.AspNetCore.DataProtection.AzureStorage` používá nová `Microsoft.Azure.Storage.`ová a předem vydaná rozhraní API a balíčky.</span><span class="sxs-lookup"><span data-stu-id="4c577-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="4c577-105">Pro otázky týkající se rozhraní Azure Storage API použijte <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="4c577-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="4c577-106">Diskuzi o tomto problému najdete v tématu [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="4c577-106">For discussion on this issue, see [aspnet/AspNetCore#8472](https://github.com/aspnet/AspNetCore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4c577-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4c577-107">Version introduced</span></span>

<span data-ttu-id="4c577-108">3,0</span><span class="sxs-lookup"><span data-stu-id="4c577-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4c577-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="4c577-109">Old behavior</span></span>

<span data-ttu-id="4c577-110">Balíček odkazoval na `WindowsAzure.Storage` balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c577-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4c577-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="4c577-111">New behavior</span></span>

<span data-ttu-id="4c577-112">Balíček odkazuje na balíček NuGet `Microsoft.Azure.Storage.Blob`.</span><span class="sxs-lookup"><span data-stu-id="4c577-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4c577-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="4c577-113">Reason for change</span></span>

<span data-ttu-id="4c577-114">Tato změna umožňuje `Microsoft.AspNetCore.DataProtection.AzureStorage` migrovat na Doporučené balíčky Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="4c577-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c577-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4c577-115">Recommended action</span></span>

<span data-ttu-id="4c577-116">Pokud stále potřebujete používat starší rozhraní Azure Storage API s ASP.NET Core 3,0, přidejte přímou závislost do balíčku [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) .</span><span class="sxs-lookup"><span data-stu-id="4c577-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="4c577-117">Tento balíček se dá nainstalovat spolu s novými rozhraními API `Microsoft.Azure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="4c577-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="4c577-118">V mnoha případech upgrade zahrnuje pouze změnu příkazů `using` pro použití nových oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="4c577-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="4c577-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4c577-119">Category</span></span>

<span data-ttu-id="4c577-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4c577-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c577-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4c577-121">Affected APIs</span></span>

<span data-ttu-id="4c577-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c577-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
