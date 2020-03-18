---
title: Bezpečné ukládání tajných kódů aplikace během vývoje
description: Zabezpečení v .NET Microservices a webových aplikací - Neukládejte tajné klíče aplikace, jako jsou hesla, připojovací řetězce nebo klíče rozhraní API ve slučování zdrojového kódu, pochopit možnosti, které můžete použít v ASP.NET Core, zejména musíte pochopit, jak zacházet s "uživatel tajemství".
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501789"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpečné ukládání tajných kódů aplikací během vývoje

Chcete-li se spojit s chráněnými prostředky a dalšími službami, ASP.NET základní aplikace obvykle potřebují používat připojovací řetězce, hesla nebo jiná pověření, která obsahují citlivé informace. Tyto citlivé informace se nazývají *tajemství*. Je osvědčeným postupem nezahrnovat tajné klíče ve zdrojovém kódu a ujistěte se, že není ukládat tajné klíče ve správě zdrojového kódu. Místo toho byste měli použít model konfigurace ASP.NET Core ke čtení tajných kódů z bezpečnějších umístění.

Je nutné oddělit tajné klíče pro přístup k vývoji a pracovní prostředky z těch, které se používají pro přístup k produkční prostředky, protože různé osoby budou potřebovat přístup k těmto různým sady tajných kódů. Chcete-li uložit tajné klíče používané během vývoje, běžné přístupy jsou buď ukládat tajné kódy v proměnných prostředí nebo pomocí nástroje ASP.NET Core Secret Manager. Pro bezpečnější úložiště v produkčním prostředí mikroslužeb můžete ukládat tajné klíče v trezoru klíčů Azure.

## <a name="store-secrets-in-environment-variables"></a>Ukládání tajných kódů v proměnných prostředí

Jedním ze způsobů, jak zachovat tajné kódy mimo zdrojový kód, je pro vývojáře nastavit tajné [kódy](/aspnet/core/security/app-secrets#environment-variables) založené na řetězec jako proměnné prostředí na svých vývojových počítačích. Při použití proměnných prostředí k ukládání tajných kódů s hierarchickými názvy, jako jsou ty vnořené v konfiguračních oddílech, je nutné pojmenovat proměnné tak, aby zahrnovaly úplnou hierarchii jejích oddílů, oddělené dvojtečkami (:).

Například nastavení proměnné `Logging:LogLevel:Default` prostředí `Debug` na hodnotu by bylo ekvivalentní hodnotě konfigurace z následujícího souboru JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Chcete-li získat přístup k těmto hodnotám z proměnných prostředí, aplikace stačí volat AddEnvironmentVariables na jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.

Všimněte si, že proměnné prostředí jsou běžně uloženy jako prostý text, takže pokud je ohrožen počítač nebo proces s proměnnými prostředí, budou viditelné hodnoty proměnných prostředí.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Ukládání tajných kódů pomocí správce tajných klíčů ASP.NET Core

Nástroj ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) poskytuje další způsob, jak uchovávat tajemství mimo zdrojový kód **během vývoje**. Chcete-li použít nástroj Správce tajných barev, nainstalujte balíček **Microsoft.Extensions.Configuration.SecretManager** do souboru projektu. Jakmile je tato závislost k dispozici a `dotnet user-secrets` byla obnovena, příkaz lze použít k nastavení hodnoty tajných kódů z příkazového řádku. Tyto tajné klíče budou uloženy v souboru JSON v adresáři profilu uživatele (podrobnosti se liší podle operačního systému), mimo zdrojový kód.

Tajné klíče stanovené nástrojem Správce tajných barev jsou uspořádány `UserSecretsId` podle vlastnosti projektu, který používá tajné klíče. Proto musíte být jisti, nastavit Vlastnost UserSecretsId v souboru projektu, jak je znázorněno ve výstřižku níže. Výchozí hodnota je identifikátor GUID přiřazený visual studio, ale skutečný řetězec není důležité, pokud je jedinečný v počítači.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Použití tajných klíčů uložených s Správcem `AddUserSecrets<T>` tajných klíčů v aplikaci se provádí voláním instance ConfigurationBuilder tak, aby do své konfigurace zahrnula tajné klíče aplikace. Obecný parametr T by měl být typ ze sestavení, které UserSecretId byla použita. Obvykle `AddUserSecrets<Startup>` se používá v pořádku.

Je `AddUserSecrets<Startup>()` součástí výchozích možností pro vývojové prostředí `CreateDefaultBuilder` při použití metody v *Program.cs*.

>[!div class="step-by-step"]
>[Předchozí](authorization-net-microservices-web-applications.md)
>[další](azure-key-vault-protects-secrets.md)
