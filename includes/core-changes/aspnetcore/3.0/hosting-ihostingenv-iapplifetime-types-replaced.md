---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394340"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hostování: typy IHostingEnvironment a IApplicationLifetime označené jako zastaralé a nahrazené

Byly zavedeny nové typy, které nahradí existující typy `IHostingEnvironment` a `IApplicationLifetime`.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Existují dva různé typy `IHostingEnvironment` a `IApplicationLifetime` z `Microsoft.Extensions.Hosting` a `Microsoft.AspNetCore.Hosting`.

#### <a name="new-behavior"></a>Nové chování

Staré typy byly označeny jako zastaralé a nahrazeny novými typy.

#### <a name="reason-for-change"></a>Důvod změny

Pokud byla `Microsoft.Extensions.Hosting` představena v ASP.NET Core 2,1, některé typy jako `IHostingEnvironment` a `IApplicationLifetime` byly zkopírovány z `Microsoft.AspNetCore.Hosting`. Některé změny ASP.NET Core 3,0 způsobí, že aplikace budou zahrnovat obory názvů `Microsoft.Extensions.Hosting` i `Microsoft.AspNetCore.Hosting`. Jakékoli použití těchto duplicitních typů způsobí chybu kompilátoru "dvojznačný odkaz" při odkazování na oba obory názvů.

#### <a name="recommended-action"></a>Doporučená akce

Nově zavedené typy nahradily všechna použití starého typu, jak je uvedeno níže:

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

Nové metody rozšíření `IHostEnvironment` `IsDevelopment` a `IsProduction` jsou v oboru názvů `Microsoft.Extensions.Hosting`. Tento obor názvů může být potřeba přidat do projektu.

#### <a name="category"></a>Kategorie

ASP.NET Core

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
