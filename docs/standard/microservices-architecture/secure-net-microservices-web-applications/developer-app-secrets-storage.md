---
title: Ukládání tajné klíče aplikace bezpečně během vývoje
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Ukládání tajné klíče aplikace bezpečně během vývoje
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 560120db35ae190bdef1f95d72ac1e5de697124e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105943"
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="f98d7-103">Ukládání tajné klíče aplikace bezpečně během vývoje</span><span class="sxs-lookup"><span data-stu-id="f98d7-103">Storing application secrets safely during development</span></span>

<span data-ttu-id="f98d7-104">Pro připojení k chráněným prostředkům a další služby, aplikace ASP.NET Core obvykle nutné použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="f98d7-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="f98d7-105">Tyto důvěrné údaje se nazývají *tajné klíče*.</span><span class="sxs-lookup"><span data-stu-id="f98d7-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="f98d7-106">Je osvědčeným postupem tak, aby neobsahoval tajné klíče ve zdrojovém kódu a určitě nechcete ukládat tajné klíče ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f98d7-106">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="f98d7-107">Místo toho používejte konfigurační model ASP.NET Core čtení těchto tajných klíčů z více zabezpečeného umístění.</span><span class="sxs-lookup"><span data-stu-id="f98d7-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="f98d7-108">Je vhodné oddělit tajné klíče pro přístup k vývoji a pracovní prostředky z těch, které používá pro přístup k prostředkům produkční, protože různí jednotlivci budete potřebovat přístup k tyto různé sady tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="f98d7-108">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="f98d7-109">K uložení použít během vývoje tajné klíče, jsou běžné přístupy buď ukládat tajné klíče v seznamu proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč.</span><span class="sxs-lookup"><span data-stu-id="f98d7-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="f98d7-110">Pro bezpečnější úložiště v produkčním prostředí může mikroslužeb ukládat tajné klíče v Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f98d7-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="f98d7-111">Ukládání tajné klíče v seznamu proměnných prostředí</span><span class="sxs-lookup"><span data-stu-id="f98d7-111">Storing secrets in environment variables</span></span>

<span data-ttu-id="f98d7-112">Je možné zachovat tajné klíče ze zdrojového kódu pro vývojáře k nastavení založené na řetězcích tajné klíče jako [proměnné prostředí](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na jejich vývoj počítačů.</span><span class="sxs-lookup"><span data-stu-id="f98d7-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="f98d7-113">Při použití proměnných prostředí pro ukládání tajných klíčů s hierarchické názvy (ty vnořené v oddílech konfigurace), vytvořte název pro objekt environment variables, který obsahuje úplnou hierarchii název tajného klíče, oddělený dvojtečky (:).</span><span class="sxs-lookup"><span data-stu-id="f98d7-113">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="f98d7-114">Například nastavením proměnné prostředí protokolování: LogLevel:Default na ladění by ekvivalentní na hodnotu konfigurace z následujícího souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="f98d7-114">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="f98d7-115">K tyto hodnoty z proměnných prostředí aplikace právě musí volat AddEnvironmentVariables jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="f98d7-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="f98d7-116">Všimněte si, že proměnné prostředí jsou obecně uložené jako prostý text, takže pokud k počítači nebo proces s proměnné prostředí dojde k narušení, se nebude zobrazovat hodnoty proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="f98d7-116">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="f98d7-117">Ukládání tajné klíče pomocí Správce technologie ASP.NET Core tajný klíč</span><span class="sxs-lookup"><span data-stu-id="f98d7-117">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="f98d7-118">ASP.NET Core [tajný klíč správce](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajné klíče ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f98d7-118">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="f98d7-119">Použití nástroje Správce tajný klíč, obsahovat odkaz nástroje (DotNetCliToolReference) k Microsoft.Extensions.SecretManager.Tools balíčku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f98d7-119">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="f98d7-120">Po této závislostí je k dispozici a byla obnovena, příkaz uživatele tajemství dotnet. lze použít k nastavení hodnoty tajných údajů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f98d7-120">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="f98d7-121">Tato tajná data se uloží do souboru JSON v profilu adresáře uživatele (podrobnosti se liší podle operačního systému), od zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f98d7-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="f98d7-122">Tajné klíče, která nastavuje nástroj Správce tajný klíč jsou uspořádány UserSecretsId vlastností projektu, který používá těchto tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="f98d7-122">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="f98d7-123">Proto musí být nastavte vlastnost UserSecretsId v souboru projektu (jak je znázorněno v následujícím fragmentu).</span><span class="sxs-lookup"><span data-stu-id="f98d7-123">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="f98d7-124">Konkrétní řetězec používá jako ID není důležité, dokud je jedinečné v projektu.</span><span class="sxs-lookup"><span data-stu-id="f98d7-124">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="f98d7-125">Pomocí tajné klíče uložené pomocí Správce tajný klíč v aplikaci lze provést voláním AddUserSecrets&lt;T&gt; na instanci ConfigurationBuilder zahrnout tajné klíče pro aplikaci v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f98d7-125">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="f98d7-126">Obecný parametr T by měl být typu ze sestavení, které UserSecretId bylo použito pro.</span><span class="sxs-lookup"><span data-stu-id="f98d7-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="f98d7-127">Obvykle pomocí AddUserSecrets&lt;spuštění&gt; je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="f98d7-127">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f98d7-128">[Předchozí](authorization-net-microservices-web-applications.md)
[další](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="f98d7-128">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
