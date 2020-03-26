---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291639"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure: Odebrané balíčky integrace Azure s předponou Microsoftu

Následující `Microsoft.*` balíčky, které poskytují integraci mezi ASP.NET Core a Sady Azure SDK nejsou součástí ASP.NET Core 5.0:

* [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), který integruje [Azure Key Vault](/azure/key-vault/) do [konfiguračního systému](/aspnet/core/fundamentals/configuration/).
* [Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), který integruje Azure Key Vault do [ASP.NET systému core data protection](/aspnet/core/security/data-protection/introduction).
* [Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), který integruje [Azure Blob Storage](/azure/storage/blobs/) do systému ASP.NET Core Data Protection.

Diskuse o tomto problému naleznete [v tématu dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Zavedená verze

5.0 Náhled 1

#### <a name="old-behavior"></a>Staré chování

Balíčky `Microsoft.*` integrované služby Azure s konfigurace a ochrany dat API.

#### <a name="new-behavior"></a>Nové chování

Nové `Azure.*` balíčky integrují služby Azure s hraničními urnami konfigurace a ochrany dat.

#### <a name="reason-for-change"></a>Důvod změny

Změna byla provedena, `Microsoft.*` protože balíčky byly:

* Použití zastaralých verzí sady Azure SDK. Jednoduché aktualizace nebyly možné, protože nové verze sady Azure SDK zahrnovaly narušující změny.
* Svázaný s plánem vydání .NET Core. Převod vlastnictví balíčků do týmu sady Azure SDK umožňuje aktualizace balíčků při aktualizaci sady Azure SDK.

#### <a name="recommended-action"></a>Doporučená akce

V ASP.NET core 2.1 nebo novější `Microsoft.*` projekty, nahradit staré nové `Azure.*` balíčky.

| Staré | Nová |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure.AspNetCore.DataProtection.Keys](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure.AspNetCore.DataProtection.Objekty BLOB](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.Configuration.Secrets](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

Nové balíčky používají novou verzi sady Azure SDK, která zahrnuje narušující změny. Obecné vzory použití jsou beze změny. Některá přetížení a možnosti se mohou lišit přizpůsobit změnám v podkladových azure sdk api.

Staré balíčky budou:

* Být podporovány ASP.NET core tým po dobu životnosti .NET Core 2.1 a 3.1.
* Nesmí být zahrnuty v rozhraní .NET 5.

Při upgradu projektu na .NET 5, přechod na `Azure.*` balíčky zachovat podporu.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
