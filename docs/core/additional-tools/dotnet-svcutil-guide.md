---
title: Přehled nástroje svcutil WCF
description: Přehled nástroje dotnet svcutil Microsoft WCF, který přidá funkce pro projekty .NET Core a ASP.NET Core, podobný nástroj svcutil WCF pro projekty .NET Framework.
author: mlacouture
ms.date: 08/20/2018
ms.custom: seodec18
ms.openlocfilehash: e42ec0d4072c56456c824a814f1b383ea70a9307
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237256"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="4a179-103">Nástroj dotnet svcutil WCF pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a179-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="4a179-104">Windows Communication Foundation (WCF) **dotnet svcutil** nástroj je nástroj příkazového řádku .NET Core, načte metadata z webové služby v umístění v síti nebo ze souboru WSDL, který generuje WCF třídu obsahující metody proxy serveru klienta, který přístup k operací webové služby.</span><span class="sxs-lookup"><span data-stu-id="4a179-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="4a179-105">Podobně jako [ **metadat modelu služby - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroje pro projekty .NET Framework **dotnet svcutil** je nástroj příkazového řádku pro generování odkaz webové služby kompatibilní s projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4a179-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="4a179-106">**Dotnet svcutil** alternativní možnost je nástroj [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) sady Visual Studio zprostředkovatel připojené služby, která se poprvé dodáváno pomocí sady Visual Studio 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="4a179-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="4a179-107">**Dotnet svcutil** nástroj jako nástroj příkazového řádku .NET Core, je k dispozici na různých platformách Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="4a179-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a179-108">Služby by měly odkazovat pouze z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="4a179-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="4a179-109">Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4a179-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a179-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a179-110">Prerequisites</span></span>

* <span data-ttu-id="4a179-111">[Sada .NET core SDK](https://dotnet.microsoft.com/download) verzi v1.0.4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="4a179-111">[.NET Core SDK](https://dotnet.microsoft.com/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="4a179-112">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="4a179-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="4a179-113">Začínáme</span><span class="sxs-lookup"><span data-stu-id="4a179-113">Getting started</span></span>

<span data-ttu-id="4a179-114">Následující příklad vás provede kroky potřebné k přidání odkaz webové služby na projekt konzoly .NET Core a vyvolat službu.</span><span class="sxs-lookup"><span data-stu-id="4a179-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="4a179-115">Vytvoříte konzolovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidá odkaz na webovou službu, která implementuje kontrakt následující:</span><span class="sxs-lookup"><span data-stu-id="4a179-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="4a179-116">V tomto příkladu bude považovat za webové službě hostované na následující adrese: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="4a179-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="4a179-117">Z příkazového okna Windows, macOS nebo Linux postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="4a179-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="4a179-118">Vytvořte adresář _HelloSvcutil_ pro váš projekt a nastavte ji váš aktuální adresář, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4a179-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="4a179-119">Vytvořte nový projekt konzoly C# v tomto adresáři pomocí [ `dotnet new` ](../tools/dotnet-new.md) takto:</span><span class="sxs-lookup"><span data-stu-id="4a179-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="4a179-120">Otevřít `HelloSvcutil.csproj` souboru v editoru projektu, upravit `Project` prvek a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na rozhraní příkazového řádku nástroje, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="4a179-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. <span data-ttu-id="4a179-121">Obnovit _dotnet svcutil_ balíček pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:</span><span class="sxs-lookup"><span data-stu-id="4a179-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="4a179-122">Spustit _dotnet_ s _svcutil_ příkazu vygenerujte soubor odkaz webové služby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4a179-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="4a179-123">Vygenerovaný soubor je uložen jako _HelloSvcutil/ServiceReference1/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="4a179-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="4a179-124">_Dotnet_svcutil_ nástroj také přidá do projektu odpovídající balíčky WCF vyžaduje proxy kód jako odkazy na balíček.</span><span class="sxs-lookup"><span data-stu-id="4a179-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="4a179-125">Obnovení balíčků WCF pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:</span><span class="sxs-lookup"><span data-stu-id="4a179-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="4a179-126">Otevřít `Program.cs` souboru v editoru, upravit `Main()` metoda a nahradit automaticky generovaný kód následujícím kódem, abyste mohli vyvolat službu web:</span><span class="sxs-lookup"><span data-stu-id="4a179-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="4a179-127">Spuštění aplikace pomocí [ `dotnet run` ](../tools/dotnet-run.md) takto:</span><span class="sxs-lookup"><span data-stu-id="4a179-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="4a179-128">Byste měli vidět následující výstup: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="4a179-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="4a179-129">Podrobný popis `dotnet-svcutil` nástroj parametry, vyvolají nástroj předávání parametru nápovědy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4a179-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="4a179-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4a179-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="4a179-131">Zpětná vazba a otázky</span><span class="sxs-lookup"><span data-stu-id="4a179-131">Feedback & questions</span></span>

<span data-ttu-id="4a179-132">Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="4a179-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="4a179-133">Můžete také zkontrolovat všechny stávající dotazy nebo potíže [v WCF úložišti na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="4a179-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="4a179-134">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="4a179-134">Release notes</span></span>

* <span data-ttu-id="4a179-135">Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) aktualizovanou verzi informace, včetně známých problémů.</span><span class="sxs-lookup"><span data-stu-id="4a179-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="4a179-136">Informace o</span><span class="sxs-lookup"><span data-stu-id="4a179-136">Information</span></span>

* [<span data-ttu-id="4a179-137">Balíček NuGet DotNet svcutil</span><span class="sxs-lookup"><span data-stu-id="4a179-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
