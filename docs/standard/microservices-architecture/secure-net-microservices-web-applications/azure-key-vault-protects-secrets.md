---
title: Pomocí služby Azure Key Vault k ochraně tajných kódů při produkci
description: Zabezpečení v rozhraní .NET Mikroslužeb a webových aplikací – Azure Key Vault je vynikající způsob, jak zpracovat tajných klíčů aplikací, které jsou zcela řídí ji správci. Správci můžou i přiřazení a odvolávat hodnoty vývoj bez vývojáře s jejich zpracování.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 291d60f941e4280ff120296ce1c392df3300dc44
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362416"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Použití Azure Key Vault k ochraně tajných kódů při produkci

Tajné kódy uložené jako proměnné prostředí nebo neukládá nástroj tajný klíč správce jsou stále místně uložená a nešifrované na počítači. Je bezpečnější možnost pro ukládání tajných kódů [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), která poskytuje zabezpečené a centrální umístění pro ukládání klíčů a tajných kódů.

**Microsoft.Extensions.Configuration.AzureKeyVault** balíček umožní aplikaci ASP.NET Core číst informace o konfiguraci ze služby Azure Key Vault. Pokud chcete začít používat tajné kódy ze služby Azure Key Vault, postupujte takto:

1. Zaregistrujte aplikaci jako aplikaci Azure AD. (Přístup k trezorům klíčů se spravuje přes Azure AD). To můžete udělat přes portál pro správu Azure. \

   Případně, pokud chcete, aby aplikace k ověřování pomocí certifikátu místo tajného klíče klienta nebo heslo, můžete použít [New-AzureRmADApplication](/powershell/module/azurerm.resources/new-azurermadapplication) rutiny Powershellu. Certifikát, který zaregistrujete pomocí služby Azure Key Vault potřebuje pouze veřejný klíč. (Aplikace bude používat privátní klíč).

2. Poskytují zaregistrovanou aplikaci přístup k trezoru klíčů tak, že vytvoříte novou službu objektu zabezpečení. Můžete provést pomocí následujících příkazů Powershellu:

   ```powershell
   $sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Zahrnout trezoru klíčů jako zdroj konfigurace ve vaší aplikaci pomocí volání <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> rozšiřující metoda při vytváření <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance. Všimněte si, že volání `AddAzureKeyVault` vyžaduje ID aplikace, který byl zaregistrován a poskytnut přístup k trezoru klíčů v předchozích krocích.

   Můžete také použít přetížení `AddAzureKeyVault` certifikátu místo tajného klíče klienta, která přijímá pouze zahrnutím odkazu na [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) balíčku.

> [!IMPORTANT]
> Doporučujeme si služby Azure Key Vault zaregistrovat jako poslední poskytovatele konfigurace, jej můžete přepsat hodnoty konfigurace z předchozích poskytovatelů.

## <a name="additional-resources"></a>Další zdroje

- **Použití Azure Key Vault k ochraně tajných klíčů aplikací** \
  [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Bezpečné ukládání tajných kódů aplikace během vývoje.** \
  [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](/aspnet/core/security/app-secrets)

- **Konfigurace ochrany dat** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](/aspnet/core/security/data-protection/configuration/overview)

- **Správa klíčů a doba života** \
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

- **Microsoft.Extensions.Configuration.KeyPerFile** úložiště GitHub. \
  [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
>[Předchozí](developer-app-secrets-storage.md)
>[další](../key-takeaways.md)
