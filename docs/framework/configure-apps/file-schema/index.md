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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039163"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="62502-102">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62502-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="62502-103">Konfigurační soubory jsou standardní soubory XML, které můžete použít ke změně nastavení a nastavení zásad pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="62502-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="62502-104">Schéma konfigurace .NET Framework se skládá z prvků, které lze použít v konfiguračních souborech pro řízení chování aplikací.</span><span class="sxs-lookup"><span data-stu-id="62502-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="62502-105">Obsah této části odráží hierarchii schématu pro spuštění, modul runtime, síť a další typy nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="62502-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="62502-106">Informace o typech, formátech a umístění konfiguračních souborů najdete v tématu [Konfigurace aplikací](../index.md).</span><span class="sxs-lookup"><span data-stu-id="62502-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="62502-107">Pokud chcete upravit konfigurační soubory přímo, Seznamte se s XML.</span><span class="sxs-lookup"><span data-stu-id="62502-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62502-108">Značky a atributy XML v konfiguračních souborech rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="62502-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="62502-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="62502-109">In this section</span></span>

<span data-ttu-id="62502-110">[ **\<> elementu konfigurace** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62502-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="62502-111">Element nejvyšší úrovně pro všechny konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="62502-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="62502-112">[ **\<element > assemblyBinding** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="62502-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="62502-113">Určuje zásadu vazby sestavení na úrovni konfigurace.</span><span class="sxs-lookup"><span data-stu-id="62502-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="62502-114">[ **\<element > linkedConfiguration** ](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62502-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="62502-115">Určuje konfigurační soubor, který se má zahrnout.</span><span class="sxs-lookup"><span data-stu-id="62502-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="62502-116">\ [schématu nastavení spuštění](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-116">[Startup Settings Schema](./startup/index.md)\</span></span>
<span data-ttu-id="62502-117">Prvky, které určují, která verze modulu CLR (Common Language Runtime) se má použít.</span><span class="sxs-lookup"><span data-stu-id="62502-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="62502-118">\ [schématu nastavení modulu runtime](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-118">[Runtime Settings Schema](./runtime/index.md)\</span></span>
<span data-ttu-id="62502-119">Prvky, které konfigurují vazby sestavení a běhové chování.</span><span class="sxs-lookup"><span data-stu-id="62502-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="62502-120">\ [schématu nastavení sítě](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-120">[Network Settings Schema](./network/index.md)\</span></span>
<span data-ttu-id="62502-121">Prvky, které určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="62502-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="62502-122">[Nastavení kryptografie\ schématu](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-122">[Cryptography Settings Schema](./cryptography/index.md)\</span></span>
<span data-ttu-id="62502-123">Prvky, které mapují popisné názvy algoritmů na třídy, které implementují kryptografické algoritmy.</span><span class="sxs-lookup"><span data-stu-id="62502-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="62502-124">\ [schématu konfiguračních oddílů](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="62502-124">[Configuration Sections Schema](configuration-sections-schema.md)\</span></span>
<span data-ttu-id="62502-125">Prvky, které slouží k vytváření a používání konfiguračních oddílů pro vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="62502-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="62502-126">\ [schématu nastavení trasování a ladění](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-126">[Trace and Debug Settings Schema](./trace-debug/index.md)\</span></span>
<span data-ttu-id="62502-127">Prvky, které určují přepínače trasování a naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="62502-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="62502-128">\ [schématu nastavení kompilátoru a poskytovatele jazyka](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)\</span></span>
<span data-ttu-id="62502-129">Prvky, které určují konfiguraci kompilátoru pro poskytovatele dostupných jazyků.</span><span class="sxs-lookup"><span data-stu-id="62502-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="62502-130">\ [schématu nastavení aplikace](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="62502-130">[Application Settings Schema](application-settings-schema.md)\</span></span>
<span data-ttu-id="62502-131">Prvky, které umožňují model Windows Forms nebo ASP.NET aplikaci ukládat a načítat nastavení s rozsahem aplikace a uživatelem.</span><span class="sxs-lookup"><span data-stu-id="62502-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="62502-132">\ [schématu nastavení aplikace](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-132">[App Settings Schema](./appsettings/index.md)\</span></span>
<span data-ttu-id="62502-133">Obsahuje vlastní nastavení aplikace, například cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="62502-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="62502-134">\ [schématu webového nastavení](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-134">[Web Settings Schema](./web/index.md)\</span></span>
<span data-ttu-id="62502-135">Prvky pro konfiguraci způsobu, jakým ASP.NET pracuje s hostitelskou aplikací, jako je IIS.</span><span class="sxs-lookup"><span data-stu-id="62502-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="62502-136">Používá se v souborech *ASPNET. config* .</span><span class="sxs-lookup"><span data-stu-id="62502-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="62502-137">\ [schématu konfigurace model Windows Forms](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-137">[Windows Forms Configuration Schema](winforms/index.md)\</span></span>
<span data-ttu-id="62502-138">Všechny prvky v části Konfigurace aplikace model Windows Forms, které zahrnují přizpůsobení, jako je například podpora více monitorů a vysokého rozlišení DPI.</span><span class="sxs-lookup"><span data-stu-id="62502-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="62502-139">\ [schématu konfigurace WCF](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-139">[WCF Configuration Schema](./wcf/index.md)\</span></span>
<span data-ttu-id="62502-140">Všechny prvky, které umožňují konfigurovat službu WCF a klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="62502-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="62502-141">\ [syntaxe direktiv WCF](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-141">[WCF Directive Syntax](./wcf-directive/index.md)\</span></span>
<span data-ttu-id="62502-142">Popisuje direktivu `@ServiceHost`, která definuje atributy specifické pro stránku používané kompilátorem. svc.</span><span class="sxs-lookup"><span data-stu-id="62502-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="62502-143">\ [schématu konfigurace WIF](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="62502-143">[WIF Configuration Schema](windows-identity-foundation/index.md)\</span></span>
<span data-ttu-id="62502-144">Všechny prvky schématu konfigurace Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="62502-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="62502-145">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="62502-145">Related sections</span></span>

<span data-ttu-id="62502-146">[Nastavení vzdálené komunikace\ schématu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62502-146">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\</span></span>
<span data-ttu-id="62502-147">Popisuje prvky, které konfigurují klientské a serverové aplikace, které implementují vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="62502-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="62502-148">\ [schématu nastavení ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62502-148">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\</span></span>
<span data-ttu-id="62502-149">Popisuje prvky, které řídí chování webových aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="62502-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="62502-150">\ [schématu nastavení webových služeb](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62502-150">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\</span></span>
<span data-ttu-id="62502-151">Popisuje prvky, které řídí chování webových služeb ASP.NET a jejich klientů.</span><span class="sxs-lookup"><span data-stu-id="62502-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="62502-152">[Konfigurace aplikací .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62502-152">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="62502-153">Popisuje postup konfigurace zabezpečení, vazby sestavení a vzdálené komunikace v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62502-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
