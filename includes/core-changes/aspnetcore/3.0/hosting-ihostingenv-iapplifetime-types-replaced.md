---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394340"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="d710b-101">Hosting: Typy IHostingEnvironment a IApplicationLifetime označené jako zastaralé a nahrazené</span><span class="sxs-lookup"><span data-stu-id="d710b-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="d710b-102">Byly zavedeny nové typy, `IHostingEnvironment` které `IApplicationLifetime` nahrazují stávající a typy.</span><span class="sxs-lookup"><span data-stu-id="d710b-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d710b-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="d710b-103">Version introduced</span></span>

<span data-ttu-id="d710b-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d710b-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d710b-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="d710b-105">Old behavior</span></span>

<span data-ttu-id="d710b-106">Tam byly `IHostingEnvironment` dva `IApplicationLifetime` různé `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting`a typy od a .</span><span class="sxs-lookup"><span data-stu-id="d710b-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d710b-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="d710b-107">New behavior</span></span>

<span data-ttu-id="d710b-108">Staré typy byly označeny jako zastaralé a nahrazeny novými typy.</span><span class="sxs-lookup"><span data-stu-id="d710b-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d710b-109">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d710b-109">Reason for change</span></span>

<span data-ttu-id="d710b-110">Když `Microsoft.Extensions.Hosting` byl zaveden v ASP.NET Core 2.1, některé typy jako `IHostingEnvironment` a `IApplicationLifetime` byly zkopírovány z `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="d710b-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="d710b-111">Některé změny ASP.NET Core 3.0 způsobí, že aplikace budou obsahovat obory `Microsoft.Extensions.Hosting` názvů i `Microsoft.AspNetCore.Hosting` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="d710b-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="d710b-112">Jakékoli použití těchto duplicitních typů způsobí chybu kompilátoru "nejednoznačný odkaz", když jsou odkazovány na oba obory názvů.</span><span class="sxs-lookup"><span data-stu-id="d710b-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d710b-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d710b-113">Recommended action</span></span>

<span data-ttu-id="d710b-114">Všechna použití starých typů byla nahrazena nově zavedenými typy, jak je uvedeno níže:</span><span class="sxs-lookup"><span data-stu-id="d710b-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="d710b-115">**Zastaralé typy (upozornění):**</span><span class="sxs-lookup"><span data-stu-id="d710b-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="d710b-116">**Nové typy:**</span><span class="sxs-lookup"><span data-stu-id="d710b-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="d710b-117">Nové `IHostEnvironment` `IsDevelopment` a `IsProduction` rozšiřující metody `Microsoft.Extensions.Hosting` jsou v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d710b-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="d710b-118">Tento obor názvů může být nutné přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="d710b-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="d710b-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d710b-119">Category</span></span>

<span data-ttu-id="d710b-120">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d710b-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d710b-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d710b-121">Affected APIs</span></span>

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
