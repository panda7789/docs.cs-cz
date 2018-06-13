---
title: Použití Azure Key Vault k ochraně tajných klíčů v době výroby
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití Azure Key Vault k ochraně tajných klíčů v době výroby
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5ad5686909c29eba5916cbcc4b7115a16108a004
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580400"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Použití Azure Key Vault k ochraně tajných klíčů v době výroby

Tajné klíče uložené jako proměnné prostředí nebo uložené nástrojem pro tajný klíč Manager jsou stále místně uložených a bez šifrování v počítači. Bezpečnější možnost pro ukládání tajné klíče je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), která poskytuje zabezpečené, centrální umístění pro ukládání klíčů a tajných klíčů.

Balíček Microsoft.Extensions.Configuration.AzureKeyVault umožňuje aplikaci ASP.NET Core číst informace o konfiguraci z Azure Key Vault. Chcete-li začít používat tajné klíče z Azure Key Vault, postupujte takto:

Nejprve zaregistrujte aplikaci jako aplikaci Azure AD. (Přístup k trezorů klíčů je spravované službou Azure AD). To lze provést prostřednictvím portálu správy Azure.

Případně, pokud chcete, aby aplikace k ověření pomocí certifikátu, místo hesla nebo klienta tajný klíč, můžete použít [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) rutiny prostředí PowerShell. Certifikát, který zaregistrujete s Azure Key Vault musí pouze veřejný klíč. (Vaše aplikace bude používat privátní klíč.)

Druhý udělte přístup zaregistrovanou aplikaci do trezoru klíčů vytvořením nového objektu služby. To provedete pomocí následujících příkazů prostředí PowerShell:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Voláním metody rozšíření IConfigurationBuilder.AddAzureKeyVault při vytváření IConfigurationRoot instance třetí, obsahovat trezoru klíčů jako zdroj konfigurace v aplikaci. Všimněte si, že volání AddAzureKeyVault bude vyžadovat ID aplikace, který byl zaregistrován a poskytnut přístup k trezoru klíčů v předchozích krocích.

  V současné době .NET Standard a .NET Core podporují získávání informace o konfiguraci ze Azure Key Vault pomocí ID klienta a tajný klíč klienta. Aplikace rozhraní .NET framework, můžete použít přetížení IConfigurationBuilder.AddAzureKeyVault, která přebírá certifikát místo tajný klíč klienta. Době psaní tohoto textu je pracovní [v průběhu](https://github.com/aspnet/Configuration/issues/605) chcete zpřístupnit tento přetížení v rozhraní .NET Standard a .NET Core. Dokud AddAzureKeyVault přetížení, které přijímá certifikát je k dispozici aplikace ASP.NET Core můžete přístup k Azure Key Vault s ověřováním na základě certifikátu explicitně vytvořením objekt KeyVaultClient, jak je znázorněno v následujícím příkladu:

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

V tomto příkladu obsahuje volání AddAzureKeyVault na konci registraci zprostředkovatele konfigurace. Je osvědčeným postupem zaregistrovat Azure Key Vault jako poslední poskytovatel konfigurace tak, aby měl příležitost k přepsání hodnoty konfigurace z předchozí zprostředkovatele, a tak, aby žádné hodnoty konfigurace z jiných zdrojů přepíšou z trezoru klíčů.

## <a name="additional-resources"></a>Další zdroje

-   **Použití Azure Key Vault a k ochraně tajných klíčů aplikace**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Bezpečné úložiště tajné klíče aplikace během vývoje**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Konfigurace ochrany dat**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Klíč správy a dobu života**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data protection výchozí nastavení*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** Úložiště GitHub.
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Předchozí] (vývojáře app-tajné klíče storage.md) [Další] (.. / takeaways.md klíč)
