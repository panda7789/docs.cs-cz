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
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="ba7eb-103">Bezpečné ukládání tajných kódů aplikace během vývoje.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-103">Storing application secrets safely during development</span></span>

<span data-ttu-id="ba7eb-104">Pro připojení k chráněným prostředkům a dalších služeb, aplikací ASP.NET Core obvykle třeba použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="ba7eb-105">Tyto citlivé údaje, se nazývají *tajných kódů*.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="ba7eb-106">Je osvědčeným postupem tak, aby nezahrnovala tajné kódy ve zdrojovém kódu a určitě ne k uložení tajných kódů ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-106">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="ba7eb-107">Místo toho měli používat ASP.NET Core konfigurační model čtení tajné klíče z více zabezpečených umístěních.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="ba7eb-108">Je vhodné oddělit tajné klíče pro přístup k vývoje a pracovním prostředkům se používají pro přístup k produkční prostředky, protože různí jednotlivci bude potřebovat přístup k tyto různé sady tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-108">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="ba7eb-109">Běžné přístupy k ukládání tajných klíčů během vývoje použít, se buď tajné kódy ukládat v proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="ba7eb-110">Pro úložiště bezpečnější v produkčním prostředí mikroslužby tajné kódy ukládat v Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="ba7eb-111">Ukládání tajných kódů v proměnných prostředí</span><span class="sxs-lookup"><span data-stu-id="ba7eb-111">Storing secrets in environment variables</span></span>

<span data-ttu-id="ba7eb-112">Jeden způsob, jak uchovávat tajemství zdrojový kód je pro vývojáře k nastavení založené na řetězci tajné kódy jako [proměnné prostředí](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na svých počítačích vývojářů.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="ba7eb-113">Při použití proměnných prostředí pro uložení tajných kódů pomocí hierarchických názvy (ty vnořené v oddílech konfigurace), vytvořte název proměnné prostředí, která zahrnuje hierarchii úplný název tajného klíče odděleny dvojtečkou (:).</span><span class="sxs-lookup"><span data-stu-id="ba7eb-113">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="ba7eb-114">Například nastavením proměnné prostředí protokolování: LogLevel:Default ladění by ekvivalentní hodnotu konfigurace z následujícího souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="ba7eb-114">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="ba7eb-115">Pro přístup k tyto hodnoty z proměnných prostředí, potřebuje aplikace právě volat AddEnvironmentVariables jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="ba7eb-116">Všimněte si, že proměnné prostředí jsou obvykle uložené jako prostý text, takže pokud počítači nebo procesu s proměnnými prostředí dojde k ohrožení, hodnoty proměnné prostředí se nebude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-116">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="ba7eb-117">Ukládání tajných kódů pomocí manažera tajných ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba7eb-117">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="ba7eb-118">ASP.NET Core [manažera tajných](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajných kódů ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-118">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="ba7eb-119">Použití nástroje Správce tajný klíč, obsahuje odkaz nástroje (DotNetCliToolReference) Microsoft.Extensions.SecretManager.Tools balíčku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-119">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="ba7eb-120">Jakmile dané závislosti je k dispozici a byla obnovena, příkaz dotnet tajných kódů uživatelů slouží k nastavení hodnoty tajných kódů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-120">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="ba7eb-121">Těchto tajných kódů se uloží do souboru JSON v uživatele adresář profilu (podrobnosti se liší podle operačního systému), od zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="ba7eb-122">Nastavit pomocí nástroje Správce tajný klíč tajné kódy jsou uspořádané podle UserSecretsId vlastnosti projektu, který je použití tajné klíče.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-122">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="ba7eb-123">Proto musí být potřeba nastavit vlastnost UserSecretsId v souboru projektu (jak je znázorněno v následujícím fragmentu kódu).</span><span class="sxs-lookup"><span data-stu-id="ba7eb-123">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="ba7eb-124">Skutečné řetězec použitý jako ID není důležité, jako je jedinečný v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-124">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="ba7eb-125">Tajnými kódy uloženými v aplikaci pomocí manažera tajných pomocí provádí volání AddUserSecrets&lt;T&gt; na instanci ConfigurationBuilder zahrnovat tajné kódy pro aplikaci v jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-125">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="ba7eb-126">Obecný parametr T musí být typu ze sestavení, které byly použity UserSecretId k.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="ba7eb-127">Obvykle pomocí AddUserSecrets&lt;spuštění&gt; je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="ba7eb-127">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
><span data-ttu-id="ba7eb-128">[Předchozí](authorization-net-microservices-web-applications.md)
>[další](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="ba7eb-128">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>