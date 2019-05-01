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
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="90567-103">Bezpečně Store tajných kódů aplikace během vývoje.</span><span class="sxs-lookup"><span data-stu-id="90567-103">Store application secrets safely during development</span></span>

<span data-ttu-id="90567-104">Pro připojení k chráněným prostředkům a dalších služeb, aplikací ASP.NET Core obvykle třeba použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="90567-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="90567-105">Tyto citlivé údaje, se nazývají *tajných kódů*.</span><span class="sxs-lookup"><span data-stu-id="90567-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="90567-106">Je osvědčeným postupem tak, aby nezahrnovala tajné kódy ve zdrojovém kódu a nezapomeňte ukládat tajné kódy ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="90567-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="90567-107">Místo toho měli používat ASP.NET Core konfigurační model čtení tajné klíče z více zabezpečených umístěních.</span><span class="sxs-lookup"><span data-stu-id="90567-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="90567-108">Je třeba oddělit tajné klíče pro přístup k vývoje a pracovním prostředkům z ty, které slouží pro přístup k produkční prostředky, protože různí jednotlivci bude potřebovat přístup k tyto různé sady tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="90567-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="90567-109">Běžné přístupy k ukládání tajných klíčů během vývoje použít, se buď tajné kódy ukládat v proměnných prostředí, nebo pomocí nástroje Správce technologie ASP.NET Core tajný klíč.</span><span class="sxs-lookup"><span data-stu-id="90567-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="90567-110">Pro úložiště bezpečnější v produkčním prostředí mikroslužby tajné kódy ukládat v Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="90567-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="90567-111">Store tajných kódů v proměnných prostředí</span><span class="sxs-lookup"><span data-stu-id="90567-111">Store secrets in environment variables</span></span>

<span data-ttu-id="90567-112">Jeden způsob, jak uchovávat tajemství zdrojový kód je pro vývojáře k nastavení založené na řetězci tajné kódy jako [proměnné prostředí](/aspnet/core/security/app-secrets#environment-variables) na svých počítačích vývojářů.</span><span class="sxs-lookup"><span data-stu-id="90567-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="90567-113">Při použití proměnných prostředí pro ukládání tajných kódů pomocí hierarchických názvy, například těch, které jsou vnořené v oddílech konfigurace, je nutné pojmenovat proměnné k zahrnutí úplné hierarchie její části oddělené znakem dvojtečky (:).</span><span class="sxs-lookup"><span data-stu-id="90567-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="90567-114">Například nastavením proměnné prostředí `Logging:LogLevel:Default` k `Debug` hodnota bude ekvivalentní hodnotu konfigurace z následujícího souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="90567-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="90567-115">Pro přístup k tyto hodnoty z proměnných prostředí, potřebuje aplikace právě volat AddEnvironmentVariables jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="90567-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="90567-116">Všimněte si, že proměnné prostředí jsou obvykle uložené jako prostý text, takže pokud počítači nebo procesu s proměnnými prostředí dojde k ohrožení, hodnoty proměnné prostředí se nebude zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="90567-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="90567-117">Store tajných kódů pomocí manažera tajných základní technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="90567-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="90567-118">ASP.NET Core [manažera tajných](/aspnet/core/security/app-secrets#secret-manager) nástroj poskytuje jinou metodu zachování tajných kódů ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="90567-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="90567-119">Chcete-li pomocí nástroje Správce tajný klíč, nainstalujte balíček **Microsoft.Extensions.Configuration.SecretManager** v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="90567-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="90567-120">Jakmile je k dispozici dané závislosti a byla obnovena, `dotnet user-secrets` příkaz lze použít k nastavení hodnoty tajných kódů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="90567-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="90567-121">Těchto tajných kódů se uloží do souboru JSON v uživatele adresář profilu (podrobnosti se liší podle operačního systému), od zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="90567-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="90567-122">Nastavit pomocí nástroje Správce tajný klíč tajné kódy jsou uspořádané podle `UserSecretsId` vlastnosti projektu, který je použití tajné klíče.</span><span class="sxs-lookup"><span data-stu-id="90567-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="90567-123">Proto musíte být potřeba nastavit vlastnost UserSecretsId v souboru projektu, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="90567-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="90567-124">Výchozí hodnota je identifikátor GUID přidělený pomocí sady Visual Studio, ale aktuální řetězcovou není důležité, dokud bude jednoznačný ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="90567-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="90567-125">Tajnými kódy uloženými v aplikaci pomocí manažera tajných pomocí provádí volání `AddUserSecrets<T>` na instanci ConfigurationBuilder zahrnovat tajné kódy pro aplikaci v jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="90567-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="90567-126">Obecný parametr T musí být typu ze sestavení, které byly použity UserSecretId k.</span><span class="sxs-lookup"><span data-stu-id="90567-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="90567-127">Obvykle pomocí `AddUserSecrets<Startup>` je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="90567-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="90567-128">`AddUserSecrets<Startup>()` Je součástí výchozí možnosti pro vývojové prostředí při použití `CreateDefaultBuilder` metoda *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="90567-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="90567-129">[Předchozí](authorization-net-microservices-web-applications.md)
>[další](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="90567-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
