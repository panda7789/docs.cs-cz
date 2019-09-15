---
title: Přehled nástroje WCF Svcutil
description: Přehled nástroje Microsoft WCF dotnet-Svcutil, který přidává funkce pro projekty .NET Core a ASP.NET Core podobně jako nástroj WCF Svcutil pro projekty .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 7c3e2f7bcfb337a09a9cc13068c22d496762a90f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969937"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="85a60-103">WCF dotnet – nástroj Svcutil pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="85a60-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="85a60-104">Nástroj Windows Communication Foundation (WCF) **dotnet-Svcutil** je .NET Core CLI nástroj, který načítá metadata z webové služby v umístění v síti nebo ze souboru WSDL a GENERUJE třídu WCF obsahující metody proxy klienta, které přistupují k webové službě. Operations.</span><span class="sxs-lookup"><span data-stu-id="85a60-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="85a60-105">Podobně jako nástroj [**Service Model Metadata-Svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework Projects ( **dotnet-Svcutil** ) je nástroj příkazového řádku pro generování odkazu webové služby kompatibilního s projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="85a60-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="85a60-106">Nástroj **dotnet-Svcutil** je alternativou k [**webové službě WCF reference**](wcf-web-service-reference-guide.md) k poskytovateli propojené služby sady Visual Studio, který se poprvé dodává se sadou Visual Studio 2017 v 15.5.</span><span class="sxs-lookup"><span data-stu-id="85a60-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="85a60-107">Nástroj **dotnet-Svcutil** jako nástroj .NET Core CLI je k dispozici pro různé platformy v systémech Linux, MacOS a Windows.</span><span class="sxs-lookup"><span data-stu-id="85a60-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85a60-108">Měli byste odkazovat jenom na služby z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="85a60-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="85a60-109">Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="85a60-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85a60-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85a60-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="85a60-111">dotnet – Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="85a60-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

* <span data-ttu-id="85a60-112">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="85a60-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="85a60-113">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="85a60-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="85a60-114">dotnet – Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="85a60-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

* <span data-ttu-id="85a60-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="85a60-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="85a60-116">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="85a60-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="85a60-117">Začínáme</span><span class="sxs-lookup"><span data-stu-id="85a60-117">Getting started</span></span>

<span data-ttu-id="85a60-118">Následující příklad vás provede kroky potřebnými k přidání odkazu webové služby do webového projektu .NET Core a vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="85a60-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="85a60-119">Vytvoříte webovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidáte odkaz na webovou službu, která implementuje následující kontrakt:</span><span class="sxs-lookup"><span data-stu-id="85a60-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="85a60-120">V tomto příkladu Předpokládejme, že webová služba bude hostována na následující adrese:`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="85a60-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="85a60-121">V okně příkazového řádku Windows, macOS nebo Linux proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="85a60-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="85a60-122">Vytvořte pro svůj projekt adresář s názvem _HelloSvcutil_ a nastavte ho jako aktuální adresář, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="85a60-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="85a60-123">V tomto adresáři C# vytvořte nový webový projekt pomocí [`dotnet new`](../tools/dotnet-new.md) příkazu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85a60-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```console
    dotnet new web
    ```

3. <span data-ttu-id="85a60-124">Nainstalujte balíček NuGet jako nástroj rozhraní příkazového řádku: [ `dotnet-svcutil` ](https://nuget.org/packages/dotnet-svcutil) </span><span class="sxs-lookup"><span data-stu-id="85a60-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="85a60-125">dotnet – Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="85a60-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="85a60-126">dotnet – Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="85a60-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="85a60-127">Otevřete soubor [ `dotnet-svcutil` ](https://nuget.org/packages/dotnet-svcutil) projektu v editoru, `Project` upravte element a přidejte balíček NuGet jako odkaz na nástroj rozhraní příkazového řádku, a to pomocí následujícího kódu: `HelloSvcutil.csproj`</span><span class="sxs-lookup"><span data-stu-id="85a60-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="85a60-128">Pak obnovte balíček _dotnet-Svcutil_ pomocí [`dotnet restore`](../tools/dotnet-restore.md) příkazu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85a60-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

    ---

4. <span data-ttu-id="85a60-129">Spusťte příkaz _dotnet-Svcutil_ pro vytvoření referenčního souboru webové služby následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85a60-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="85a60-130">dotnet – Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="85a60-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="85a60-131">dotnet – Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="85a60-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="85a60-132">Vygenerovaný soubor je uložený jako _HelloSvcutil/ServiceReference/reference. cs_.</span><span class="sxs-lookup"><span data-stu-id="85a60-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="85a60-133">Nástroj _dotnet-Svcutil_ také přidá do projektu příslušné balíčky WCF vyžadované proxy kódem jako odkazy na balíčky.</span><span class="sxs-lookup"><span data-stu-id="85a60-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="85a60-134">Použití odkazu na službu</span><span class="sxs-lookup"><span data-stu-id="85a60-134">Using the Service Reference</span></span>

1. <span data-ttu-id="85a60-135">Pomocí [`dotnet restore`](../tools/dotnet-restore.md) příkazu obnovte balíčky služby WCF následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85a60-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

2. <span data-ttu-id="85a60-136">Vyhledejte název klientské třídy a operace, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="85a60-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="85a60-137">`Reference.cs`bude obsahovat třídu, která dědí z `System.ServiceModel.ClientBase`, s metodami, které lze použít k volání operací ve službě.</span><span class="sxs-lookup"><span data-stu-id="85a60-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="85a60-138">V tomto příkladu chcete zavolat operaci _Hello_ služby _sayHello_ .</span><span class="sxs-lookup"><span data-stu-id="85a60-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="85a60-139">`ServiceReference.SayHelloClient`je název třídy klienta a má metodu nazvanou `HelloAsync` , která může být použita k volání operace.</span><span class="sxs-lookup"><span data-stu-id="85a60-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="85a60-140">`Startup.cs` Otevřete soubor v editoru a přidejte příkaz using pro obor názvů odkazu na službu v horní části:</span><span class="sxs-lookup"><span data-stu-id="85a60-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="85a60-141">`Configure` Upravte metodu pro vyvolání webové služby.</span><span class="sxs-lookup"><span data-stu-id="85a60-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="85a60-142">To provedete vytvořením instance třídy, která dědí z `ClientBase` a voláním metody v objektu klienta:</span><span class="sxs-lookup"><span data-stu-id="85a60-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="85a60-143">Spusťte aplikaci pomocí [`dotnet run`](../tools/dotnet-run.md) příkazu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85a60-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```console
    dotnet run
    ```

6. <span data-ttu-id="85a60-144">Přejděte na adresu URL uvedenou v konzole (například `http://localhost:5000`) ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="85a60-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="85a60-145">Měl by se zobrazit následující výstup: "Hello dotnet-Svcutil!"</span><span class="sxs-lookup"><span data-stu-id="85a60-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="85a60-146">Podrobný popis `dotnet-svcutil` parametrů nástroje získáte tak, že vyvoláte nástroj, který předává parametr help následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="85a60-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="85a60-147">dotnet – Svcutil 2. x</span><span class="sxs-lookup"><span data-stu-id="85a60-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="85a60-148">dotnet – Svcutil 1. x</span><span class="sxs-lookup"><span data-stu-id="85a60-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="85a60-149">Názory & dotazů</span><span class="sxs-lookup"><span data-stu-id="85a60-149">Feedback & questions</span></span>

<span data-ttu-id="85a60-150">Pokud máte nějaké dotazy nebo připomínky, [otevřete problém na GitHubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="85a60-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="85a60-151">V [ÚLOŽIŠTI WCF na GitHubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)můžete také zkontrolovat všechny existující otázky nebo problémy.</span><span class="sxs-lookup"><span data-stu-id="85a60-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="85a60-152">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="85a60-152">Release notes</span></span>

* <span data-ttu-id="85a60-153">Aktualizované informace o verzi, včetně známých problémů, najdete v [poznámkách k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) .</span><span class="sxs-lookup"><span data-stu-id="85a60-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="85a60-154">Informace o</span><span class="sxs-lookup"><span data-stu-id="85a60-154">Information</span></span>

* [<span data-ttu-id="85a60-155">dotnet – balíček NuGet pro Svcutil</span><span class="sxs-lookup"><span data-stu-id="85a60-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
