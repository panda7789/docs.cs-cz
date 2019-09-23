---
title: Vytvoření nového projektu ASP.NET Core gRPC – gRPC pro vývojáře WCF
description: Naučte se vytvořit projekt gRPC pomocí sady Visual Studio nebo z příkazového řádku.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184566"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="a706d-103">Vytvoření nového projektu ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="a706d-103">Create a new ASP.NET Core gRPC project</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a706d-104">.NET Core přináší výkonný nástroj `dotnet`CLI, který umožňuje vytvářet a spravovat projekty a řešení z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a706d-104">.NET Core comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="a706d-105">Nástroj je úzce integrovaný se sadou Visual Studio, takže vše je dostupné i prostřednictvím známého rozhraní grafického uživatelského rozhraní (GUI).</span><span class="sxs-lookup"><span data-stu-id="a706d-105">The tool is closely integrated with Visual Studio, so everything is also available through the familiar GUI interface.</span></span> <span data-ttu-id="a706d-106">V této kapitole se zobrazí obě možnosti vytvoření nového projektu ASP.NET Core gRPC: nejprve pomocí sady Visual Studio a pak pomocí .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="a706d-106">This chapter will show both ways to create a new ASP.NET Core gRPC project: first with Visual Studio, then with the .NET Core CLI.</span></span>

## <a name="create-the-project-using-visual-studio"></a><span data-ttu-id="a706d-107">Vytvoření projektu pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a706d-107">Create the project using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a706d-108">K vývoji jakékoli aplikace ASP.NET Core 3,0 budete potřebovat Visual Studio 2019,3 nebo novější s nainstalovanou úlohou **vývoj pro ASP.NET a web** .</span><span class="sxs-lookup"><span data-stu-id="a706d-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019.3 or later with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="a706d-109">Vytvoří prázdné řešení s názvem **TraderSys** ze šablony *prázdného řešení* .</span><span class="sxs-lookup"><span data-stu-id="a706d-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="a706d-110">Přidejte složku řešení s názvem `src`, potom klikněte pravým tlačítkem myši na složku a zvolte možnost **Přidat** > **Nový projekt** z kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="a706d-110">Add a Solution Folder called `src`, then right-click on the folder and choose **Add** > **New Project** from the context menu.</span></span> <span data-ttu-id="a706d-111">Do `grpc` vyhledávacího pole šablony zadejte a měli byste vidět šablonu projektu s názvem `gRPC Service`.</span><span class="sxs-lookup"><span data-stu-id="a706d-111">Enter `grpc` in the template search box and you should see a project template called `gRPC Service`.</span></span>

![Dialogové okno Přidat nový projekt zobrazující šablonu projektu služby gRPC](media/create-project/new-grpc-project.png)

<span data-ttu-id="a706d-113">Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Konfigurovat projekt** a pojmenujte projekt `TraderSys.Portfolios`a přidejte `src` podadresář do **umístění**.</span><span class="sxs-lookup"><span data-stu-id="a706d-113">Click **Next** to continue to the **Configure project** dialog and name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Dialogové okno Konfigurace projektu](media/create-project/configure-project.png)

<span data-ttu-id="a706d-115">Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Nový projekt gRPC** .</span><span class="sxs-lookup"><span data-stu-id="a706d-115">Click **Next** to continue to the **New gRPC project** dialog.</span></span>

![Dialog Nový projekt gRPC](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="a706d-117">V současnosti existují omezené možnosti pro vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="a706d-117">At present, there are limited options for the service creation.</span></span> <span data-ttu-id="a706d-118">Docker se zavede později v knize, takže nechejte toto políčko zatím nezaškrtnuté a stačí kliknout na **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="a706d-118">Docker will be introduced later in the book, so leave that checkbox unchecked for now and just click **Create**.</span></span> <span data-ttu-id="a706d-119">Váš první projekt ASP.NET Core 3,0 gRPC se vygeneruje a přidá do řešení.</span><span class="sxs-lookup"><span data-stu-id="a706d-119">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="a706d-120">Pokud nechcete informace o práci s nástrojem `dotnet CLI`, přejděte k části [příklad kódu](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="a706d-120">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-using-the-net-core-cli"></a><span data-ttu-id="a706d-121">Vytvoření projektu pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a706d-121">Create the project using the .NET Core CLI</span></span>

<span data-ttu-id="a706d-122">Tato část se zabývá vytvářením řešení a projektů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a706d-122">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="a706d-123">Vytvořte řešení, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="a706d-123">Create the solution as shown below.</span></span> <span data-ttu-id="a706d-124">Příznak (nebo `--output`) určuje výstupní adresář, který bude vytvořen v aktuálním adresáři, pokud neexistuje. `-o`</span><span class="sxs-lookup"><span data-stu-id="a706d-124">The `-o` (or `--output`) flag specifies the output directory, which will be created in the current directory if it does not exist.</span></span> <span data-ttu-id="a706d-125">Řešení bude mít stejný název jako adresář, tj. `TraderSys.sln`. Pomocí `-n` příznaku (nebo `--name`) můžete zadat jiný název.</span><span class="sxs-lookup"><span data-stu-id="a706d-125">The solution will be given the same name as the directory, i.e. `TraderSys.sln`. You can provide a different name using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="a706d-126">ASP.NET Core 3,0 obsahuje šablonu CLI pro služby gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="a706d-126">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="a706d-127">Vytvoří nový projekt pomocí této šablony a umístí ho do `src` podadresáře, jako je konvence pro ASP.NET Core projekty.</span><span class="sxs-lookup"><span data-stu-id="a706d-127">Create the new project using this template, putting it into an `src` subdirectory as is the convention for ASP.NET Core projects.</span></span> <span data-ttu-id="a706d-128">Projekt bude pojmenován za adresářem (tj. `TraderSys.Portfolios.csproj`), pokud neurčíte jiný název `-n` s příznakem.</span><span class="sxs-lookup"><span data-stu-id="a706d-128">The project will be named after the directory (i.e. `TraderSys.Portfolios.csproj`) unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="a706d-129">Nakonec přidejte projekt do řešení pomocí `dotnet sln` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a706d-129">Finally, add the project to the solution using the `dotnet sln` command.</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="a706d-130">Vzhledem k tomu, že daný adresář obsahuje `.csproj` pouze jeden soubor, můžete se zbavit zadáním pouze adresáře, do kterého se uloží text.</span><span class="sxs-lookup"><span data-stu-id="a706d-130">Since the given directory only contains a single `.csproj` file, you can get away with specifying just the directory to save typing.</span></span>

<span data-ttu-id="a706d-131">Toto řešení teď můžete otevřít v aplikaci Visual Studio 2019, Visual Studio Code nebo libovolnému editoru, kterému dáváte přednost.</span><span class="sxs-lookup"><span data-stu-id="a706d-131">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="a706d-132">Vyčištění ukázkového kódu</span><span class="sxs-lookup"><span data-stu-id="a706d-132">Clean up the example code</span></span>

<span data-ttu-id="a706d-133">Nyní jste vytvořili ukázkovou službu pomocí šablony gRPC, která byla přezkoumána dříve v knize.</span><span class="sxs-lookup"><span data-stu-id="a706d-133">You've now created an example service using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="a706d-134">To není užitečné v našem obchodním kontextu zásob, takže budeme upravovat věci našeho prvního projektu.</span><span class="sxs-lookup"><span data-stu-id="a706d-134">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="a706d-135">Přejmenujte a upravte soubor.</span><span class="sxs-lookup"><span data-stu-id="a706d-135">Rename and edit the proto file</span></span>

<span data-ttu-id="a706d-136">Pokračujte a přejmenujte `Protos/greet.proto` soubor na `Protos/portfolios.proto` a otevřete ho v editoru.</span><span class="sxs-lookup"><span data-stu-id="a706d-136">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto` and open it in your editor.</span></span> <span data-ttu-id="a706d-137">`package` Odstraňte vše za řádkem, potom `package` `option csharp_namespace`Změňte názvy a a `service` odeberte výchozí `SayHello` službu, aby kód vypadal takto.</span><span class="sxs-lookup"><span data-stu-id="a706d-137">Delete everything after the `package` line, then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service, so the code looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="a706d-138">Šablona ve výchozím nastavení nepřidá `Protos` část oboru názvů, ale její přidání usnadňuje udržování tříd generovaných gRPC a vlastní třídy jasně oddělené v kódu.</span><span class="sxs-lookup"><span data-stu-id="a706d-138">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="a706d-139">Pokud přejmenujete `greet.proto` soubor v integrovaném vývojovém prostředí (IDE), jako je například Visual Studio, odkaz na tento soubor se automaticky `.csproj` aktualizuje v souboru.</span><span class="sxs-lookup"><span data-stu-id="a706d-139">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="a706d-140">Ale v některých dalších editorech, jako je například Visual Studio Code, není tento odkaz automaticky aktualizován, takže je nutné ručně upravit soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="a706d-140">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="a706d-141">V cílících `Protobuf` sestavení gRPC je element Item, který vám umožní určit, které `.proto` soubory by se měly kompilovat a které formy generování kódu se vyžadují (tj. "Server" nebo "klient").</span><span class="sxs-lookup"><span data-stu-id="a706d-141">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="a706d-142">Přejmenovat třídu GreeterService</span><span class="sxs-lookup"><span data-stu-id="a706d-142">Rename the GreeterService class</span></span>

<span data-ttu-id="a706d-143">Třída je ve složce a dědí z `Greeter.GreeterBase`. `Services` `GreeterService`</span><span class="sxs-lookup"><span data-stu-id="a706d-143">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="a706d-144">Přejmenujte `PortfolioService` ji na a změňte základní třídu `Portfolios.PortfoliosBase`na.</span><span class="sxs-lookup"><span data-stu-id="a706d-144">Rename it to `PortfolioService` and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="a706d-145">`override` Odstraňte metody.</span><span class="sxs-lookup"><span data-stu-id="a706d-145">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="a706d-146">V metodě ve `GreeterService` třídě`Startup` byl odkaz na třídu. `Configure`</span><span class="sxs-lookup"><span data-stu-id="a706d-146">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="a706d-147">Pokud jste použili Refaktoring pro přejmenování třídy, tento odkaz by měl být automaticky aktualizován.</span><span class="sxs-lookup"><span data-stu-id="a706d-147">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="a706d-148">Pokud jste to ale neudělali, budete ho muset ručně upravit.</span><span class="sxs-lookup"><span data-stu-id="a706d-148">However, if you didn't, you need to edit it manually.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="a706d-149">V další části přidáme do této nové služby funkce.</span><span class="sxs-lookup"><span data-stu-id="a706d-149">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a706d-150">[Předchozí](migrate-wcf-to-grpc.md)
>[Další](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="a706d-150">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
