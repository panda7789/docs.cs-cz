---
title: Bezpečné ukládání tajných kódů aplikace během vývoje.
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Bezpečné ukládání tajných kódů aplikace během vývoje.
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6f5dfbb53b99fec4d7cc66c528fe866c71c2172f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143867"
---
# <a name="storing-application-secrets-safely-during-development"></a>Bezpečné ukládání tajných kódů aplikace během vývoje.

Pro připojení k chráněným prostředkům a dalších služeb, aplikací ASP.NET Core obvykle třeba použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace. Tyto citlivé údaje, se nazývají *tajných kódů*. Je osvědčeným postupem tak, aby nezahrnovala tajné kódy ve zdrojovém kódu a určitě ne k uložení tajných kódů ve správě zdrojového kódu. Místo toho měli používat ASP.NET Core konfigurační model čtení tajné klíče z více zabezpečených umístěních.

Je vhodné oddělit tajné klíče pro přístup k vývoje a pracovním prostředkům se používají pro přístup k produkční prostředky, protože různí jednotlivci bude potřebovat přístup k tyto různé sady tajných kódů. Běžné přístupy k ukládání tajných klíčů během vývoje použít, se buď tajné kódy ukládat v proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč. Pro úložiště bezpečnější v produkčním prostředí mikroslužby tajné kódy ukládat v Azure Key Vault.

## <a name="storing-secrets-in-environment-variables"></a>Ukládání tajných kódů v proměnných prostředí

Jeden způsob, jak uchovávat tajemství zdrojový kód je pro vývojáře k nastavení založené na řetězci tajné kódy jako [proměnné prostředí](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na svých počítačích vývojářů. Při použití proměnných prostředí pro uložení tajných kódů pomocí hierarchických názvy (ty vnořené v oddílech konfigurace), vytvořte název proměnné prostředí, která zahrnuje hierarchii úplný název tajného klíče odděleny dvojtečkou (:).

Například nastavením proměnné prostředí protokolování: LogLevel:Default ladění by ekvivalentní hodnotu konfigurace z následujícího souboru JSON:

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

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Ukládání tajných kódů pomocí manažera tajných ASP.NET Core

ASP.NET Core [manažera tajných](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajných kódů ze zdrojového kódu. Použití nástroje Správce tajný klíč, obsahuje odkaz nástroje (DotNetCliToolReference) Microsoft.Extensions.SecretManager.Tools balíčku v souboru projektu. Jakmile dané závislosti je k dispozici a byla obnovena, příkaz dotnet tajných kódů uživatelů slouží k nastavení hodnoty tajných kódů z příkazového řádku. Těchto tajných kódů se uloží do souboru JSON v uživatele adresář profilu (podrobnosti se liší podle operačního systému), od zdrojového kódu.

Nastavit pomocí nástroje Správce tajný klíč tajné kódy jsou uspořádané podle UserSecretsId vlastnosti projektu, který je použití tajné klíče. Proto musí být potřeba nastavit vlastnost UserSecretsId v souboru projektu (jak je znázorněno v následujícím fragmentu kódu). Skutečné řetězec použitý jako ID není důležité, jako je jedinečný v rámci projektu.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Tajnými kódy uloženými v aplikaci pomocí manažera tajných pomocí provádí volání AddUserSecrets&lt;T&gt; na instanci ConfigurationBuilder zahrnovat tajné kódy pro aplikaci v jeho konfiguraci. Obecný parametr T musí být typu ze sestavení, které byly použity UserSecretId k. Obvykle pomocí AddUserSecrets&lt;spuštění&gt; je v pořádku.


>[!div class="step-by-step"]
>[Předchozí](authorization-net-microservices-web-applications.md)
>[další](azure-key-vault-protects-secrets.md)