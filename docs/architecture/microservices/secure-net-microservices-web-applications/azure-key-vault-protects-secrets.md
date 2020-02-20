---
title: Ochrana tajných kódů při produkci pomocí Azure Key Vault
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – Azure Key Vault je skvělým způsobem, jak zpracovávat tajné klíče aplikací, které jsou zcela řízené správci. Správci mohou dokonce přiřazovat a odvolávat hodnoty vývoje bez vývojářů, kteří je chtějí zpracovat.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: cc95d491136c945255408cec2bd49d4d6579e29a
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501757"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="7e94d-104">Použití Azure Key Vault k ochraně tajných kódů v produkčním čase</span><span class="sxs-lookup"><span data-stu-id="7e94d-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="7e94d-105">Tajné klíče uložené jako proměnné prostředí nebo uložené nástrojem Správce tajných klíčů jsou pořád uložené místně a v počítači nejsou zašifrované.</span><span class="sxs-lookup"><span data-stu-id="7e94d-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="7e94d-106">Bezpečnější je možnost ukládání tajných kódů je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), což zajišťuje zabezpečené, centrální umístění pro ukládání klíčů a tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="7e94d-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="7e94d-107">Balíček **Microsoft. Extensions. Configuration. AzureKeyVault** umožňuje aplikaci ASP.NET Core číst informace o konfiguraci z Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="7e94d-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="7e94d-108">Pokud chcete začít používat tajné klíče z Azure Key Vault, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="7e94d-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="7e94d-109">Zaregistrujte svoji aplikaci jako aplikaci Azure AD.</span><span class="sxs-lookup"><span data-stu-id="7e94d-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="7e94d-110">(Přístup k trezorům klíčů spravuje Azure AD.) To se dá udělat na portálu pro správu Azure. </span><span class="sxs-lookup"><span data-stu-id="7e94d-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="7e94d-111">Případně, pokud chcete, aby se aplikace ověřovala pomocí certifikátu místo hesla nebo tajného klíče klienta, můžete použít rutinu [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e94d-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="7e94d-112">Certifikát, který zaregistrujete pomocí Azure Key Vault potřebuje jenom svůj veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="7e94d-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="7e94d-113">Vaše aplikace bude používat privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="7e94d-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="7e94d-114">Udělte registrované aplikaci přístup k trezoru klíčů vytvořením nového instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="7e94d-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="7e94d-115">Můžete to provést pomocí následujících příkazů PowerShellu:</span><span class="sxs-lookup"><span data-stu-id="7e94d-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="7e94d-116">Zahrňte Trezor klíčů jako zdroj konfigurace v aplikaci voláním metody rozšíření <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> při vytváření instance <xref:Microsoft.Extensions.Configuration.IConfigurationRoot>.</span><span class="sxs-lookup"><span data-stu-id="7e94d-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="7e94d-117">Všimněte si, že volání `AddAzureKeyVault` vyžaduje ID aplikace, které bylo zaregistrováno a kterému byl udělen přístup k trezoru klíčů v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="7e94d-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="7e94d-118">Můžete také použít přetížení `AddAzureKeyVault`, které přebírá certifikát místo tajného klíče klienta, a to jenom tak, že obsahuje odkaz na balíček [Microsoft. IdentityModel. clients. Active](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) .</span><span class="sxs-lookup"><span data-stu-id="7e94d-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e94d-119">Doporučujeme, abyste jako poslední Poskytovatel konfigurace zaregistrovali Azure Key Vault, takže může přepsat hodnoty konfigurace z předchozích zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="7e94d-119">We recommend that you register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7e94d-120">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="7e94d-120">Additional resources</span></span>

- <span data-ttu-id="7e94d-121">**Použití Azure Key Vault k ochraně tajných klíčů aplikace** </span><span class="sxs-lookup"><span data-stu-id="7e94d-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="7e94d-122">**Bezpečné ukládání tajných kódů aplikací během vývoje** </span><span class="sxs-lookup"><span data-stu-id="7e94d-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="7e94d-123">**Konfigurace \ ochrany dat**</span><span class="sxs-lookup"><span data-stu-id="7e94d-123">**Configuring data protection** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="7e94d-124">**Správa a životnost klíče ochrany dat v ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="7e94d-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="7e94d-125">**Microsoft. Extensions. Configuration. KeyPerFile** – úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="7e94d-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="7e94d-126">[Předchozí](developer-app-secrets-storage.md)
>[Další](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="7e94d-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
