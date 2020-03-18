---
title: Bezpečné ukládání tajných kódů aplikace během vývoje
description: Zabezpečení v .NET Microservices a webových aplikací - Neukládejte tajné klíče aplikace, jako jsou hesla, připojovací řetězce nebo klíče rozhraní API ve slučování zdrojového kódu, pochopit možnosti, které můžete použít v ASP.NET Core, zejména musíte pochopit, jak zacházet s "uživatel tajemství".
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501789"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="09a48-103">Bezpečné ukládání tajných kódů aplikací během vývoje</span><span class="sxs-lookup"><span data-stu-id="09a48-103">Store application secrets safely during development</span></span>

<span data-ttu-id="09a48-104">Chcete-li se spojit s chráněnými prostředky a dalšími službami, ASP.NET základní aplikace obvykle potřebují používat připojovací řetězce, hesla nebo jiná pověření, která obsahují citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="09a48-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="09a48-105">Tyto citlivé informace se nazývají *tajemství*.</span><span class="sxs-lookup"><span data-stu-id="09a48-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="09a48-106">Je osvědčeným postupem nezahrnovat tajné klíče ve zdrojovém kódu a ujistěte se, že není ukládat tajné klíče ve správě zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="09a48-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="09a48-107">Místo toho byste měli použít model konfigurace ASP.NET Core ke čtení tajných kódů z bezpečnějších umístění.</span><span class="sxs-lookup"><span data-stu-id="09a48-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="09a48-108">Je nutné oddělit tajné klíče pro přístup k vývoji a pracovní prostředky z těch, které se používají pro přístup k produkční prostředky, protože různé osoby budou potřebovat přístup k těmto různým sady tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="09a48-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="09a48-109">Chcete-li uložit tajné klíče používané během vývoje, běžné přístupy jsou buď ukládat tajné kódy v proměnných prostředí nebo pomocí nástroje ASP.NET Core Secret Manager.</span><span class="sxs-lookup"><span data-stu-id="09a48-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="09a48-110">Pro bezpečnější úložiště v produkčním prostředí mikroslužeb můžete ukládat tajné klíče v trezoru klíčů Azure.</span><span class="sxs-lookup"><span data-stu-id="09a48-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="09a48-111">Ukládání tajných kódů v proměnných prostředí</span><span class="sxs-lookup"><span data-stu-id="09a48-111">Store secrets in environment variables</span></span>

<span data-ttu-id="09a48-112">Jedním ze způsobů, jak zachovat tajné kódy mimo zdrojový kód, je pro vývojáře nastavit tajné [kódy](/aspnet/core/security/app-secrets#environment-variables) založené na řetězec jako proměnné prostředí na svých vývojových počítačích.</span><span class="sxs-lookup"><span data-stu-id="09a48-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="09a48-113">Při použití proměnných prostředí k ukládání tajných kódů s hierarchickými názvy, jako jsou ty vnořené v konfiguračních oddílech, je nutné pojmenovat proměnné tak, aby zahrnovaly úplnou hierarchii jejích oddílů, oddělené dvojtečkami (:).</span><span class="sxs-lookup"><span data-stu-id="09a48-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="09a48-114">Například nastavení proměnné `Logging:LogLevel:Default` prostředí `Debug` na hodnotu by bylo ekvivalentní hodnotě konfigurace z následujícího souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="09a48-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="09a48-115">Chcete-li získat přístup k těmto hodnotám z proměnných prostředí, aplikace stačí volat AddEnvironmentVariables na jeho ConfigurationBuilder při vytváření objektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="09a48-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="09a48-116">Všimněte si, že proměnné prostředí jsou běžně uloženy jako prostý text, takže pokud je ohrožen počítač nebo proces s proměnnými prostředí, budou viditelné hodnoty proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="09a48-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="09a48-117">Ukládání tajných kódů pomocí správce tajných klíčů ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="09a48-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="09a48-118">Nástroj ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) poskytuje další způsob, jak uchovávat tajemství mimo zdrojový kód **během vývoje**.</span><span class="sxs-lookup"><span data-stu-id="09a48-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code **during development**.</span></span> <span data-ttu-id="09a48-119">Chcete-li použít nástroj Správce tajných barev, nainstalujte balíček **Microsoft.Extensions.Configuration.SecretManager** do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="09a48-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="09a48-120">Jakmile je tato závislost k dispozici a `dotnet user-secrets` byla obnovena, příkaz lze použít k nastavení hodnoty tajných kódů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="09a48-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="09a48-121">Tyto tajné klíče budou uloženy v souboru JSON v adresáři profilu uživatele (podrobnosti se liší podle operačního systému), mimo zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="09a48-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="09a48-122">Tajné klíče stanovené nástrojem Správce tajných barev jsou uspořádány `UserSecretsId` podle vlastnosti projektu, který používá tajné klíče.</span><span class="sxs-lookup"><span data-stu-id="09a48-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="09a48-123">Proto musíte být jisti, nastavit Vlastnost UserSecretsId v souboru projektu, jak je znázorněno ve výstřižku níže.</span><span class="sxs-lookup"><span data-stu-id="09a48-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="09a48-124">Výchozí hodnota je identifikátor GUID přiřazený visual studio, ale skutečný řetězec není důležité, pokud je jedinečný v počítači.</span><span class="sxs-lookup"><span data-stu-id="09a48-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="09a48-125">Použití tajných klíčů uložených s Správcem `AddUserSecrets<T>` tajných klíčů v aplikaci se provádí voláním instance ConfigurationBuilder tak, aby do své konfigurace zahrnula tajné klíče aplikace.</span><span class="sxs-lookup"><span data-stu-id="09a48-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="09a48-126">Obecný parametr T by měl být typ ze sestavení, které UserSecretId byla použita.</span><span class="sxs-lookup"><span data-stu-id="09a48-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="09a48-127">Obvykle `AddUserSecrets<Startup>` se používá v pořádku.</span><span class="sxs-lookup"><span data-stu-id="09a48-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="09a48-128">Je `AddUserSecrets<Startup>()` součástí výchozích možností pro vývojové prostředí `CreateDefaultBuilder` při použití metody v *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="09a48-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="09a48-129">[Předchozí](authorization-net-microservices-web-applications.md)
>[další](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="09a48-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
