---
title: "Ukládání tajné klíče aplikace bezpečně během vývoje"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Ukládání tajné klíče aplikace bezpečně během vývoje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f70f7c741da9653745e4f542125986c701b5d22d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="5f448-104">Ukládání tajné klíče aplikace bezpečně během vývoje</span><span class="sxs-lookup"><span data-stu-id="5f448-104">Storing application secrets safely during development</span></span>

<span data-ttu-id="5f448-105">Pro připojení k chráněným prostředkům a další služby, aplikace ASP.NET Core obvykle nutné použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="5f448-105">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="5f448-106">Tyto důvěrné údaje se nazývají *tajné klíče*.</span><span class="sxs-lookup"><span data-stu-id="5f448-106">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="5f448-107">Je osvědčeným postupem tak, aby neobsahoval tajné klíče ve zdrojovém kódu a určitě nechcete ukládat tajné klíče ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5f448-107">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="5f448-108">Místo toho používejte konfigurační model ASP.NET Core čtení těchto tajných klíčů z více zabezpečeného umístění.</span><span class="sxs-lookup"><span data-stu-id="5f448-108">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="5f448-109">Je vhodné oddělit tajné klíče pro přístup k vývoji a pracovní prostředky z těch, které používá pro přístup k prostředkům produkční, protože různí jednotlivci budete potřebovat přístup k tyto různé sady tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="5f448-109">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="5f448-110">K uložení použít během vývoje tajné klíče, jsou běžné přístupy buď ukládat tajné klíče v seznamu proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč.</span><span class="sxs-lookup"><span data-stu-id="5f448-110">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="5f448-111">Pro bezpečnější úložiště v produkčním prostředí může mikroslužeb ukládat tajné klíče v Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="5f448-111">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="5f448-112">Ukládání tajné klíče v seznamu proměnných prostředí</span><span class="sxs-lookup"><span data-stu-id="5f448-112">Storing secrets in environment variables</span></span>

<span data-ttu-id="5f448-113">Je možné zachovat tajné klíče ze zdrojového kódu pro vývojáře k nastavení založené na řetězcích tajné klíče jako [proměnné prostředí](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na jejich vývoj počítačů.</span><span class="sxs-lookup"><span data-stu-id="5f448-113">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="5f448-114">Při použití proměnných prostředí pro ukládání tajných klíčů s hierarchické názvy (ty vnořené v oddílech konfigurace), vytvořte název pro objekt environment variables, který obsahuje úplnou hierarchii název tajného klíče, oddělený dvojtečky (:).</span><span class="sxs-lookup"><span data-stu-id="5f448-114">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="5f448-115">Například nastavením proměnné prostředí protokolování: LogLevel:Default na ladění by ekvivalentní na hodnotu konfigurace z následujícího souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="5f448-115">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="5f448-116">K tyto hodnoty z proměnných prostředí aplikace právě musí volat AddEnvironmentVariables jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="5f448-116">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="5f448-117">Všimněte si, že proměnné prostředí jsou obecně uložené jako prostý text, takže pokud k počítači nebo proces s proměnné prostředí dojde k narušení, se nebude zobrazovat hodnoty proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="5f448-117">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="5f448-118">Ukládání tajné klíče pomocí Správce technologie ASP.NET Core tajný klíč</span><span class="sxs-lookup"><span data-stu-id="5f448-118">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="5f448-119">ASP.NET Core [tajný klíč správce](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajné klíče ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5f448-119">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="5f448-120">Použití nástroje Správce tajný klíč, obsahovat odkaz nástroje (DotNetCliToolReference) k Microsoft.Extensions.SecretManager.Tools balíčku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="5f448-120">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="5f448-121">Po této závislostí je k dispozici a byla obnovena, příkaz uživatele tajemství dotnet. lze použít k nastavení hodnoty tajných údajů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5f448-121">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="5f448-122">Tato tajná data se uloží do souboru JSON v profilu adresáře uživatele (podrobnosti se liší podle operačního systému), od zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5f448-122">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="5f448-123">Tajné klíče, která nastavuje nástroj Správce tajný klíč jsou uspořádány UserSecretsId vlastností projektu, který používá těchto tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="5f448-123">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="5f448-124">Proto musí být nastavte vlastnost UserSecretsId v souboru projektu (jak je znázorněno v následujícím fragmentu).</span><span class="sxs-lookup"><span data-stu-id="5f448-124">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="5f448-125">Konkrétní řetězec používá jako ID není důležité, dokud je jedinečné v projektu.</span><span class="sxs-lookup"><span data-stu-id="5f448-125">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="5f448-126">Pomocí tajné klíče uložené pomocí Správce tajný klíč v aplikaci lze provést voláním AddUserSecrets&lt;T&gt; na instanci ConfigurationBuilder zahrnout tajné klíče pro aplikaci v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5f448-126">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="5f448-127">Obecný parametr T by měl být typu ze sestavení, které UserSecretId bylo použito pro.</span><span class="sxs-lookup"><span data-stu-id="5f448-127">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="5f448-128">Obvykle pomocí AddUserSecrets&lt;spuštění&gt; je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="5f448-128">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5f448-129">[Předchozí] (autorizace net mikroslužeb web-applications.md) [Další] (azure-key trezoru – chrání secrets.md)</span><span class="sxs-lookup"><span data-stu-id="5f448-129">[Previous] (authorization-net-microservices-web-applications.md) [Next] (azure-key-vault-protects-secrets.md)</span></span>
