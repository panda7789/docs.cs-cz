---
title: Ochrana tajných kódů při produkci pomocí Azure Key Vault
description: Zabezpečení v .NET Microservices a webových aplikací – Azure Key Vault je vynikající způsob, jak zpracovat tajné kódy aplikací, které jsou zcela řízeny správci. Správci mohou dokonce přiřadit a odvolat hodnoty vývoje, aniž by je vývojáři museli zpracovávat.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: cc95d491136c945255408cec2bd49d4d6579e29a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501757"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="d90b3-104">Použití azure key vault uchránit tajné klíče v době výroby</span><span class="sxs-lookup"><span data-stu-id="d90b3-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="d90b3-105">Tajné klíče uložené jako proměnné prostředí nebo uložené nástrojem Správce tajných barev jsou stále uloženy místně a nezašifrované v počítači.</span><span class="sxs-lookup"><span data-stu-id="d90b3-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="d90b3-106">Bezpečnější možností pro ukládání tajných kódů je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), který poskytuje zabezpečené, centrální umístění pro ukládání klíčů a tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="d90b3-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="d90b3-107">Balíček **Microsoft.Extensions.Configuration.AzureKeyVault** umožňuje ASP.NET základní aplikaci číst informace o konfiguraci z trezoru klíčů Azure.</span><span class="sxs-lookup"><span data-stu-id="d90b3-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="d90b3-108">Chcete-li začít používat tajné klíče z trezoru klíčů Azure, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d90b3-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="d90b3-109">Zaregistrujte svou aplikaci jako aplikaci Azure AD.</span><span class="sxs-lookup"><span data-stu-id="d90b3-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="d90b3-110">(Přístup k trezorům klíčů spravuje Azure AD.) To lze provést prostřednictvím portálu pro správu Azure.</span><span class="sxs-lookup"><span data-stu-id="d90b3-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="d90b3-111">Případně pokud chcete, aby se vaše aplikace ověřovala pomocí certifikátu namísto hesla nebo tajného klíče klienta, můžete použít rutinu prostředí PowerShell [Nové AzADAplikace.](/powershell/module/az.resources/new-azadapplication)</span><span class="sxs-lookup"><span data-stu-id="d90b3-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="d90b3-112">Certifikát, který zaregistrujete pomocí služby Azure Key Vault, potřebuje pouze váš veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="d90b3-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="d90b3-113">Aplikace bude používat soukromý klíč.</span><span class="sxs-lookup"><span data-stu-id="d90b3-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="d90b3-114">Podejte registrované aplikaci přístup k trezoru klíčů vytvořením nového instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="d90b3-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="d90b3-115">To lze provést pomocí následujících příkazů prostředí PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d90b3-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="d90b3-116">Zahrnout trezor klíčů jako zdroj konfigurace v <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> aplikaci voláním <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> metody rozšíření při vytváření instance.</span><span class="sxs-lookup"><span data-stu-id="d90b3-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="d90b3-117">Všimněte `AddAzureKeyVault` si, že volání vyžaduje ID aplikace, která byla registrována a udělen přístup k trezoru klíčů v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="d90b3-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="d90b3-118">Můžete také použít `AddAzureKeyVault` přetížení, které přebírá certifikát místo tajného klíče klienta pouze zahrnutím odkazu na balíček [Microsoft.IdentityModel.Clients.ActiveDirectory.](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory)</span><span class="sxs-lookup"><span data-stu-id="d90b3-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d90b3-119">Doporučujeme zaregistrovat Azure Key Vault jako poslední zprostředkovatel konfigurace, aby mohl přepsat hodnoty konfigurace od předchozích poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="d90b3-119">We recommend that you register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d90b3-120">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d90b3-120">Additional resources</span></span>

- <span data-ttu-id="d90b3-121">**Použití azure key vaultu k ochraně tajných kódů aplikací** </span><span class="sxs-lookup"><span data-stu-id="d90b3-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="d90b3-122">**Bezpečné ukládání tajných kódů aplikací během vývoje** </span><span class="sxs-lookup"><span data-stu-id="d90b3-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="d90b3-123">**Konfigurace ochrany dat** </span><span class="sxs-lookup"><span data-stu-id="d90b3-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="d90b3-124">**Správa klíčů a životnost klíčů pro ochranu dat v ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="d90b3-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="d90b3-125">Úložiště **GitHub Microsoft.Extensions.Configuration.KeyPerFile** GitHub.</span><span class="sxs-lookup"><span data-stu-id="d90b3-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="d90b3-126">[Předchozí](developer-app-secrets-storage.md)
>[další](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="d90b3-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
