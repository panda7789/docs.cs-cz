---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416273"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure: odebraly se balíčky Microsoft infixních integrací Azure.

Následující `Microsoft.*` balíčky, které poskytují integraci mezi ASP.NET Core a sady Azure SDK, nejsou zahrnuté v ASP.NET Core 5,0:

* [Microsoft.Extensions.Configuration. AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), která integruje [Azure Key Vault](/azure/key-vault/) do [konfiguračního systému](/aspnet/core/fundamentals/configuration/).
* [Microsoft. AspNetCore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), který integruje Azure Key Vault do [ASP.NET Core systému ochrany dat](/aspnet/core/security/data-protection/introduction).
* [Microsoft. AspNetCore. DataProtection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), který integruje [Azure Blob Storage](/azure/storage/blobs/) do ASP.NET Core systému ochrany dat.

Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 1

#### <a name="old-behavior"></a>Staré chování

`Microsoft.*`Integrované služby Azure pro balíčky s rozhraními API pro konfiguraci a ochranu dat.

#### <a name="new-behavior"></a>Nové chování

Nové `Azure.*` balíčky integrují služby Azure s rozhraními API pro konfiguraci a ochranu dat.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna byla provedena, protože `Microsoft.*` balíčky byly:

* Pomocí zastaralých verzí sady Azure SDK. Jednoduché aktualizace nebyly možné, protože nové verze sady Azure SDK zahrnovaly zásadní změny.
* Je vázáno na plán verze .NET Core. Přenos vlastnictví balíčků do týmu Azure SDK umožňuje aktualizace balíčku, protože se aktualizuje sada Azure SDK.

#### <a name="recommended-action"></a>Doporučená akce

V ASP.NET Core 2,1 nebo novějších projektech nahraďte staré `Microsoft.*` novými `Azure.*` balíčky.

| Původním | Nová |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure. Extensions. AspNetCore. DataProtection. Keys](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure. Extensions. AspNetCore. DataProtection. BLOBs](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.AspNetCore.Configuration. Záleží](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

Nové balíčky používají novou verzi sady Azure SDK, která obsahuje zásadní změny. Obecné vzorce použití se nezměnily. Některá přetížení a možnosti se mohou lišit v tom, že se změny v podkladových rozhraních API sady Azure SDK můžou přizpůsobit.

Staré balíčky budou:

* Být podporován ASP.NET Core týmem po dobu života .NET Core 2,1 a 3,1.
* Není součástí rozhraní .NET 5.

Při upgradu projektu na rozhraní .NET 5 se přechodem do `Azure.*` balíčků zachová podpora.

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
