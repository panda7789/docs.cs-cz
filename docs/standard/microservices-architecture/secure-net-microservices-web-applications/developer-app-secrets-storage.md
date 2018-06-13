---
title: Ukládání tajné klíče aplikace bezpečně během vývoje
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Ukládání tajné klíče aplikace bezpečně během vývoje
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d8dd2da07104d6461d4eec0cb3fccd61c4db71c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580111"
---
# <a name="storing-application-secrets-safely-during-development"></a>Ukládání tajné klíče aplikace bezpečně během vývoje

Pro připojení k chráněným prostředkům a další služby, aplikace ASP.NET Core obvykle nutné použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace. Tyto důvěrné údaje se nazývají *tajné klíče*. Je osvědčeným postupem tak, aby neobsahoval tajné klíče ve zdrojovém kódu a určitě nechcete ukládat tajné klíče ve správě zdrojového kódu. Místo toho používejte konfigurační model ASP.NET Core čtení těchto tajných klíčů z více zabezpečeného umístění.

Je vhodné oddělit tajné klíče pro přístup k vývoji a pracovní prostředky z těch, které používá pro přístup k prostředkům produkční, protože různí jednotlivci budete potřebovat přístup k tyto různé sady tajných klíčů. K uložení použít během vývoje tajné klíče, jsou běžné přístupy buď ukládat tajné klíče v seznamu proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč. Pro bezpečnější úložiště v produkčním prostředí může mikroslužeb ukládat tajné klíče v Azure Key Vault.

## <a name="storing-secrets-in-environment-variables"></a>Ukládání tajné klíče v seznamu proměnných prostředí

Je možné zachovat tajné klíče ze zdrojového kódu pro vývojáře k nastavení založené na řetězcích tajné klíče jako [proměnné prostředí](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na jejich vývoj počítačů. Při použití proměnných prostředí pro ukládání tajných klíčů s hierarchické názvy (ty vnořené v oddílech konfigurace), vytvořte název pro objekt environment variables, který obsahuje úplnou hierarchii název tajného klíče, oddělený dvojtečky (:).

Například nastavením proměnné prostředí protokolování: LogLevel:Default na ladění by ekvivalentní na hodnotu konfigurace z následujícího souboru JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

K tyto hodnoty z proměnných prostředí aplikace právě musí volat AddEnvironmentVariables jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.

Všimněte si, že proměnné prostředí jsou obecně uložené jako prostý text, takže pokud k počítači nebo proces s proměnné prostředí dojde k narušení, se nebude zobrazovat hodnoty proměnných prostředí.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Ukládání tajné klíče pomocí Správce technologie ASP.NET Core tajný klíč

ASP.NET Core [tajný klíč správce](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajné klíče ze zdrojového kódu. Použití nástroje Správce tajný klíč, obsahovat odkaz nástroje (DotNetCliToolReference) k Microsoft.Extensions.SecretManager.Tools balíčku v souboru projektu. Po této závislostí je k dispozici a byla obnovena, příkaz uživatele tajemství dotnet. lze použít k nastavení hodnoty tajných údajů z příkazového řádku. Tato tajná data se uloží do souboru JSON v profilu adresáře uživatele (podrobnosti se liší podle operačního systému), od zdrojového kódu.

Tajné klíče, která nastavuje nástroj Správce tajný klíč jsou uspořádány UserSecretsId vlastností projektu, který používá těchto tajných klíčů. Proto musí být nastavte vlastnost UserSecretsId v souboru projektu (jak je znázorněno v následujícím fragmentu). Konkrétní řetězec používá jako ID není důležité, dokud je jedinečné v projektu.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Pomocí tajné klíče uložené pomocí Správce tajný klíč v aplikaci lze provést voláním AddUserSecrets&lt;T&gt; na instanci ConfigurationBuilder zahrnout tajné klíče pro aplikaci v konfiguraci. Obecný parametr T by měl být typu ze sestavení, které UserSecretId bylo použito pro. Obvykle pomocí AddUserSecrets&lt;spuštění&gt; je v pořádku.


>[!div class="step-by-step"]
[Předchozí] (autorizace net mikroslužeb web-applications.md) [Další] (azure-key trezoru – chrání secrets.md)
