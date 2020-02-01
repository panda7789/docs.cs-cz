---
title: Vytvoření nového projektu ASP.NET Core gRPC – gRPC pro vývojáře WCF
description: Naučte se vytvořit projekt gRPC pomocí sady Visual Studio nebo příkazového řádku.
ms.date: 09/02/2019
ms.openlocfilehash: fbcc598cf503a5baeca941803ff8fa0d5fc99671
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919402"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="d2bfd-103">Vytvoření nového projektu gRPC ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2bfd-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="d2bfd-104">.NET Core SDK se dodává s výkonným nástrojem CLI, `dotnet`, který umožňuje vytvářet a spravovat projekty a řešení z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-104">The .NET Core SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="d2bfd-105">Sada SDK je úzce integrovaná se sadou Visual Studio, takže vše je také k dispozici prostřednictvím známého grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="d2bfd-106">Tato kapitola ukazuje jak vytvořit nový projekt ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="d2bfd-107">Vytvoření projektu pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2bfd-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2bfd-108">K vývoji jakékoli aplikace ASP.NET Core 3,0 budete potřebovat Visual Studio 2019 verze 16,3 nebo novější s nainstalovanou úlohou **vývoj ASP.NET a webu** .</span><span class="sxs-lookup"><span data-stu-id="d2bfd-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019 version 16.3 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="d2bfd-109">Vytvoří prázdné řešení s názvem **TraderSys** ze šablony *prázdného řešení* .</span><span class="sxs-lookup"><span data-stu-id="d2bfd-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="d2bfd-110">Přidejte složku řešení s názvem `src`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="d2bfd-111">Potom klikněte pravým tlačítkem na složku a zvolte **přidat** > **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="d2bfd-112">Do vyhledávacího pole šablony zadejte `grpc` a měli byste vidět šablonu projektu s názvem `gRPC Service`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![Snímek obrazovky s dialogovým oknem přidat nový projekt](media/create-project/new-grpc-project.png)

<span data-ttu-id="d2bfd-114">Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Konfigurovat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="d2bfd-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="d2bfd-115">Pojmenujte projekt `TraderSys.Portfolios` a přidejte podadresář `src` do **umístění**.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-115">Name the project `TraderSys.Portfolios` and add an `src` subdirectory to the **Location**.</span></span>

![Snímek obrazovky s dialogem Konfigurovat nový projekt](media/create-project/configure-project.png)

<span data-ttu-id="d2bfd-117">Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **vytvořit novou službu gRPC** .</span><span class="sxs-lookup"><span data-stu-id="d2bfd-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![Snímek obrazovky s dialogovým oknem vytvořit novou službu gRPC](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="d2bfd-119">V současnosti máte omezené možnosti pro vytvoření služby.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="d2bfd-120">Docker se zavede později, takže teď nechte tuto možnost nevybranou.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="d2bfd-121">Stačí vybrat **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-121">Just select **Create**.</span></span> <span data-ttu-id="d2bfd-122">Váš první projekt ASP.NET Core 3,0 gRPC se vygeneruje a přidá do řešení.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-122">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="d2bfd-123">Pokud nechcete mít informace o práci s `dotnet CLI`, přejděte k části [ukázkový kód](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="d2bfd-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-core-cli"></a><span data-ttu-id="d2bfd-124">Vytvoření projektu pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="d2bfd-124">Create the project by using the .NET Core CLI</span></span>

<span data-ttu-id="d2bfd-125">Tato část se zabývá vytvářením řešení a projektů z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="d2bfd-126">Vytvořte řešení, jak je znázorněno v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="d2bfd-127">Příznak `-o` (nebo `--output`) určuje výstupní adresář, který se vytvoří v aktuálním adresáři, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="d2bfd-128">Řešení má stejný název jako adresář: `TraderSys.sln`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="d2bfd-129">Pomocí příznaku `-n` (nebo `--name`) můžete zadat jiný název.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="d2bfd-130">ASP.NET Core 3,0 obsahuje šablonu CLI pro služby gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-130">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="d2bfd-131">Vytvořte nový projekt pomocí této šablony a zadáte ho do podadresáře `src`, stejně jako se jedná o konvenční pro ASP.NET Core projekty.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="d2bfd-132">Projekt je pojmenován za adresářem (`TraderSys.Portfolios.csproj`), pokud neurčíte jiný název s příznakem `-n`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="d2bfd-133">Nakonec přidejte projekt do řešení pomocí příkazu `dotnet sln`:</span><span class="sxs-lookup"><span data-stu-id="d2bfd-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="d2bfd-134">Vzhledem k tomu, že konkrétní adresář obsahuje pouze jeden soubor `.csproj`, můžete zadat pouze adresář a uložit tak jeho zadání.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="d2bfd-135">Toto řešení teď můžete otevřít v aplikaci Visual Studio 2019, Visual Studio Code nebo libovolnému editoru, kterému dáváte přednost.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="d2bfd-136">Vyčištění ukázkového kódu</span><span class="sxs-lookup"><span data-stu-id="d2bfd-136">Clean up the example code</span></span>

<span data-ttu-id="d2bfd-137">Nyní jste vytvořili ukázkovou službu pomocí šablony gRPC, která byla přezkoumána dříve v knize.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="d2bfd-138">To není užitečné v našem obchodním kontextu zásob, takže budeme upravovat věci našeho prvního projektu.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-138">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="d2bfd-139">Přejmenujte a upravte soubor.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-139">Rename and edit the proto file</span></span>

<span data-ttu-id="d2bfd-140">Pokračujte a přejmenujte soubor `Protos/greet.proto` na `Protos/portfolios.proto`a otevřete ho v editoru.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="d2bfd-141">Odstraňte vše za `package` řádek.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="d2bfd-142">Pak změňte `option csharp_namespace`, `package` a `service` jména a odeberte výchozí `SayHello` službu.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="d2bfd-143">Kód nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="d2bfd-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="d2bfd-144">Šablona nepřidá ve výchozím nastavení část `Protos` oboru názvů, ale přidáním ji usnadňuje udržování tříd generovaných gRPC a vaše vlastní třídy jasně oddělené ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="d2bfd-145">Pokud soubor `greet.proto` přejmenujete v integrovaném vývojovém prostředí (IDE), jako je například Visual Studio, odkaz na tento soubor se automaticky aktualizuje v souboru `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="d2bfd-146">Ale v některých dalších editorech, jako je například Visual Studio Code, není tento odkaz automaticky aktualizován, takže je nutné ručně upravit soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="d2bfd-147">V cílících sestavení gRPC je k dispozici prvek `Protobuf` položky, který umožňuje určit, které `.proto` soubory by měly být kompilovány a jaký formulář pro generování kódu je vyžadován (tj. "Server" nebo "klient").</span><span class="sxs-lookup"><span data-stu-id="d2bfd-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="d2bfd-148">Přejmenovat třídu `GreeterService`</span><span class="sxs-lookup"><span data-stu-id="d2bfd-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="d2bfd-149">Třída `GreeterService` je ve složce `Services` a dědí z `Greeter.GreeterBase`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="d2bfd-150">Přejmenujte jej na `PortfolioService`a změňte základní třídu na `Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="d2bfd-151">Odstraňte metody `override`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="d2bfd-152">Existoval odkaz na třídu `GreeterService` v metodě `Configure` ve třídě `Startup`.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="d2bfd-153">Pokud jste použili Refaktoring pro přejmenování třídy, tento odkaz by měl být automaticky aktualizován.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="d2bfd-154">Pokud jste to ale neudělali, budete ho muset ručně upravit.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-154">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="d2bfd-155">V další části přidáme do této nové služby funkce.</span><span class="sxs-lookup"><span data-stu-id="d2bfd-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d2bfd-156">[Předchozí](migrate-wcf-to-grpc.md)
>[Další](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="d2bfd-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
