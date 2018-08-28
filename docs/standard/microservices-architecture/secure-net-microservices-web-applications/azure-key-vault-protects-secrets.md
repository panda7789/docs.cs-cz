---
title: Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 84e016e4620b73444f800b02076489012ea5e844
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001437"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci

Tajné kódy uložené jako proměnné prostředí nebo neukládá nástroj tajný klíč správce jsou stále místně uložená a nešifrované na počítači. Je bezpečnější možnost pro ukládání tajných kódů [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), která poskytuje zabezpečené a centrální umístění pro ukládání klíčů a tajných kódů.

Balíček Microsoft.Extensions.Configuration.AzureKeyVault umožňuje aplikaci ASP.NET Core číst informace o konfiguraci ze služby Azure Key Vault. Pokud chcete začít používat tajné kódy ze služby Azure Key Vault, postupujte takto:

Nejprve registrovat aplikaci jako aplikaci Azure AD. (Přístup k trezorům klíčů se spravuje přes Azure AD). To můžete udělat přes portál pro správu Azure.

Případně, pokud chcete, aby aplikace k ověřování pomocí certifikátu místo tajného klíče klienta nebo heslo, můžete použít [New-AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) rutiny Powershellu. Certifikát, který zaregistrujete pomocí služby Azure Key Vault potřebuje pouze veřejný klíč. (Aplikace bude používat privátní klíč).

Za druhé poskytují přístup zaregistrovanou aplikaci do služby key vault tak, že vytvoříte nový instanční objekt. Můžete provést pomocí následujících příkazů Powershellu:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Třetí volání metody rozšíření IConfigurationBuilder.AddAzureKeyVault při vytváření IConfigurationRoot instance zahrnují služby key vault jako zdroj konfigurace ve vaší aplikaci. Všimněte si, že volání AddAzureKeyVault bude vyžadovat ID aplikace, který byl zaregistrován a poskytnut přístup k trezoru klíčů v předchozích krocích.

  V současné době .NET Standard a .NET Core podporují získávání informací o konfiguraci ze služby Azure Key Vault pomocí ID klienta a tajný kód klienta. Aplikace rozhraní .NET framework můžete použít přetížení IConfigurationBuilder.AddAzureKeyVault, která přebírá certifikátu místo tajného klíče klienta. V době psaní tohoto textu je práce [probíhá](https://github.com/aspnet/Configuration/issues/605) chcete zpřístupnit tento přetížení v .NET Standard a .NET Core. Dokud AddAzureKeyVault přetížení, která přijímá certifikát je k dispozici, ASP.NET Core aplikace můžou k služby Azure Key Vault s ověřováním na základě certifikátů explicitně vytvořením objektu KeyVaultClient, jak je znázorněno v následujícím příkladu:

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

V tomto příkladu obsahuje volání AddAzureKeyVault na konci registraci zprostředkovatele konfigurace. Je osvědčeným postupem je registrace služby Azure Key Vault jako poslední poskytovatele konfigurace tak, aby měla možnost přepsat hodnoty konfigurace z předchozích poskytovatelů a tak, aby žádné hodnoty konfigurace z jiných zdrojů přepíšou z trezoru klíčů.

## <a name="additional-resources"></a>Další zdroje

-   **Použití Azure Key Vault k ochraně tajných klíčů aplikací**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Bezpečné ukládání tajných kódů aplikace během vývoje.**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Konfigurace ochrany dat**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Správa klíčů a doba života**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** Úložiště GitHub.
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Předchozí](developer-app-secrets-storage.md)
[další](../key-takeaways.md)
