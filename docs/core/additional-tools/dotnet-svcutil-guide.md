---
title: Nástroj Microsoft WCF svcutil dotnet.
description: Přehled nástroje dotnet svcutil Microsoft WCF, který přidá funkce pro .NET Core a ASP.NET Core projekty, podobně jako nástroj svcutil WCF pro projekty rozhraní .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 06/04/2018
ms.openlocfilehash: c40dd9b437afe7381244b944228b6b2efe046eb2
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753419"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a><span data-ttu-id="5cd12-103">Nástroj Microsoft WCF svcutil dotnet.</span><span class="sxs-lookup"><span data-stu-id="5cd12-103">Microsoft WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="5cd12-104">Windows Communication Foundation (WCF) **dotnet svcutil** nástroj je nástroj .NET Core rozhraní příkazového řádku, který získává metadata z webové služby v umístění v síti nebo ze souboru WSDL a generuje WCF třída obsahující metody proxy serveru klienta, přístup k operace webové služby.</span><span class="sxs-lookup"><span data-stu-id="5cd12-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="5cd12-105">Podobně jako [ **Metadata modelu služby - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro projekty rozhraní .NET Framework **dotnet svcutil** je nástroj příkazového řádku pro generování odkazu na webovou službu kompatibilní s projekty .NET Core a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5cd12-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="5cd12-106">**Dotnet svcutil** nástroj je alternativní možnost [ **odkaz na službu WCF Web** ](wcf-web-service-reference-guide.md) Visual Studio připojené poskytovatele služeb, která nejprve odeslaná pomocí sady Visual Studio 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="5cd12-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="5cd12-107">**Dotnet svcutil** nástroj jako nástroj pro .NET Core rozhraní příkazového řádku, je k dispozici platformy Linux, systému macOS a systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5cd12-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cd12-108">Služby by měl odkazovat jenom z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="5cd12-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="5cd12-109">Přidání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5cd12-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5cd12-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cd12-110">Prerequisites</span></span>

* <span data-ttu-id="5cd12-111">[.NET core SDK](https://www.microsoft.com/net/download) v1.0.4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="5cd12-111">[.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="5cd12-112">Editor vaše oblíbené kódu</span><span class="sxs-lookup"><span data-stu-id="5cd12-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="5cd12-113">Začínáme</span><span class="sxs-lookup"><span data-stu-id="5cd12-113">Getting started</span></span>

<span data-ttu-id="5cd12-114">Následující příklad vás provede kroky potřebné k přidání odkazu na webovou službu do projektu konzoly .NET Core a vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="5cd12-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="5cd12-115">Vytvoříte konzolovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidá odkaz na webová služba, která implementuje kontrakt následující:</span><span class="sxs-lookup"><span data-stu-id="5cd12-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="5cd12-116">V tomto příkladu se webová služba bude předpokládat pro hostování na následující adrese: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="5cd12-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="5cd12-117">Z příkazového okna Windows, systému macOS nebo Linux proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="5cd12-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="5cd12-118">Vytvořte adresář s názvem _HelloSvcutil_ pro svůj projekt a nastavit jej jako aktuální adresář, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5cd12-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="5cd12-119">Vytvořit nový projekt konzolové C# do tohoto adresáře pomocí [ `dotnet new` ](../tools/dotnet-new.md) příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="5cd12-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="5cd12-120">Otevřete `HelloSvcutil.csproj` souboru ve svém editoru projektu, upravit `Project` elementu a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz nástroj příkazového řádku, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="5cd12-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. <span data-ttu-id="5cd12-121">Obnovit _dotnet svcutil_ balíček pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="5cd12-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="5cd12-122">Spustit _dotnet_ s _svcutil_ příkazu vygenerujte soubor webové služby odkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5cd12-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="5cd12-123">Vygenerovaný soubor je uložena jako _HelloSvcutil/ServiceReference1/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="5cd12-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="5cd12-124">_Dotnet_svcutil_ nástroj také přidá do projektu odpovídající balíčky WCF vyžaduje kód proxy jako balíček odkazuje.</span><span class="sxs-lookup"><span data-stu-id="5cd12-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="5cd12-125">Obnovení balíčků WCF pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="5cd12-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="5cd12-126">Otevřete `Program.cs` souboru ve svém editoru, upravit `Main()` metodu a nahraďte automaticky generovaného kódu pomocí následující kód k vyvolání webové služby:</span><span class="sxs-lookup"><span data-stu-id="5cd12-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="5cd12-127">Spuštění aplikace pomocí [ `dotnet run` ](../tools/dotnet-run.md) příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="5cd12-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="5cd12-128">Měli byste vidět následující výstup: "Hello dotnet svcutil!"</span><span class="sxs-lookup"><span data-stu-id="5cd12-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="5cd12-129">Podrobný popis `dotnet-svcutil` nástroj parametry, vyvolání nástroje předání parametru nápovědy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5cd12-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="5cd12-130">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5cd12-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="5cd12-131">Názory a dotazy</span><span class="sxs-lookup"><span data-stu-id="5cd12-131">Feedback & questions</span></span>

<span data-ttu-id="5cd12-132">Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="5cd12-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="5cd12-133">Můžete také zkontrolovat existující dotazy nebo problémy [v úložišti WCF na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="5cd12-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="5cd12-134">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="5cd12-134">Release notes</span></span>

* <span data-ttu-id="5cd12-135">Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) aktualizované verze informace, včetně známých problémů.</span><span class="sxs-lookup"><span data-stu-id="5cd12-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="5cd12-136">Informace o</span><span class="sxs-lookup"><span data-stu-id="5cd12-136">Information</span></span>

* [<span data-ttu-id="5cd12-137">Balíček NuGet svcutil DotNet.</span><span class="sxs-lookup"><span data-stu-id="5cd12-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
