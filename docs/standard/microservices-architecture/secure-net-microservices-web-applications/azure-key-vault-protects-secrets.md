---
title: "Použití Azure Key Vault k ochraně tajných klíčů v době výroby"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití Azure Key Vault k ochraně tajných klíčů v době výroby"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7f922997e8d0c63e206cd68f4efda14985c86b72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="cc8fc-104">Použití Azure Key Vault k ochraně tajných klíčů v době výroby</span><span class="sxs-lookup"><span data-stu-id="cc8fc-104">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="cc8fc-105">Tajné klíče uložené jako proměnné prostředí nebo uložené nástrojem pro tajný klíč Manager jsou stále místně uložených a bez šifrování v počítači.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="cc8fc-106">Bezpečnější možnost pro ukládání tajné klíče je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), která poskytuje zabezpečené, centrální umístění pro ukládání klíčů a tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="cc8fc-107">Balíček Microsoft.Extensions.Configuration.AzureKeyVault umožňuje aplikaci ASP.NET Core číst informace o konfiguraci z Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-107">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="cc8fc-108">Chcete-li začít používat tajné klíče z Azure Key Vault, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cc8fc-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="cc8fc-109">Nejprve zaregistrujte aplikaci jako aplikaci Azure AD.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-109">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="cc8fc-110">(Přístup k trezorů klíčů je spravované službou Azure AD). To lze provést prostřednictvím portálu správy Azure.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="cc8fc-111">Případně, pokud chcete, aby aplikace k ověření pomocí certifikátu, místo hesla nebo klienta tajný klíč, můžete použít [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) rutiny prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="cc8fc-112">Certifikát, který zaregistrujete s Azure Key Vault musí pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="cc8fc-113">(Vaše aplikace bude používat privátní klíč.)</span><span class="sxs-lookup"><span data-stu-id="cc8fc-113">(Your application will use the private key.)</span></span>

<span data-ttu-id="cc8fc-114">Druhý udělte přístup zaregistrovanou aplikaci do trezoru klíčů vytvořením nového objektu služby.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-114">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="cc8fc-115">To provedete pomocí následujících příkazů prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="cc8fc-115">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="cc8fc-116">Voláním metody rozšíření IConfigurationBuilder.AddAzureKeyVault při vytváření IConfigurationRoot instance třetí, obsahovat trezoru klíčů jako zdroj konfigurace v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-116">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="cc8fc-117">Všimněte si, že volání AddAzureKeyVault bude vyžadovat ID aplikace, který byl zaregistrován a poskytnut přístup k trezoru klíčů v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-117">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="cc8fc-118">V současné době .NET Standard a .NET Core podporují získávání informace o konfiguraci ze Azure Key Vault pomocí ID klienta a tajný klíč klienta.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-118">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="cc8fc-119">Aplikace rozhraní .NET framework, můžete použít přetížení IConfigurationBuilder.AddAzureKeyVault, která přebírá certifikát místo tajný klíč klienta.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-119">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="cc8fc-120">Době psaní tohoto textu je pracovní [v průběhu](https://github.com/aspnet/Configuration/issues/605) chcete zpřístupnit tento přetížení v rozhraní .NET Standard a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-120">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="cc8fc-121">Dokud AddAzureKeyVault přetížení, které přijímá certifikát je k dispozici aplikace ASP.NET Core můžete přístup k Azure Key Vault s ověřováním na základě certifikátu explicitně vytvořením objekt KeyVaultClient, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cc8fc-121">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="cc8fc-122">V tomto příkladu obsahuje volání AddAzureKeyVault na konci registraci zprostředkovatele konfigurace.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-122">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="cc8fc-123">Je osvědčeným postupem zaregistrovat Azure Key Vault jako poslední poskytovatel konfigurace tak, aby měl příležitost k přepsání hodnoty konfigurace z předchozí zprostředkovatele, a tak, aby žádné hodnoty konfigurace z jiných zdrojů přepíšou z trezoru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-123">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cc8fc-124">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cc8fc-124">Additional resources</span></span>

-   <span data-ttu-id="cc8fc-125">**Použití Azure Key Vault a k ochraně tajných klíčů aplikace**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="cc8fc-125">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="cc8fc-126">**Bezpečné úložiště tajné klíče aplikace během vývoje**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="cc8fc-126">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="cc8fc-127">**Konfigurace ochrany dat**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="cc8fc-127">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="cc8fc-128">**Klíč správy a dobu života**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data protection výchozí nastavení*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="cc8fc-128">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="cc8fc-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span><span class="sxs-lookup"><span data-stu-id="cc8fc-129">**Microsoft.Extensions.Configuration.DockerSecrets.**</span></span> <span data-ttu-id="cc8fc-130">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="cc8fc-130">GitHub repo.</span></span>
    [<span data-ttu-id="cc8fc-131">*https://github.com/ASPNET/Configuration/Tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span><span class="sxs-lookup"><span data-stu-id="cc8fc-131">*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*</span></span>](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
<span data-ttu-id="cc8fc-132">[Předchozí] (vývojáře app-tajné klíče storage.md) [Další] (.. / takeaways.md klíč)</span><span class="sxs-lookup"><span data-stu-id="cc8fc-132">[Previous] (developer-app-secrets-storage.md) [Next] (../key-takeaways.md)</span></span>
