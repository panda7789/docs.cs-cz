---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901594"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Ochrana dat: DataProtection. AzureStorage používá nová rozhraní API Azure Storage.

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> závisí na [Azure Storagech knihovnách](https://github.com/Azure/azure-storage-net). Tyto knihovny přejmenovaly jejich sestavení, balíčky a obory názvů. Počínaje ASP.NET Core 3,0 `Microsoft.AspNetCore.DataProtection.AzureStorage` používá nová `Microsoft.Azure.Storage.`ová a předem vydaná rozhraní API a balíčky.

Pro otázky týkající se rozhraní Azure Storage API použijte <https://github.com/Azure/azure-storage-net>. Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Balíček odkazoval na `WindowsAzure.Storage` balíček NuGet.

#### <a name="new-behavior"></a>Nové chování

Balíček odkazuje na balíček NuGet `Microsoft.Azure.Storage.Blob`.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna umožňuje `Microsoft.AspNetCore.DataProtection.AzureStorage` migrovat na Doporučené balíčky Azure Storage.

#### <a name="recommended-action"></a>Doporučená akce

Pokud stále potřebujete používat starší rozhraní Azure Storage API s ASP.NET Core 3,0, přidejte přímou závislost do balíčku [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Tento balíček se dá nainstalovat spolu s novými rozhraními API `Microsoft.Azure.Storage`.

V mnoha případech upgrade zahrnuje pouze změnu příkazů `using` pro použití nových oborů názvů:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
