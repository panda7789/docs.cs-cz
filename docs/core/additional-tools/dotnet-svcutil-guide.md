---
title: Přehled nástroje WCF svcutil
description: Přehled nástroje Dotnet-svcutil společnosti Microsoft WCF, který přidává funkce pro projekty .NET Core a ASP.NET Core, podobně jako nástroj WCF svcutil pro projekty rozhraní .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920939"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="9af12-103">WCF dotnet-svcutil nástroj pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="9af12-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="9af12-104">Nástroj WCF (Windows Communication Foundation) **dotnet-svcutil** je nástroj .NET, který načítá metadata z webové služby v síťovém umístění nebo ze souboru WSDL a generuje třídu WCF obsahující metody proxy klienta, které přistupují k operacím webové služby.</span><span class="sxs-lookup"><span data-stu-id="9af12-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="9af12-105">Podobně jako [**u nástroje Metadata modelu služby - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro projekty rozhraní .NET Framework je **dotnet-svcutil** nástroj příkazového řádku pro generování odkazu webové služby kompatibilního s projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9af12-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="9af12-106">Nástroj **dotnet-svcutil** je alternativou k poskytovateli připojených služeb [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio, který byl poprvé dodán s Visual Studio 2017 verze 15.5.</span><span class="sxs-lookup"><span data-stu-id="9af12-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="9af12-107">Nástroj **dotnet-svcutil** jako nástroj .NET je k dispozici napříč platformami v systémech Linux, macOS a Windows.</span><span class="sxs-lookup"><span data-stu-id="9af12-107">The **dotnet-svcutil** tool as a .NET tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9af12-108">Měli byste odkazovat pouze na služby z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="9af12-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="9af12-109">Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9af12-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9af12-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9af12-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="9af12-111">dotnet-svcutil 2,x</span><span class="sxs-lookup"><span data-stu-id="9af12-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="9af12-112">[Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="9af12-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="9af12-113">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="9af12-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="9af12-114">dotnet-svcutil 1,x</span><span class="sxs-lookup"><span data-stu-id="9af12-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="9af12-115">[Sada .NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="9af12-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="9af12-116">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="9af12-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="9af12-117">Začínáme</span><span class="sxs-lookup"><span data-stu-id="9af12-117">Getting started</span></span>

<span data-ttu-id="9af12-118">Následující příklad vás provede kroky potřebné k přidání odkazu webové služby na webový projekt .NET Core a vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="9af12-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="9af12-119">Vytvoříte webovou aplikaci .NET Core s názvem *HelloSvcutil* a přidáte odkaz na webovou službu, která implementuje následující kontrakt:</span><span class="sxs-lookup"><span data-stu-id="9af12-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="9af12-120">V tomto příkladu předpokládejme, že webová služba bude hostována na následující adrese:`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="9af12-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="9af12-121">Z příkazového okna Windows, macOS nebo Linux uvádějí težcí kroky:</span><span class="sxs-lookup"><span data-stu-id="9af12-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="9af12-122">Vytvořte adresář s názvem _HelloSvcutil_ pro váš projekt a udělejte z něj aktuální adresář, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9af12-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="9af12-123">Vytvořte nový webový projekt jazyka C# v tomto adresáři pomocí příkazu [`dotnet new`](../tools/dotnet-new.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9af12-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="9af12-124">Nainstalujte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako nástroj cli: </span><span class="sxs-lookup"><span data-stu-id="9af12-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="9af12-125">dotnet-svcutil 2,x</span><span class="sxs-lookup"><span data-stu-id="9af12-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="9af12-126">dotnet-svcutil 1,x</span><span class="sxs-lookup"><span data-stu-id="9af12-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="9af12-127">Otevřete `HelloSvcutil.csproj` soubor projektu v editoru, `Project` upravte prvek a přidejte [balíček `dotnet-svcutil` NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na nástroj rozhraní příkazového příkazu pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="9af12-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="9af12-128">Potom obnovte balíček _dotnet-svcutil_ pomocí příkazu [`dotnet restore`](../tools/dotnet-restore.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9af12-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="9af12-129">Spusťte příkaz _dotnet-svcutil_ a vygenerujte referenční soubor webové služby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9af12-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="9af12-130">dotnet-svcutil 2,x</span><span class="sxs-lookup"><span data-stu-id="9af12-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="9af12-131">dotnet-svcutil 1,x</span><span class="sxs-lookup"><span data-stu-id="9af12-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="9af12-132">Generovaný soubor je uložen jako _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="9af12-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="9af12-133">Nástroj _dotnet-svcutil_ také přidá do projektu příslušné balíčky WCF vyžadované proxy kódem jako odkazy na balíček.</span><span class="sxs-lookup"><span data-stu-id="9af12-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="9af12-134">Použití odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="9af12-134">Using the Service Reference</span></span>

1. <span data-ttu-id="9af12-135">Obnovte balíčky WCF pomocí příkazu [`dotnet restore`](../tools/dotnet-restore.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9af12-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="9af12-136">Vyhledejte název třídy klienta a operace, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="9af12-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="9af12-137">`Reference.cs`bude obsahovat třídu, `System.ServiceModel.ClientBase`která dědí z , s metodami, které lze použít k volání operací ve službě.</span><span class="sxs-lookup"><span data-stu-id="9af12-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="9af12-138">V tomto příkladu chcete volat operace _Hello_ služby _SayHello._</span><span class="sxs-lookup"><span data-stu-id="9af12-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="9af12-139">`ServiceReference.SayHelloClient`je název třídy klienta a má `HelloAsync` metodu, která je volána, kterou lze použít k volání operace.</span><span class="sxs-lookup"><span data-stu-id="9af12-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="9af12-140">Otevřete `Startup.cs` soubor v editoru a nahoře přidejte příkaz using pro obor názvů odkazů na službu:</span><span class="sxs-lookup"><span data-stu-id="9af12-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="9af12-141">Upravte `Configure` metodu pro vyvolání webové služby.</span><span class="sxs-lookup"><span data-stu-id="9af12-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="9af12-142">To provést vytvořením instance třídy, která `ClientBase` dědí z a volání metody na objekt klienta:</span><span class="sxs-lookup"><span data-stu-id="9af12-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="9af12-143">Spusťte aplikaci pomocí příkazu [`dotnet run`](../tools/dotnet-run.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9af12-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="9af12-144">Přejděte na adresu URL uvedenou `http://localhost:5000`v konzole (například) ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9af12-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="9af12-145">Měli byste vidět následující výstup: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="9af12-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="9af12-146">Podrobný popis parametrů `dotnet-svcutil` nástroje zobrazíte následujícím způsobem, když předá nástroj parametrnápovědy takto:</span><span class="sxs-lookup"><span data-stu-id="9af12-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="9af12-147">dotnet-svcutil 2,x</span><span class="sxs-lookup"><span data-stu-id="9af12-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="9af12-148">dotnet-svcutil 1,x</span><span class="sxs-lookup"><span data-stu-id="9af12-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="9af12-149">Zpětná vazba & otázky</span><span class="sxs-lookup"><span data-stu-id="9af12-149">Feedback & questions</span></span>

<span data-ttu-id="9af12-150">Pokud máte nějaké dotazy nebo zpětnou [vazbu, otevřete problém na GitHubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="9af12-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="9af12-151">Můžete také zkontrolovat všechny existující otázky nebo problémy [na wcf úložiště na GitHubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="9af12-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="9af12-152">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="9af12-152">Release notes</span></span>

- <span data-ttu-id="9af12-153">Aktualizované informace o verzi, včetně známých problémů, naleznete v [poznámkách k verzi.](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md)</span><span class="sxs-lookup"><span data-stu-id="9af12-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="9af12-154">Informace</span><span class="sxs-lookup"><span data-stu-id="9af12-154">Information</span></span>

- [<span data-ttu-id="9af12-155">dotnet-svcutil NuGet balíček</span><span class="sxs-lookup"><span data-stu-id="9af12-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
