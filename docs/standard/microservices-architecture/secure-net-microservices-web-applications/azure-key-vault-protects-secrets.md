---
title: Ochrana tajných kódů při produkci pomocí Azure Key Vault
description: Zabezpečení v rozhraní .NET Mikroslužeb a webových aplikací – Azure Key Vault je vynikající způsob, jak zpracovat tajných klíčů aplikací, které jsou zcela řídí ji správci. Správci můžou i přiřazení a odvolávat hodnoty vývoj bez vývojáře s jejich zpracování.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019539"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="fd8a5-104">Použití Azure Key Vault k ochraně tajných kódů při produkci</span><span class="sxs-lookup"><span data-stu-id="fd8a5-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="fd8a5-105">Tajné kódy uložené jako proměnné prostředí nebo neukládá nástroj tajný klíč správce jsou stále místně uložená a nešifrované na počítači.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="fd8a5-106">Je bezpečnější možnost pro ukládání tajných kódů [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), která poskytuje zabezpečené a centrální umístění pro ukládání klíčů a tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="fd8a5-107">**Microsoft.Extensions.Configuration.AzureKeyVault** balíček umožní aplikaci ASP.NET Core číst informace o konfiguraci ze služby Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="fd8a5-108">Pokud chcete začít používat tajné kódy ze služby Azure Key Vault, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="fd8a5-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="fd8a5-109">Zaregistrujte aplikaci jako aplikaci Azure AD.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="fd8a5-110">(Přístup k trezorům klíčů se spravuje přes Azure AD). To můžete udělat přes portál pro správu Azure. \\</span><span class="sxs-lookup"><span data-stu-id="fd8a5-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\\</span></span>

   <span data-ttu-id="fd8a5-111">Případně, pokud chcete, aby aplikace k ověřování pomocí certifikátu místo tajného klíče klienta nebo heslo, můžete použít [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) rutiny Powershellu.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="fd8a5-112">Certifikát, který zaregistrujete pomocí služby Azure Key Vault potřebuje pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="fd8a5-113">Vaše aplikace bude používat privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="fd8a5-114">Poskytují zaregistrovanou aplikaci přístup k trezoru klíčů tak, že vytvoříte novou službu objektu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="fd8a5-115">Můžete provést pomocí následujících příkazů Powershellu:</span><span class="sxs-lookup"><span data-stu-id="fd8a5-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="fd8a5-116">Zahrnout trezoru klíčů jako zdroj konfigurace ve vaší aplikaci pomocí volání <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> rozšiřující metoda při vytváření <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="fd8a5-117">Všimněte si, že volání `AddAzureKeyVault` vyžaduje ID aplikace, který byl zaregistrován a poskytnut přístup k trezoru klíčů v předchozích krocích.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="fd8a5-118">Můžete také použít přetížení `AddAzureKeyVault` certifikátu místo tajného klíče klienta, která přijímá pouze zahrnutím odkazu na [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) balíčku.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd8a5-119">Doporučujeme si služby Azure Key Vault zaregistrovat jako poslední poskytovatele konfigurace, jej můžete přepsat hodnoty konfigurace z předchozích poskytovatelů.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fd8a5-120">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="fd8a5-120">Additional resources</span></span>

- <span data-ttu-id="fd8a5-121">**Použití Azure Key Vault k ochraně tajných klíčů aplikací** \\</span><span class="sxs-lookup"><span data-stu-id="fd8a5-121">**Using Azure Key Vault to protect application secrets** \\</span></span>
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="fd8a5-122">**Bezpečné ukládání tajných kódů aplikace během vývoje.** \\</span><span class="sxs-lookup"><span data-stu-id="fd8a5-122">**Safe storage of app secrets during development** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="fd8a5-123">**Konfigurace ochrany dat** \\</span><span class="sxs-lookup"><span data-stu-id="fd8a5-123">**Configuring data protection** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="fd8a5-124">**Správa klíčů ochrany dat a životnosti v ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="fd8a5-124">**Data Protection key management and lifetime in ASP.NET Core** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="fd8a5-125">**Microsoft.Extensions.Configuration.KeyPerFile** úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="fd8a5-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="fd8a5-126">[Předchozí](developer-app-secrets-storage.md)
>[další](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="fd8a5-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
