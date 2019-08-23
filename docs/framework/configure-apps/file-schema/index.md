---
title: Schéma konfiguračního souboru pro .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921030"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="36e76-102">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="36e76-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="36e76-103">Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavení zásad pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="36e76-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="36e76-104">Schéma konfigurace .NET Framework se skládá z prvků, které lze použít v konfiguračních souborech pro řízení chování aplikací.</span><span class="sxs-lookup"><span data-stu-id="36e76-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="36e76-105">Obsah této části odráží hierarchii schématu pro spuštění, modul runtime, síť a další typy nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="36e76-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="36e76-106">Informace o typech, formátech a umístění konfiguračních souborů naleznete v článku [Konfigurace aplikací](../index.md).</span><span class="sxs-lookup"><span data-stu-id="36e76-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](../index.md).</span></span> <span data-ttu-id="36e76-107">Pokud chcete upravit konfigurační soubory přímo, Seznamte se s XML.</span><span class="sxs-lookup"><span data-stu-id="36e76-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36e76-108">Značky a atributy XML v konfiguračních souborech rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="36e76-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="36e76-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="36e76-109">In this section</span></span>

<span data-ttu-id="36e76-110">[**element >Konfigurace\<** ](configuration-element.md) `<configuration>` Popisuje element, který je prvkem nejvyšší úrovně pro všechny konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="36e76-110">[**\<configuration>** Element](configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="36e76-111">[assemblyBinding > element určuje zásadu vazby sestavení na úrovni konfigurace.  **\<** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="36e76-111">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="36e76-112">[linkedConfiguration > element určuje konfigurační soubor, který se má zahrnout.  **\<** ](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="36e76-112">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="36e76-113">[Schéma nastavení spouštění](./startup/index.md) Popisuje prvky, které určují, která verze modulu CLR (Common Language Runtime) se má použít.</span><span class="sxs-lookup"><span data-stu-id="36e76-113">[Startup Settings Schema](./startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="36e76-114">[Schéma nastavení modulu runtime](./runtime/index.md) Popisuje prvky, které konfigurují vazby sestavení a chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="36e76-114">[Runtime Settings Schema](./runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="36e76-115">[Schéma nastavení sítě](./network/index.md) Popisuje prvky, které určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="36e76-115">[Network Settings Schema](./network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="36e76-116">[Schéma nastavení kryptografie](./cryptography/index.md) Popisuje prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="36e76-116">[Cryptography Settings Schema](./cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="36e76-117">[Schéma konfiguračních oddílů](configuration-sections-schema.md) Popisuje prvky, které slouží k vytvoření a použití konfiguračních oddílů pro vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="36e76-117">[Configuration Sections Schema](configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="36e76-118">[Nastavení trasování a ladění – schéma](./trace-debug/index.md) Popisuje prvky, které určují přepínače trasování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="36e76-118">[Trace and Debug Settings Schema](./trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="36e76-119">[Schéma nastavení kompilátoru a poskytovatele jazyka](./compiler/index.md) Popisuje prvky, které určují konfiguraci kompilátoru pro poskytovatele dostupných jazyků.</span><span class="sxs-lookup"><span data-stu-id="36e76-119">[Compiler and Language Provider Settings Schema](./compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="36e76-120">[Schéma nastavení aplikace](application-settings-schema.md) Popisuje prvky, které umožňují model Windows Forms nebo ASP.NET aplikaci ukládat a načítat nastavení s rozsahem aplikace a uživatelem.</span><span class="sxs-lookup"><span data-stu-id="36e76-120">[Application Settings Schema](application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="36e76-121">[Schéma nastavení aplikace](./appsettings/index.md) Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="36e76-121">[App Settings Schema](./appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="36e76-122">[Schéma nastavení webu](./web/index.md) Všechny prvky ve schématu nastavení webu, které obsahují prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je služba IIS.</span><span class="sxs-lookup"><span data-stu-id="36e76-122">[Web Settings Schema](./web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="36e76-123">Používá se v souborech *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="36e76-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="36e76-124">[Schéma konfigurace model Windows Forms](winforms/index.md) Všechny prvky v části Konfigurace aplikace model Windows Forms, které zahrnují vlastní nastavení, jako je například podpora více monitorů a vysokého rozlišení DPI.</span><span class="sxs-lookup"><span data-stu-id="36e76-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="36e76-125">[Schéma konfigurace WCF](./wcf/index.md) Všechny prvky, které umožňují konfigurovat službu WCF a klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="36e76-125">[WCF Configuration Schema](./wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="36e76-126">[Syntaxe direktivy WCF](./wcf-directive/index.md) `@ServiceHost` Popisuje direktivu, která definuje atributy specifické pro stránku používané kompilátorem. svc.</span><span class="sxs-lookup"><span data-stu-id="36e76-126">[WCF Directive Syntax](./wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="36e76-127">[Schéma konfigurace WIF](windows-identity-foundation/index.md) Všechny prvky schématu konfigurace Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="36e76-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="36e76-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="36e76-128">Related sections</span></span>

<span data-ttu-id="36e76-129">[Schéma nastavení vzdálené komunikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Popisuje prvky, které konfigurují klientské a serverové aplikace, které implementují vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="36e76-129">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="36e76-130">[Schéma nastavení ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Popisuje prvky, které řídí chování webových aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="36e76-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="36e76-131">[Schéma nastavení webových služeb](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Popisuje prvky, které řídí chování webových služeb ASP.NET a jejich klientů.</span><span class="sxs-lookup"><span data-stu-id="36e76-131">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="36e76-132">[Konfigurace aplikací .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Popisuje postup konfigurace zabezpečení, vazby sestavení a vzdálené komunikace v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36e76-132">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
