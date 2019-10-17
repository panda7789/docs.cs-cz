---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394340"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="20348-101">Hostování: typy IHostingEnvironment a IApplicationLifetime označené jako zastaralé a nahrazené</span><span class="sxs-lookup"><span data-stu-id="20348-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="20348-102">Byly zavedeny nové typy, které nahradí existující typy `IHostingEnvironment` a `IApplicationLifetime`.</span><span class="sxs-lookup"><span data-stu-id="20348-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="20348-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="20348-103">Version introduced</span></span>

<span data-ttu-id="20348-104">3.0</span><span class="sxs-lookup"><span data-stu-id="20348-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="20348-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="20348-105">Old behavior</span></span>

<span data-ttu-id="20348-106">Existují dva různé typy `IHostingEnvironment` a `IApplicationLifetime` z `Microsoft.Extensions.Hosting` a `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="20348-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="20348-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="20348-107">New behavior</span></span>

<span data-ttu-id="20348-108">Staré typy byly označeny jako zastaralé a nahrazeny novými typy.</span><span class="sxs-lookup"><span data-stu-id="20348-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="20348-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="20348-109">Reason for change</span></span>

<span data-ttu-id="20348-110">Pokud byla `Microsoft.Extensions.Hosting` představena v ASP.NET Core 2,1, některé typy jako `IHostingEnvironment` a `IApplicationLifetime` byly zkopírovány z `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="20348-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="20348-111">Některé změny ASP.NET Core 3,0 způsobí, že aplikace budou zahrnovat obory názvů `Microsoft.Extensions.Hosting` i `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="20348-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="20348-112">Jakékoli použití těchto duplicitních typů způsobí chybu kompilátoru "dvojznačný odkaz" při odkazování na oba obory názvů.</span><span class="sxs-lookup"><span data-stu-id="20348-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="20348-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="20348-113">Recommended action</span></span>

<span data-ttu-id="20348-114">Nově zavedené typy nahradily všechna použití starého typu, jak je uvedeno níže:</span><span class="sxs-lookup"><span data-stu-id="20348-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="20348-115">**Zastaralé typy (upozornění):**</span><span class="sxs-lookup"><span data-stu-id="20348-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="20348-116">**Nové typy:**</span><span class="sxs-lookup"><span data-stu-id="20348-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="20348-117">Nové metody rozšíření `IHostEnvironment` `IsDevelopment` a `IsProduction` jsou v oboru názvů `Microsoft.Extensions.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="20348-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="20348-118">Tento obor názvů může být potřeba přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="20348-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="20348-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="20348-119">Category</span></span>

<span data-ttu-id="20348-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="20348-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="20348-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="20348-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
