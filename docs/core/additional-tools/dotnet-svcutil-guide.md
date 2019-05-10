---
title: Přehled nástroje svcutil WCF
description: Přehled nástroje dotnet svcutil Microsoft WCF, který přidá funkce pro projekty .NET Core a ASP.NET Core, podobný nástroj svcutil WCF pro projekty .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 5e361ce85bec696fe5d76c4f43a444c543a9012d
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063296"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="f0e4b-103">Nástroj dotnet svcutil WCF pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="f0e4b-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="f0e4b-104">Windows Communication Foundation (WCF) **dotnet svcutil** nástroj je nástroj příkazového řádku .NET Core, načte metadata z webové služby v umístění v síti nebo ze souboru WSDL, který generuje WCF třídu obsahující metody proxy serveru klienta, který přístup k operací webové služby.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="f0e4b-105">Podobně jako [ **metadat modelu služby - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroje pro projekty .NET Framework **dotnet svcutil** je nástroj příkazového řádku pro generování odkaz webové služby kompatibilní s projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="f0e4b-106">**Dotnet svcutil** alternativní možnost je nástroj [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) sady Visual Studio zprostředkovatel připojené služby, která se poprvé dodáváno pomocí sady Visual Studio 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="f0e4b-107">**Dotnet svcutil** nástroj jako nástroj příkazového řádku .NET Core, je k dispozici na různých platformách Windows, Linux a macOS.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0e4b-108">Služby by měly odkazovat pouze z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="f0e4b-109">Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0e4b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0e4b-110">Prerequisites</span></span>

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="f0e4b-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)
* <span data-ttu-id="f0e4b-112">[Sady SDK .NET core 2.1](https://dotnet.microsoft.com/download) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="f0e4b-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="f0e4b-113">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="f0e4b-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="f0e4b-114">DotNet – svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
* <span data-ttu-id="f0e4b-115">[.NET core 1.0.4 SDK](https://dotnet.microsoft.com/download) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="f0e4b-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="f0e4b-116">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="f0e4b-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="f0e4b-117">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f0e4b-117">Getting started</span></span>

<span data-ttu-id="f0e4b-118">Následující příklad vás provede kroky potřebné k přidání odkaz webové služby do webového projektu .NET Core a vyvolat službu.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="f0e4b-119">Vytvoříte webovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidejte odkaz na webovou službu, která implementuje kontrakt následující:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="f0e4b-120">V tomto příkladu předpokládejme, že webová služba bude možné hostovat na následující adrese: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="f0e4b-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="f0e4b-121">Z příkazového okna Windows, macOS nebo Linux postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="f0e4b-122">Vytvořte adresář _HelloSvcutil_ pro váš projekt a nastavte ji váš aktuální adresář, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="f0e4b-123">Vytvořte nový C# webový projekt v tomto adresáři pomocí [ `dotnet new` ](../tools/dotnet-new.md) takto:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```console
    dotnet new web
    ```

3. <span data-ttu-id="f0e4b-124">Nainstalujte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako nástroj příkazového řádku:  </span><span class="sxs-lookup"><span data-stu-id="f0e4b-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="f0e4b-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="f0e4b-126">DotNet – svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="f0e4b-127">Otevřít `HelloSvcutil.csproj` souboru v editoru projektu, upravit `Project` prvek a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na rozhraní příkazového řádku nástroje, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="f0e4b-128">Obnovte _dotnet svcutil_ balíček pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

    ---

4. <span data-ttu-id="f0e4b-129">Spustit _dotnet svcutil_ příkazu vygenerujte soubor odkaz webové služby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="f0e4b-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="f0e4b-131">DotNet – svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="f0e4b-132">Vygenerovaný soubor je uložen jako _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="f0e4b-133">_Dotnet svcutil_ nástroj také přidá do projektu odpovídající balíčky WCF vyžaduje proxy kód jako odkazy na balíček.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="f0e4b-134">Pomocí odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="f0e4b-134">Using the Service Reference</span></span>

1. <span data-ttu-id="f0e4b-135">Obnovení balíčků WCF pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

2. <span data-ttu-id="f0e4b-136">Vyhledejte název klienta, třídy a operace, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="f0e4b-137">`Reference.cs` bude obsahovat třídu, která dědí z `System.ServiceModel.ClientBase`, metodami, které slouží k volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="f0e4b-138">V tomto příkladu chcete volat _SayHello_ služby _Hello_ operace.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="f0e4b-139">`ServiceReference.SayHelloClient` je název třídy klienta a je volána metoda `HelloAsync` , který je možné volat operaci.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="f0e4b-140">Otevřít `Startup.cs` souboru ve svém editoru a přidejte sadu pomocí příkazu pro obor názvů odkazu služby v horní části:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="f0e4b-141">Upravit `Configure` metoda k vyvolání webové služby.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="f0e4b-142">To provedete tak, že vytvoříte instanci, která dědí z třídy `ClientBase` a volání metody u objektu klienta:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. <span data-ttu-id="f0e4b-143">Spuštění aplikace pomocí [ `dotnet run` ](../tools/dotnet-run.md) takto:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```console
    dotnet run
    ```

6. <span data-ttu-id="f0e4b-144">Přejděte na adresu URL uvedená v konzole (například `http://localhost:5000`) ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="f0e4b-145">Byste měli vidět následující výstup: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="f0e4b-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="f0e4b-146">Podrobný popis `dotnet-svcutil` nástroj parametry, vyvolají nástroj předávání parametru nápovědy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f0e4b-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="f0e4b-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="f0e4b-148">DotNet – svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="f0e4b-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="f0e4b-149">Zpětná vazba a otázky</span><span class="sxs-lookup"><span data-stu-id="f0e4b-149">Feedback & questions</span></span>

<span data-ttu-id="f0e4b-150">Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="f0e4b-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="f0e4b-151">Můžete také zkontrolovat všechny stávající dotazy nebo potíže [v WCF úložišti na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="f0e4b-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="f0e4b-152">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="f0e4b-152">Release notes</span></span>

* <span data-ttu-id="f0e4b-153">Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) aktualizovanou verzi informace, včetně známých problémů.</span><span class="sxs-lookup"><span data-stu-id="f0e4b-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="f0e4b-154">Informace o</span><span class="sxs-lookup"><span data-stu-id="f0e4b-154">Information</span></span>

* [<span data-ttu-id="f0e4b-155">Balíček NuGet DotNet svcutil</span><span class="sxs-lookup"><span data-stu-id="f0e4b-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
