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
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="4e8c1-103">Bezpečné ukládání tajných kódů aplikací během vývoje</span><span class="sxs-lookup"><span data-stu-id="4e8c1-103">Store application secrets safely during development</span></span>

<span data-ttu-id="4e8c1-104">Aby bylo možné se připojit k chráněným prostředkům a dalším službám, aplikace ASP.NET Core obvykle potřebují použít připojovací řetězce, hesla nebo jiné přihlašovací údaje, které obsahují citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="4e8c1-105">Tyto citlivé části informací se nazývají *tajné*kódy.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="4e8c1-106">Osvědčeným postupem je nezahrnovat tajné kódy do zdrojového kódu a zajistit, aby se neukládaly tajné klíče ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="4e8c1-107">Místo toho byste měli použít konfigurační model ASP.NET Core ke čtení tajných kódů z bezpečnějších umístění.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="4e8c1-108">Musíte oddělit tajné klíče pro přístup k vývojovým a pracovním prostředkům z těch, které se používají pro přístup k produkčním prostředkům, protože různí uživatelé budou potřebovat přístup k těmto různým sadám tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="4e8c1-109">Pro ukládání tajných kódů používaných při vývoji se běžně používají k ukládání tajných klíčů do proměnných prostředí nebo pomocí nástroje ASP.NET Core správce tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="4e8c1-110">Pro bezpečnější úložiště v produkčních prostředích můžou mikroslužby ukládat tajné kódy do Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="4e8c1-111">Uložení tajných kódů v proměnných prostředí</span><span class="sxs-lookup"><span data-stu-id="4e8c1-111">Store secrets in environment variables</span></span>

<span data-ttu-id="4e8c1-112">Jedním ze způsobů, jak zachovat tajné klíče ze zdrojového kódu, je vývojářům nastavovat tajné klíče jako [proměnné prostředí](/aspnet/core/security/app-secrets#environment-variables) na svých vývojových počítačích.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="4e8c1-113">Když použijete proměnné prostředí k ukládání tajných kódů s hierarchickými názvy, jako jsou ty, které jsou vnořené v konfiguračních oddílech, musíte proměnné pojmenovat tak, aby zahrnovaly celou hierarchii jeho sekcí, oddělená dvojtečkami (:).</span><span class="sxs-lookup"><span data-stu-id="4e8c1-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="4e8c1-114">Například nastavení proměnné `Logging:LogLevel:Default` prostředí na `Debug` hodnotu by bylo ekvivalentní hodnotě konfigurace z následujícího souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="4e8c1-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="4e8c1-115">Pro přístup k těmto hodnotám z proměnných prostředí musí aplikace při vytváření objektu IConfigurationRoot volat pouze AddEnvironmentVariables na své nerozšiřuje configurationbuilder.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="4e8c1-116">Všimněte si, že proměnné prostředí se běžně ukládají jako prostý text, takže pokud dojde k ohrožení bezpečnosti počítače nebo procesu s proměnnými prostředí, budou se zobrazovat hodnoty proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="4e8c1-117">Uložení tajných kódů pomocí Správce ASP.NET Core tajných klíčů</span><span class="sxs-lookup"><span data-stu-id="4e8c1-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="4e8c1-118">Nástroj ASP.NET Core [správce tajných](/aspnet/core/security/app-secrets#secret-manager) klíčů poskytuje další způsob udržování tajných kódů ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="4e8c1-119">Chcete-li použít nástroj Správce tajných klíčů, nainstalujte balíček **Microsoft. Extensions. Configuration. SecretManager** do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="4e8c1-120">Jakmile je tato závislost přítomna a byla obnovena, `dotnet user-secrets` lze pomocí příkazu nastavit hodnotu tajných kódů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="4e8c1-121">Tyto tajné kódy budou uloženy v souboru JSON v adresáři profilu uživatele (podrobnosti se liší podle operačního systému), a to mimo zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="4e8c1-122">Tajné klíče nastavené nástrojem Správce tajných klíčů jsou uspořádány podle `UserSecretsId` vlastnosti projektu, který používá tajné klíče.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="4e8c1-123">Proto je nutné, abyste nastavili vlastnost UserSecretsId v souboru projektu, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="4e8c1-124">Výchozí hodnota je identifikátor GUID přiřazený aplikací Visual Studio, ale skutečný řetězec není důležitý, pokud je v počítači jedinečný.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="4e8c1-125">Používání tajných klíčů uložených s tajným správcem v aplikaci se provádí `AddUserSecrets<T>` voláním instance nerozšiřuje configurationbuilder, aby zahrnovala tajné klíče pro aplikaci ve své konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="4e8c1-126">Obecný parametr T by měl být typ ze sestavení, na které se UserSecretId použil.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="4e8c1-127">Obvykle je `AddUserSecrets<Startup>` používání velmi přesné.</span><span class="sxs-lookup"><span data-stu-id="4e8c1-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="4e8c1-128">Je součástí výchozích možností pro vývojové prostředí při `CreateDefaultBuilder` použití metody v *program.cs*. `AddUserSecrets<Startup>()`</span><span class="sxs-lookup"><span data-stu-id="4e8c1-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4e8c1-129">[Předchozí](authorization-net-microservices-web-applications.md)Další
>[](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="4e8c1-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
