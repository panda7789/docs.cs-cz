---
title: Bezpečné ukládání tajných kódů aplikace během vývoje
description: Zabezpečení v Mikroslužby .NET a webové aplikace - není ukládejte tajné klíče aplikace, jako jsou hesla, připojovací řetězce nebo klíče rozhraní API ve správě zdrojového kódu pochopit možnosti, které můžete použít v ASP.NET Core, zejména je nutné pochopit, jak zpracovávat " tajné kódy".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019422"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpečně Store tajných kódů aplikace během vývoje.

Pro připojení k chráněným prostředkům a dalších služeb, aplikací ASP.NET Core obvykle třeba použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace. Tyto citlivé údaje, se nazývají *tajných kódů*. Je osvědčeným postupem tak, aby nezahrnovala tajné kódy ve zdrojovém kódu a nezapomeňte ukládat tajné kódy ve správě zdrojového kódu. Místo toho měli používat ASP.NET Core konfigurační model čtení tajné klíče z více zabezpečených umístěních.

Je třeba oddělit tajné klíče pro přístup k vývoje a pracovním prostředkům z ty, které slouží pro přístup k produkční prostředky, protože různí jednotlivci bude potřebovat přístup k tyto různé sady tajných kódů. Běžné přístupy k ukládání tajných klíčů během vývoje použít, se buď tajné kódy ukládat v proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč. Pro úložiště bezpečnější v produkčním prostředí mikroslužby tajné kódy ukládat v Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Store tajných kódů v proměnných prostředí

Jeden způsob, jak uchovávat tajemství zdrojový kód je pro vývojáře k nastavení založené na řetězci tajné kódy jako [proměnné prostředí](/aspnet/core/security/app-secrets#environment-variables) na svých počítačích vývojářů. Při použití proměnných prostředí pro ukládání tajných kódů pomocí hierarchických názvy, například těch, které jsou vnořené v oddílech konfigurace, je nutné pojmenovat proměnné k zahrnutí úplné hierarchie její části oddělené znakem dvojtečky (:).

Například nastavením proměnné prostředí `Logging:LogLevel:Default` k `Debug` hodnota bude ekvivalentní hodnotu konfigurace z následujícího souboru JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Pro přístup k tyto hodnoty z proměnných prostředí, potřebuje aplikace právě volat AddEnvironmentVariables jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.

Všimněte si, že proměnné prostředí jsou obvykle uložené jako prostý text, takže pokud počítači nebo procesu s proměnnými prostředí dojde k ohrožení, hodnoty proměnné prostředí se nebude zobrazovat.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Store tajných kódů pomocí manažera tajných základní technologie ASP.NET

ASP.NET Core [manažera tajných](/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajných kódů ze zdrojového kódu. Chcete-li pomocí nástroje Správce tajný klíč, nainstalujte balíček **Microsoft.Extensions.Configuration.SecretManager** v souboru projektu. Jakmile je k dispozici dané závislosti a byla obnovena, `dotnet user-secrets` příkaz lze použít k nastavení hodnoty tajných kódů z příkazového řádku. Těchto tajných kódů se uloží do souboru JSON v uživatele adresář profilu (podrobnosti se liší podle operačního systému), od zdrojového kódu.

Nastavit pomocí nástroje Správce tajný klíč tajné kódy jsou uspořádané podle `UserSecretsId` vlastnosti projektu, který je použití tajné klíče. Proto musíte být potřeba nastavit vlastnost UserSecretsId v souboru projektu, jak je znázorněno v následujícím fragmentu kódu. Výchozí hodnota je identifikátor GUID přidělený pomocí sady Visual Studio, ale aktuální řetězcovou není důležité, dokud bude jednoznačný ve vašem počítači.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Tajnými kódy uloženými v aplikaci pomocí manažera tajných pomocí provádí volání `AddUserSecrets<T>` na instanci ConfigurationBuilder zahrnovat tajné kódy pro aplikaci v jeho konfiguraci. Obecný parametr T musí být typu ze sestavení, které byly použity UserSecretId k. Obvykle pomocí `AddUserSecrets<Startup>` je v pořádku.

`AddUserSecrets<Startup>()` Je součástí výchozí možnosti pro vývojové prostředí při použití `CreateDefaultBuilder` metoda *Program.cs*.

>[!div class="step-by-step"]
>[Předchozí](authorization-net-microservices-web-applications.md)
>[další](azure-key-vault-protects-secrets.md)
