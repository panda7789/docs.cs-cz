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
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Použití azure key vault uchránit tajné klíče v době výroby

Tajné klíče uložené jako proměnné prostředí nebo uložené nástrojem Správce tajných barev jsou stále uloženy místně a nezašifrované v počítači. Bezpečnější možností pro ukládání tajných kódů je [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), který poskytuje zabezpečené, centrální umístění pro ukládání klíčů a tajných kódů.

Balíček **Microsoft.Extensions.Configuration.AzureKeyVault** umožňuje ASP.NET základní aplikaci číst informace o konfiguraci z trezoru klíčů Azure. Chcete-li začít používat tajné klíče z trezoru klíčů Azure, postupujte takto:

1. Zaregistrujte svou aplikaci jako aplikaci Azure AD. (Přístup k trezorům klíčů spravuje Azure AD.) To lze provést prostřednictvím portálu pro správu Azure.\

   Případně pokud chcete, aby se vaše aplikace ověřovala pomocí certifikátu namísto hesla nebo tajného klíče klienta, můžete použít rutinu prostředí PowerShell [Nové AzADAplikace.](/powershell/module/az.resources/new-azadapplication) Certifikát, který zaregistrujete pomocí služby Azure Key Vault, potřebuje pouze váš veřejný klíč. Aplikace bude používat soukromý klíč.

2. Podejte registrované aplikaci přístup k trezoru klíčů vytvořením nového instančního objektu. To lze provést pomocí následujících příkazů prostředí PowerShell:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Zahrnout trezor klíčů jako zdroj konfigurace v <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> aplikaci voláním <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> metody rozšíření při vytváření instance. Všimněte `AddAzureKeyVault` si, že volání vyžaduje ID aplikace, která byla registrována a udělen přístup k trezoru klíčů v předchozích krocích.

   Můžete také použít `AddAzureKeyVault` přetížení, které přebírá certifikát místo tajného klíče klienta pouze zahrnutím odkazu na balíček [Microsoft.IdentityModel.Clients.ActiveDirectory.](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory)

> [!IMPORTANT]
> Doporučujeme zaregistrovat Azure Key Vault jako poslední zprostředkovatel konfigurace, aby mohl přepsat hodnoty konfigurace od předchozích poskytovatelů.

## <a name="additional-resources"></a>Další zdroje

- **Použití azure key vaultu k ochraně tajných kódů aplikací** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Bezpečné ukládání tajných kódů aplikací během vývoje** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Konfigurace ochrany dat** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **Správa klíčů a životnost klíčů pro ochranu dat v ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- Úložiště **GitHub Microsoft.Extensions.Configuration.KeyPerFile** GitHub. \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
>[Předchozí](developer-app-secrets-storage.md)
>[další](../key-takeaways.md)
