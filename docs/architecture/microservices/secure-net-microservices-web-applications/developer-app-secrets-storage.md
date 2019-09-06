---
title: Bezpečné ukládání tajných kódů aplikace během vývoje
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – neukládejte tajné klíče vaší aplikace jako hesla, připojovací řetězce nebo klíče rozhraní API ve správě zdrojového kódu. Seznamte se s možnostmi, které můžete použít v ASP.NET Core, zejména musíte pochopit, jak se má řídit uživatel. tajné kódy.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296484"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpečné ukládání tajných kódů aplikací během vývoje

Aby bylo možné se připojit k chráněným prostředkům a dalším službám, aplikace ASP.NET Core obvykle potřebují použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace. Tyto citlivé části informací se nazývají *tajné*kódy. Osvědčeným postupem je nezahrnovat tajné kódy do zdrojového kódu a zajistit, aby se neukládaly tajné klíče ve správě zdrojového kódu. Místo toho byste měli použít konfigurační model ASP.NET Core ke čtení tajných kódů z bezpečnějších umístění.

Musíte oddělit tajné klíče pro přístup k vývojovým a pracovním prostředkům z těch, které se používají pro přístup k produkčním prostředkům, protože různí uživatelé budou potřebovat přístup k těmto různým sadám tajných kódů. Pro ukládání tajných kódů používaných při vývoji se běžně používají k ukládání tajných klíčů do proměnných prostředí nebo pomocí nástroje ASP.NET Core správce tajných klíčů. Pro bezpečnější úložiště v produkčních prostředích můžou mikroslužby ukládat tajné kódy do Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Uložení tajných kódů v proměnných prostředí

Jedním ze způsobů, jak zachovat tajné klíče ze zdrojového kódu, je vývojářům nastavovat tajné klíče jako [proměnné prostředí](/aspnet/core/security/app-secrets#environment-variables) na svých vývojových počítačích. Když použijete proměnné prostředí k ukládání tajných kódů s hierarchickými názvy, jako jsou ty, které jsou vnořené v konfiguračních oddílech, musíte proměnné pojmenovat tak, aby zahrnovaly celou hierarchii jeho sekcí, oddělená dvojtečkami (:).

Například nastavení proměnné `Logging:LogLevel:Default` prostředí na `Debug` hodnotu by bylo ekvivalentní hodnotě konfigurace z následujícího souboru JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Pro přístup k těmto hodnotám z proměnných prostředí musí aplikace při vytváření objektu IConfigurationRoot volat pouze AddEnvironmentVariables na své nerozšiřuje configurationbuilder.

Všimněte si, že proměnné prostředí se běžně ukládají jako prostý text, takže pokud dojde k ohrožení bezpečnosti počítače nebo procesu s proměnnými prostředí, budou se zobrazovat hodnoty proměnných prostředí.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Uložení tajných kódů pomocí Správce ASP.NET Core tajných klíčů

Nástroj ASP.NET Core [správce tajných](/aspnet/core/security/app-secrets#secret-manager) klíčů poskytuje další způsob udržování tajných kódů ze zdrojového kódu. Chcete-li použít nástroj Správce tajných klíčů, nainstalujte balíček **Microsoft. Extensions. Configuration. SecretManager** do souboru projektu. Jakmile je tato závislost přítomna a byla obnovena, `dotnet user-secrets` lze pomocí příkazu nastavit hodnotu tajných kódů z příkazového řádku. Tyto tajné kódy budou uloženy v souboru JSON v adresáři profilu uživatele (podrobnosti se liší podle operačního systému), a to mimo zdrojový kód.

Tajné klíče nastavené nástrojem Správce tajných klíčů jsou uspořádány podle `UserSecretsId` vlastnosti projektu, který používá tajné klíče. Proto je nutné, abyste nastavili vlastnost UserSecretsId v souboru projektu, jak je znázorněno v následujícím fragmentu kódu. Výchozí hodnota je identifikátor GUID přiřazený aplikací Visual Studio, ale skutečný řetězec není důležitý, pokud je v počítači jedinečný.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Používání tajných klíčů uložených s tajným správcem v aplikaci se provádí `AddUserSecrets<T>` voláním instance nerozšiřuje configurationbuilder, aby zahrnovala tajné klíče pro aplikaci ve své konfiguraci. Obecný parametr T by měl být typ ze sestavení, na které se UserSecretId použil. Obvykle je `AddUserSecrets<Startup>` používání velmi přesné.

Je součástí výchozích možností pro vývojové prostředí při `CreateDefaultBuilder` použití metody v *program.cs*. `AddUserSecrets<Startup>()`

>[!div class="step-by-step"]
>[Předchozí](authorization-net-microservices-web-applications.md)Další
>[](azure-key-vault-protects-secrets.md)
