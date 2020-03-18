---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901594"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Ochrana dat: DataProtection.AzureStorage používá nová api úložiště Azure

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>závisí na [knihovnách Azure Storage](https://github.com/Azure/azure-storage-net). Tyto knihovny přejmenovaly svá sestavení, balíčky a obory názvů. Počínaje ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` `Microsoft.Azure.Storage.`používá nová předpona API a balíčky.

Máte-li dotazy týkající se <https://github.com/Azure/azure-storage-net>api úložiště Azure, použijte . Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Balíček odkazuje `WindowsAzure.Storage` na balíček NuGet.

#### <a name="new-behavior"></a>Nové chování

Balíček odkazuje `Microsoft.Azure.Storage.Blob` na balíček NuGet.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna `Microsoft.AspNetCore.DataProtection.AzureStorage` umožňuje migraci na doporučené balíčky azure storage.

#### <a name="recommended-action"></a>Doporučená akce

Pokud stále potřebujete používat starší rozhraní API úložiště Azure s ASP.NET Core 3.0, přidejte přímou závislost do balíčku [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/) Tento balíček lze nainstalovat `Microsoft.Azure.Storage` společně s novými api.

V mnoha případech upgrade zahrnuje `using` pouze změnu příkazů použít nové obory názvů:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
