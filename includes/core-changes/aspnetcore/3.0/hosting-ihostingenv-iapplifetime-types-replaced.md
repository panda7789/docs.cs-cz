---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394340"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hosting: Typy IHostingEnvironment a IApplicationLifetime označené jako zastaralé a nahrazené

Byly zavedeny nové typy, `IHostingEnvironment` které `IApplicationLifetime` nahrazují stávající a typy.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Tam byly `IHostingEnvironment` dva `IApplicationLifetime` různé `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting`a typy od a .

#### <a name="new-behavior"></a>Nové chování

Staré typy byly označeny jako zastaralé a nahrazeny novými typy.

#### <a name="reason-for-change"></a>Důvod změny

Když `Microsoft.Extensions.Hosting` byl zaveden v ASP.NET Core 2.1, některé typy jako `IHostingEnvironment` a `IApplicationLifetime` byly zkopírovány z `Microsoft.AspNetCore.Hosting`. Některé změny ASP.NET Core 3.0 způsobí, že aplikace budou obsahovat obory `Microsoft.Extensions.Hosting` názvů i `Microsoft.AspNetCore.Hosting` obory názvů. Jakékoli použití těchto duplicitních typů způsobí chybu kompilátoru "nejednoznačný odkaz", když jsou odkazovány na oba obory názvů.

#### <a name="recommended-action"></a>Doporučená akce

Všechna použití starých typů byla nahrazena nově zavedenými typy, jak je uvedeno níže:

**Zastaralé typy (upozornění):**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**Nové typy:**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

Nové `IHostEnvironment` `IsDevelopment` a `IsProduction` rozšiřující metody `Microsoft.Extensions.Hosting` jsou v oboru názvů. Tento obor názvů může být nutné přidat do projektu.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

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
