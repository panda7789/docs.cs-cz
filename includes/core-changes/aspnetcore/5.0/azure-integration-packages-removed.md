---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416273"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="8120f-101">Azure: odebraly se balíčky Microsoft infixních integrací Azure.</span><span class="sxs-lookup"><span data-stu-id="8120f-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="8120f-102">Následující `Microsoft.*` balíčky, které poskytují integraci mezi ASP.NET Core a sady Azure SDK, nejsou zahrnuté v ASP.NET Core 5,0:</span><span class="sxs-lookup"><span data-stu-id="8120f-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="8120f-103">[Microsoft.Extensions.Configuration. AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), která integruje [Azure Key Vault](/azure/key-vault/) do [konfiguračního systému](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="8120f-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="8120f-104">[Microsoft. AspNetCore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), který integruje Azure Key Vault do [ASP.NET Core systému ochrany dat](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="8120f-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="8120f-105">[Microsoft. AspNetCore. DataProtection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), který integruje [Azure Blob Storage](/azure/storage/blobs/) do ASP.NET Core systému ochrany dat.</span><span class="sxs-lookup"><span data-stu-id="8120f-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="8120f-106">Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="8120f-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8120f-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8120f-107">Version introduced</span></span>

<span data-ttu-id="8120f-108">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8120f-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8120f-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="8120f-109">Old behavior</span></span>

<span data-ttu-id="8120f-110">`Microsoft.*`Integrované služby Azure pro balíčky s rozhraními API pro konfiguraci a ochranu dat.</span><span class="sxs-lookup"><span data-stu-id="8120f-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8120f-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="8120f-111">New behavior</span></span>

<span data-ttu-id="8120f-112">Nové `Azure.*` balíčky integrují služby Azure s rozhraními API pro konfiguraci a ochranu dat.</span><span class="sxs-lookup"><span data-stu-id="8120f-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8120f-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="8120f-113">Reason for change</span></span>

<span data-ttu-id="8120f-114">Tato změna byla provedena, protože `Microsoft.*` balíčky byly:</span><span class="sxs-lookup"><span data-stu-id="8120f-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="8120f-115">Pomocí zastaralých verzí sady Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="8120f-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="8120f-116">Jednoduché aktualizace nebyly možné, protože nové verze sady Azure SDK zahrnovaly zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="8120f-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="8120f-117">Je vázáno na plán verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8120f-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="8120f-118">Přenos vlastnictví balíčků do týmu Azure SDK umožňuje aktualizace balíčku, protože se aktualizuje sada Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="8120f-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8120f-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8120f-119">Recommended action</span></span>

<span data-ttu-id="8120f-120">V ASP.NET Core 2,1 nebo novějších projektech nahraďte staré `Microsoft.*` novými `Azure.*` balíčky.</span><span class="sxs-lookup"><span data-stu-id="8120f-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="8120f-121">Původním</span><span class="sxs-lookup"><span data-stu-id="8120f-121">Old</span></span> | <span data-ttu-id="8120f-122">Nová</span><span class="sxs-lookup"><span data-stu-id="8120f-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="8120f-123">Azure. Extensions. AspNetCore. DataProtection. Keys</span><span class="sxs-lookup"><span data-stu-id="8120f-123">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="8120f-124">Azure. Extensions. AspNetCore. DataProtection. BLOBs</span><span class="sxs-lookup"><span data-stu-id="8120f-124">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="8120f-125">Azure.Extensions.AspNetCore.Configuration. Záleží</span><span class="sxs-lookup"><span data-stu-id="8120f-125">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="8120f-126">Nové balíčky používají novou verzi sady Azure SDK, která obsahuje zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="8120f-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="8120f-127">Obecné vzorce použití se nezměnily.</span><span class="sxs-lookup"><span data-stu-id="8120f-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="8120f-128">Některá přetížení a možnosti se mohou lišit v tom, že se změny v podkladových rozhraních API sady Azure SDK můžou přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="8120f-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="8120f-129">Staré balíčky budou:</span><span class="sxs-lookup"><span data-stu-id="8120f-129">The old packages will:</span></span>

* <span data-ttu-id="8120f-130">Být podporován ASP.NET Core týmem po dobu života .NET Core 2,1 a 3,1.</span><span class="sxs-lookup"><span data-stu-id="8120f-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="8120f-131">Není součástí rozhraní .NET 5.</span><span class="sxs-lookup"><span data-stu-id="8120f-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="8120f-132">Při upgradu projektu na rozhraní .NET 5 se přechodem do `Azure.*` balíčků zachová podpora.</span><span class="sxs-lookup"><span data-stu-id="8120f-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="8120f-133">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8120f-133">Category</span></span>

<span data-ttu-id="8120f-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8120f-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8120f-135">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8120f-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
