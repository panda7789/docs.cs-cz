---
title: Bezpečné ukládání tajných kódů aplikace během vývoje
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – neukládejte tajné klíče vaší aplikace jako hesla, připojovací řetězce nebo klíče rozhraní API ve správě zdrojového kódu. Seznamte se s možnostmi, které můžete použít v ASP.NET Core, zejména musíte pochopit, jak se má řídit uživatel. tajné kódy.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501789"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpečné ukládání tajných kódů aplikací během vývoje

Aby bylo možné se připojit k chráněným prostředkům a dalším službám, aplikace ASP.NET Core obvykle potřebují použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace. Tyto citlivé části informací se nazývají *tajné*kódy. Osvědčeným postupem je nezahrnovat tajné kódy do zdrojového kódu a zajistit, aby se neukládaly tajné klíče ve správě zdrojového kódu. Místo toho byste měli použít konfigurační model ASP.NET Core ke čtení tajných kódů z bezpečnějších umístění.

Musíte oddělit tajné klíče pro přístup k vývojovým a pracovním prostředkům z těch, které se používají pro přístup k produkčním prostředkům, protože různí uživatelé budou potřebovat přístup k těmto různým sadám tajných kódů. Pro ukládání tajných kódů používaných při vývoji se běžně používají k ukládání tajných klíčů do proměnných prostředí nebo pomocí nástroje ASP.NET Core správce tajných klíčů. Pro bezpečnější úložiště v produkčních prostředích můžou mikroslužby ukládat tajné kódy do Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Uložení tajných kódů v proměnných prostředí

Jedním ze způsobů, jak zachovat tajné klíče ze zdrojového kódu, je vývojářům nastavovat tajné klíče jako [proměnné prostředí](/aspnet/core/security/app-secrets#environment-variables) na svých vývojových počítačích. Když použijete proměnné prostředí k ukládání tajných kódů s hierarchickými názvy, jako jsou ty, které jsou vnořené v konfiguračních oddílech, musíte proměnné pojmenovat tak, aby zahrnovaly celou hierarchii jeho sekcí, oddělená dvojtečkami (:).

Například nastavení proměnné prostředí `Logging:LogLevel:Default` na hodnotu `Debug` hodnota by byla ekvivalentní hodnotě konfigurace z následujícího souboru JSON:

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

Nástroj ASP.NET Core [správce tajných](/aspnet/core/security/app-secrets#secret-manager) klíčů poskytuje další způsob udržování tajných kódů ze zdrojového kódu **během vývoje**. Chcete-li použít nástroj Správce tajných klíčů, nainstalujte balíček **Microsoft. Extensions. Configuration. SecretManager** do souboru projektu. Jakmile je tato závislost přítomna a byla obnovena, lze pomocí příkazu `dotnet user-secrets` nastavit hodnotu tajných kódů z příkazového řádku. Tyto tajné kódy budou uloženy v souboru JSON v adresáři profilu uživatele (podrobnosti se liší podle operačního systému), a to mimo zdrojový kód.

Tajné klíče nastavené nástrojem Správce tajných klíčů jsou uspořádány pomocí vlastnosti `UserSecretsId` projektu, který používá tajné kódy. Proto je nutné, abyste nastavili vlastnost UserSecretsId v souboru projektu, jak je znázorněno v následujícím fragmentu kódu. Výchozí hodnota je identifikátor GUID přiřazený aplikací Visual Studio, ale skutečný řetězec není důležitý, pokud je v počítači jedinečný.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Používání tajných klíčů uložených s tajným správcem v aplikaci se provádí voláním `AddUserSecrets<T>` na instanci nerozšiřuje configurationbuilder, aby se do své konfigurace zahrnuly tajné kódy pro aplikaci. Obecný parametr T by měl být typ ze sestavení, na které se UserSecretId použil. Obvykle je použití `AddUserSecrets<Startup>` přesné.

`AddUserSecrets<Startup>()` je součástí výchozích možností pro vývojové prostředí při použití metody `CreateDefaultBuilder` v *program.cs*.

>[!div class="step-by-step"]
>[Předchozí](authorization-net-microservices-web-applications.md)
>[Další](azure-key-vault-protects-secrets.md)
