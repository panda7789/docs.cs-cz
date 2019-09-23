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
# <a name="create-a-new-aspnet-core-grpc-project"></a>Vytvoření nového projektu ASP.NET Core gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.NET Core přináší výkonný nástroj `dotnet`CLI, který umožňuje vytvářet a spravovat projekty a řešení z příkazového řádku. Nástroj je úzce integrovaný se sadou Visual Studio, takže vše je dostupné i prostřednictvím známého rozhraní grafického uživatelského rozhraní (GUI). V této kapitole se zobrazí obě možnosti vytvoření nového projektu ASP.NET Core gRPC: nejprve pomocí sady Visual Studio a pak pomocí .NET Core CLI.

## <a name="create-the-project-using-visual-studio"></a>Vytvoření projektu pomocí sady Visual Studio

> [!IMPORTANT]
> K vývoji jakékoli aplikace ASP.NET Core 3,0 budete potřebovat Visual Studio 2019,3 nebo novější s nainstalovanou úlohou **vývoj pro ASP.NET a web** .

Vytvoří prázdné řešení s názvem **TraderSys** ze šablony *prázdného řešení* . Přidejte složku řešení s názvem `src`, potom klikněte pravým tlačítkem myši na složku a zvolte možnost **Přidat** > **Nový projekt** z kontextové nabídky. Do `grpc` vyhledávacího pole šablony zadejte a měli byste vidět šablonu projektu s názvem `gRPC Service`.

![Dialogové okno Přidat nový projekt zobrazující šablonu projektu služby gRPC](media/create-project/new-grpc-project.png)

Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Konfigurovat projekt** a pojmenujte projekt `TraderSys.Portfolios`a přidejte `src` podadresář do **umístění**.

![Dialogové okno Konfigurace projektu](media/create-project/configure-project.png)

Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Nový projekt gRPC** .

![Dialog Nový projekt gRPC](media/create-project/create-new-grpc-service.png)

V současnosti existují omezené možnosti pro vytvoření služby. Docker se zavede později v knize, takže nechejte toto políčko zatím nezaškrtnuté a stačí kliknout na **vytvořit**. Váš první projekt ASP.NET Core 3,0 gRPC se vygeneruje a přidá do řešení. Pokud nechcete informace o práci s nástrojem `dotnet CLI`, přejděte k části [příklad kódu](#clean-up-the-example-code) .

## <a name="create-the-project-using-the-net-core-cli"></a>Vytvoření projektu pomocí .NET Core CLI

Tato část se zabývá vytvářením řešení a projektů z příkazového řádku.

Vytvořte řešení, jak je znázorněno níže. Příznak (nebo `--output`) určuje výstupní adresář, který bude vytvořen v aktuálním adresáři, pokud neexistuje. `-o` Řešení bude mít stejný název jako adresář, tj. `TraderSys.sln`. Pomocí `-n` příznaku (nebo `--name`) můžete zadat jiný název.

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 obsahuje šablonu CLI pro služby gRPC Services. Vytvoří nový projekt pomocí této šablony a umístí ho do `src` podadresáře, jako je konvence pro ASP.NET Core projekty. Projekt bude pojmenován za adresářem (tj. `TraderSys.Portfolios.csproj`), pokud neurčíte jiný název `-n` s příznakem.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Nakonec přidejte projekt do řešení pomocí `dotnet sln` příkazu.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Vzhledem k tomu, že daný adresář obsahuje `.csproj` pouze jeden soubor, můžete se zbavit zadáním pouze adresáře, do kterého se uloží text.

Toto řešení teď můžete otevřít v aplikaci Visual Studio 2019, Visual Studio Code nebo libovolnému editoru, kterému dáváte přednost.

## <a name="clean-up-the-example-code"></a>Vyčištění ukázkového kódu

Nyní jste vytvořili ukázkovou službu pomocí šablony gRPC, která byla přezkoumána dříve v knize. To není užitečné v našem obchodním kontextu zásob, takže budeme upravovat věci našeho prvního projektu.

### <a name="rename-and-edit-the-proto-file"></a>Přejmenujte a upravte soubor.

Pokračujte a přejmenujte `Protos/greet.proto` soubor na `Protos/portfolios.proto` a otevřete ho v editoru. `package` Odstraňte vše za řádkem, potom `package` `option csharp_namespace`Změňte názvy a a `service` odeberte výchozí `SayHello` službu, aby kód vypadal takto.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Šablona ve výchozím nastavení nepřidá `Protos` část oboru názvů, ale její přidání usnadňuje udržování tříd generovaných gRPC a vlastní třídy jasně oddělené v kódu.

Pokud přejmenujete `greet.proto` soubor v integrovaném vývojovém prostředí (IDE), jako je například Visual Studio, odkaz na tento soubor se automaticky `.csproj` aktualizuje v souboru. Ale v některých dalších editorech, jako je například Visual Studio Code, není tento odkaz automaticky aktualizován, takže je nutné ručně upravit soubor projektu.

V cílících `Protobuf` sestavení gRPC je element Item, který vám umožní určit, které `.proto` soubory by se měly kompilovat a které formy generování kódu se vyžadují (tj. "Server" nebo "klient").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Přejmenovat třídu GreeterService

Třída je ve složce a dědí z `Greeter.GreeterBase`. `Services` `GreeterService` Přejmenujte `PortfolioService` ji na a změňte základní třídu `Portfolios.PortfoliosBase`na. `override` Odstraňte metody.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

V metodě ve `GreeterService` třídě`Startup` byl odkaz na třídu. `Configure` Pokud jste použili Refaktoring pro přejmenování třídy, tento odkaz by měl být automaticky aktualizován. Pokud jste to ale neudělali, budete ho muset ručně upravit.

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

V další části přidáme do této nové služby funkce.

>[!div class="step-by-step"]
>[Předchozí](migrate-wcf-to-grpc.md)
>[Další](migrate-request-reply.md)
