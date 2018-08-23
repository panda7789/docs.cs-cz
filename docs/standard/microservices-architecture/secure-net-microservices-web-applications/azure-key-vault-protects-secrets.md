---
title: Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 84e016e4620b73444f800b02076489012ea5e844
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752144"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="8a882-103">Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci</span><span class="sxs-lookup"><span data-stu-id="8a882-103">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="8a882-104">Tajné kódy uložené jako proměnné prostředí nebo neukládá nástroj tajný klíč správce jsou stále místně uložená a nešifrované na počítači.</span><span class="sxs-lookup"><span data-stu-id="8a882-104">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="8a882-105">Je bezpečnější možnost pro ukládání tajných kódů [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), která poskytuje zabezpečené a centrální umístění pro ukládání klíčů a tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="8a882-105">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="8a882-106">Balíček Microsoft.Extensions.Configuration.AzureKeyVault umožňuje aplikaci ASP.NET Core číst informace o konfiguraci ze služby Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="8a882-106">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="8a882-107">Pokud chcete začít používat tajné kódy ze služby Azure Key Vault, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="8a882-107">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="8a882-108">Nejprve registrovat aplikaci jako aplikaci Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8a882-108">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="8a882-109">(Přístup k trezorům klíčů se spravuje přes Azure AD). To můžete udělat přes portál pro správu Azure.</span><span class="sxs-lookup"><span data-stu-id="8a882-109">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="8a882-110">Případně, pokud chcete, aby aplikace k ověřování pomocí certifikátu místo tajného klíče klienta nebo heslo, můžete použít [New-AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) rutiny Powershellu.</span><span class="sxs-lookup"><span data-stu-id="8a882-110">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="8a882-111">Certifikát, který zaregistrujete pomocí služby Azure Key Vault potřebuje pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="8a882-111">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="8a882-112">(Aplikace bude používat privátní klíč).</span><span class="sxs-lookup"><span data-stu-id="8a882-112">(Your application will use the private key.)</span></span>

<span data-ttu-id="8a882-113">Za druhé poskytují přístup zaregistrovanou aplikaci do služby key vault tak, že vytvoříte nový instanční objekt.</span><span class="sxs-lookup"><span data-stu-id="8a882-113">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="8a882-114">Můžete provést pomocí následujících příkazů Powershellu:</span><span class="sxs-lookup"><span data-stu-id="8a882-114">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="8a882-115">Třetí volání metody rozšíření IConfigurationBuilder.AddAzureKeyVault při vytváření IConfigurationRoot instance zahrnují služby key vault jako zdroj konfigurace ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8a882-115">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="8a882-116">Všimněte si, že volání AddAzureKeyVault bude vyžadovat ID aplikace, který byl zaregistrován a poskytnut přístup k trezoru klíčů v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="8a882-116">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="8a882-117">V současné době .NET Standard a .NET Core podporují získávání informací o konfiguraci ze služby Azure Key Vault pomocí ID klienta a tajný kód klienta.</span><span class="sxs-lookup"><span data-stu-id="8a882-117">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="8a882-118">Aplikace rozhraní .NET framework můžete použít přetížení IConfigurationBuilder.AddAzureKeyVault, která přebírá certifikátu místo tajného klíče klienta.</span><span class="sxs-lookup"><span data-stu-id="8a882-118">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="8a882-119">V době psaní tohoto textu je práce [probíhá](https://github.com/aspnet/Configuration/issues/605) chcete zpřístupnit tento přetížení v .NET Standard a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a882-119">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="8a882-120">Dokud AddAzureKeyVault přetížení, která přijímá certifikát je k dispozici, ASP.NET Core aplikace můžou k služby Azure Key Vault s ověřováním na základě certifikátů explicitně vytvořením objektu KeyVaultClient, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8a882-120">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="8a882-121">V tomto příkladu obsahuje volání AddAzureKeyVault na konci registraci zprostředkovatele konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8a882-121">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="8a882-122">Je osvědčeným postupem je registrace služby Azure Key Vault jako poslední poskytovatele konfigurace tak, aby měla možnost přepsat hodnoty konfigurace z předchozích poskytovatelů a tak, aby žádné hodnoty konfigurace z jiných zdrojů přepíšou z trezoru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a882-122">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8a882-123">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8a882-123">Additional resources</span></span>

-   <span data-ttu-id="8a882-124">**Použití Azure Key Vault k ochraně tajných klíčů aplikací**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="8a882-124">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="8a882-125">**Bezpečné ukládání tajných kódů aplikace během vývoje.**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="8a882-125">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="8a882-126">**Konfigurace ochrany dat**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="8a882-126">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="8a882-127">**Správa klíčů a doba života**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="8a882-127">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="8a882-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="8a882-128">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="8a882-129">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="8a882-129">GitHub repo.</span></span>
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="8a882-130">[Předchozí](developer-app-secrets-storage.md)
[další](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="8a882-130">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
