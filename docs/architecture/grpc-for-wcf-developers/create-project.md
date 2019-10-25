---
title: Vytvoření nového projektu ASP.NET Core gRPC – gRPC pro vývojáře WCF
description: Naučte se vytvořit projekt gRPC pomocí sady Visual Studio nebo z příkazového řádku.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a30d19e1e48692ad68a648406d4bf369937744d7
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846713"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Vytvoření nového projektu gRPC ASP.NET Core

.NET Core přináší výkonný nástroj CLI, `dotnet`, který umožňuje vytvářet a spravovat projekty a řešení z příkazového řádku. Nástroj je úzce integrovaný se sadou Visual Studio, takže vše je dostupné i prostřednictvím známého rozhraní grafického uživatelského rozhraní (GUI). V této kapitole se zobrazí obě možnosti vytvoření nového projektu ASP.NET Core gRPC: nejprve pomocí sady Visual Studio a pak pomocí .NET Core CLI.

## <a name="create-the-project-using-visual-studio"></a>Vytvoření projektu pomocí sady Visual Studio

> [!IMPORTANT]
> K vývoji jakékoli aplikace ASP.NET Core 3,0 budete potřebovat Visual Studio 2019,3 nebo novější s nainstalovanou úlohou **vývoj pro ASP.NET a web** .

Vytvoří prázdné řešení s názvem **TraderSys** ze šablony *prázdného řešení* . Přidejte složku řešení s názvem `src`, klikněte pravým tlačítkem myši na složku a zvolte možnost **přidat** > **Nový projekt** z kontextové nabídky. Do vyhledávacího pole šablony zadejte `grpc` a měli byste vidět šablonu projektu s názvem `gRPC Service`.

![Dialogové okno Přidat nový projekt zobrazující šablonu projektu služby gRPC](media/create-project/new-grpc-project.png)

Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Konfigurovat projekt** a pojmenujte projekt `TraderSys.Portfolios`a přidejte podadresář `src` do **umístění**.

![Dialogové okno Konfigurace projektu](media/create-project/configure-project.png)

Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Nový projekt gRPC** .

![Dialog Nový projekt gRPC](media/create-project/create-new-grpc-service.png)

V současnosti existují omezené možnosti pro vytvoření služby. Docker se zavede později v knize, takže nechejte toto políčko zatím nezaškrtnuté a stačí kliknout na **vytvořit**. Váš první projekt ASP.NET Core 3,0 gRPC se vygeneruje a přidá do řešení. Pokud nechcete mít informace o práci s `dotnet CLI`, přejděte k části [ukázkový kód](#clean-up-the-example-code) .

## <a name="create-the-project-using-the-net-core-cli"></a>Vytvoření projektu pomocí .NET Core CLI

Tato část se zabývá vytvářením řešení a projektů z příkazového řádku.

Vytvořte řešení, jak je znázorněno níže. Příznak `-o` (nebo `--output`) určuje výstupní adresář, který se vytvoří v aktuálním adresáři, pokud neexistuje. Řešení bude mít stejný název jako adresář, tj. `TraderSys.sln`. Pomocí příznaku `-n` (nebo `--name`) můžete zadat jiný název.

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 obsahuje šablonu CLI pro služby gRPC Services. Vytvořte nový projekt pomocí této šablony, který umístí do podadresáře `src`, jako je konvence pro ASP.NET Core projekty. Projekt bude pojmenován za adresářem (tj. `TraderSys.Portfolios.csproj`), pokud neurčíte jiný název s příznakem `-n`.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Nakonec přidejte projekt do řešení pomocí příkazu `dotnet sln`.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Vzhledem k tomu, že daný adresář obsahuje pouze jeden soubor `.csproj`, můžete se zbavit zadání pouze adresáře, do kterého se má ukládat text.

Toto řešení teď můžete otevřít v aplikaci Visual Studio 2019, Visual Studio Code nebo libovolnému editoru, kterému dáváte přednost.

## <a name="clean-up-the-example-code"></a>Vyčištění ukázkového kódu

Nyní jste vytvořili ukázkovou službu pomocí šablony gRPC, která byla přezkoumána dříve v knize. To není užitečné v našem obchodním kontextu zásob, takže budeme upravovat věci našeho prvního projektu.

### <a name="rename-and-edit-the-proto-file"></a>Přejmenujte a upravte soubor.

Pokračujte a přejmenujte soubor `Protos/greet.proto` na `Protos/portfolios.proto` a otevřete ho v editoru. Odstraňte vše za `package` řádek, potom změňte názvy `option csharp_namespace`, `package` a `service` a odeberte výchozí `SayHello` službu, aby kód vypadal takto.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Šablona nepřidá ve výchozím nastavení část `Protos` oboru názvů, ale přidáním ji usnadňuje udržování tříd generovaných gRPC a vaše vlastní třídy jasně oddělené ve vašem kódu.

Pokud soubor `greet.proto` přejmenujete v integrovaném vývojovém prostředí (IDE), jako je například Visual Studio, odkaz na tento soubor se automaticky aktualizuje v souboru `.csproj`. Ale v některých dalších editorech, jako je například Visual Studio Code, není tento odkaz automaticky aktualizován, takže je nutné ručně upravit soubor projektu.

V cílících sestavení gRPC je k dispozici prvek `Protobuf` položky, který umožňuje určit, které `.proto` soubory by měly být kompilovány a které formy generování kódu jsou vyžadovány (tj. "Server" nebo "klient").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Přejmenovat třídu GreeterService

Třída `GreeterService` je ve složce `Services` a dědí z `Greeter.GreeterBase`. Přejmenujte jej na `PortfolioService` a změňte základní třídu na `Portfolios.PortfoliosBase`. Odstraňte metody `override`.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Existoval odkaz na třídu `GreeterService` v metodě `Configure` ve třídě `Startup`. Pokud jste použili Refaktoring pro přejmenování třídy, tento odkaz by měl být automaticky aktualizován. Pokud jste to ale neudělali, budete ho muset ručně upravit.

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
