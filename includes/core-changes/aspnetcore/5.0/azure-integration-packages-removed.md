---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291639"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="cc544-101">Azure: Odebrané balíčky integrace Azure s předponou Microsoftu</span><span class="sxs-lookup"><span data-stu-id="cc544-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="cc544-102">Následující `Microsoft.*` balíčky, které poskytují integraci mezi ASP.NET Core a Sady Azure SDK nejsou součástí ASP.NET Core 5.0:</span><span class="sxs-lookup"><span data-stu-id="cc544-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="cc544-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), který integruje [Azure Key Vault](/azure/key-vault/) do [konfiguračního systému](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="cc544-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="cc544-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), který integruje Azure Key Vault do [ASP.NET systému core data protection](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="cc544-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="cc544-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), který integruje [Azure Blob Storage](/azure/storage/blobs/) do systému ASP.NET Core Data Protection.</span><span class="sxs-lookup"><span data-stu-id="cc544-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="cc544-106">Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="cc544-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cc544-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="cc544-107">Version introduced</span></span>

<span data-ttu-id="cc544-108">5.0 Náhled 1</span><span class="sxs-lookup"><span data-stu-id="cc544-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cc544-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="cc544-109">Old behavior</span></span>

<span data-ttu-id="cc544-110">Balíčky `Microsoft.*` integrované služby Azure s konfigurace a ochrany dat API.</span><span class="sxs-lookup"><span data-stu-id="cc544-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cc544-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="cc544-111">New behavior</span></span>

<span data-ttu-id="cc544-112">Nové `Azure.*` balíčky integrují služby Azure s hraničními urnami konfigurace a ochrany dat.</span><span class="sxs-lookup"><span data-stu-id="cc544-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cc544-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="cc544-113">Reason for change</span></span>

<span data-ttu-id="cc544-114">Změna byla provedena, `Microsoft.*` protože balíčky byly:</span><span class="sxs-lookup"><span data-stu-id="cc544-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="cc544-115">Použití zastaralých verzí sady Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="cc544-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="cc544-116">Jednoduché aktualizace nebyly možné, protože nové verze sady Azure SDK zahrnovaly narušující změny.</span><span class="sxs-lookup"><span data-stu-id="cc544-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="cc544-117">Svázaný s plánem vydání .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc544-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="cc544-118">Převod vlastnictví balíčků do týmu sady Azure SDK umožňuje aktualizace balíčků při aktualizaci sady Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="cc544-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cc544-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="cc544-119">Recommended action</span></span>

<span data-ttu-id="cc544-120">V ASP.NET core 2.1 nebo novější `Microsoft.*` projekty, nahradit staré nové `Azure.*` balíčky.</span><span class="sxs-lookup"><span data-stu-id="cc544-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="cc544-121">Staré</span><span class="sxs-lookup"><span data-stu-id="cc544-121">Old</span></span> | <span data-ttu-id="cc544-122">Nová</span><span class="sxs-lookup"><span data-stu-id="cc544-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="cc544-123">Azure.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="cc544-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="cc544-124">Azure.AspNetCore.DataProtection.Objekty BLOB</span><span class="sxs-lookup"><span data-stu-id="cc544-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="cc544-125">Azure.Extensions.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="cc544-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="cc544-126">Nové balíčky používají novou verzi sady Azure SDK, která zahrnuje narušující změny.</span><span class="sxs-lookup"><span data-stu-id="cc544-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="cc544-127">Obecné vzory použití jsou beze změny.</span><span class="sxs-lookup"><span data-stu-id="cc544-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="cc544-128">Některá přetížení a možnosti se mohou lišit přizpůsobit změnám v podkladových azure sdk api.</span><span class="sxs-lookup"><span data-stu-id="cc544-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="cc544-129">Staré balíčky budou:</span><span class="sxs-lookup"><span data-stu-id="cc544-129">The old packages will:</span></span>

* <span data-ttu-id="cc544-130">Být podporovány ASP.NET core tým po dobu životnosti .NET Core 2.1 a 3.1.</span><span class="sxs-lookup"><span data-stu-id="cc544-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="cc544-131">Nesmí být zahrnuty v rozhraní .NET 5.</span><span class="sxs-lookup"><span data-stu-id="cc544-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="cc544-132">Při upgradu projektu na .NET 5, přechod na `Azure.*` balíčky zachovat podporu.</span><span class="sxs-lookup"><span data-stu-id="cc544-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="cc544-133">Kategorie</span><span class="sxs-lookup"><span data-stu-id="cc544-133">Category</span></span>

<span data-ttu-id="cc544-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cc544-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cc544-135">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cc544-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
