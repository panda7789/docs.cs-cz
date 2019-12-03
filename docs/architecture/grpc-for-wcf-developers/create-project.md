---
title: Vytvoření nového projektu ASP.NET Core gRPC – gRPC pro vývojáře WCF
description: Naučte se vytvořit projekt gRPC pomocí sady Visual Studio nebo příkazového řádku.
ms.date: 09/02/2019
ms.openlocfilehash: ea6d7658404f61fedb25d7de7ddedb7c51437383
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711437"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Vytvoření nového projektu gRPC ASP.NET Core

.NET Core SDK se dodává s výkonným nástrojem CLI, `dotnet`, který umožňuje vytvářet a spravovat projekty a řešení z příkazového řádku. Sada SDK je úzce integrovaná se sadou Visual Studio, takže vše je také k dispozici prostřednictvím známého grafického uživatelského rozhraní. Tato kapitola ukazuje jak vytvořit nový projekt ASP.NET Core gRPC.

## <a name="create-the-project-by-using-visual-studio"></a>Vytvoření projektu pomocí sady Visual Studio

> [!IMPORTANT]
> K vývoji jakékoli aplikace ASP.NET Core 3,0 budete potřebovat Visual Studio 2019 16,3 nebo novější s nainstalovanou úlohou **vývoj pro ASP.NET a web** .

Vytvoří prázdné řešení s názvem **TraderSys** ze šablony *prázdného řešení* . Přidejte složku řešení s názvem `src`. Potom klikněte pravým tlačítkem na složku a zvolte **přidat** > **Nový projekt**. Do vyhledávacího pole šablony zadejte `grpc` a měli byste vidět šablonu projektu s názvem `gRPC Service`.

![Snímek obrazovky s dialogovým oknem přidat nový projekt](media/create-project/new-grpc-project.png)

Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **Konfigurovat nový projekt** . Pojmenujte projekt `TraderSys.Portfolios`a přidejte podadresář `src` do **umístění**.

![Snímek obrazovky s dialogem Konfigurovat nový projekt](media/create-project/configure-project.png)

Kliknutím na tlačítko **Další** pokračujte v dialogovém okně **vytvořit novou službu gRPC** .

![Snímek obrazovky s dialogovým oknem vytvořit novou službu gRPC](media/create-project/create-new-grpc-service.png)

V současnosti máte omezené možnosti pro vytvoření služby. Docker se zavede později, takže teď nechte tuto možnost nevybranou. Stačí vybrat **vytvořit**. Váš první projekt ASP.NET Core 3,0 gRPC se vygeneruje a přidá do řešení. Pokud nechcete mít informace o práci s `dotnet CLI`, přejděte k části [ukázkový kód](#clean-up-the-example-code) .

## <a name="create-the-project-by-using-the-net-core-cli"></a>Vytvoření projektu pomocí .NET Core CLI

Tato část se zabývá vytvářením řešení a projektů z příkazového řádku.

Vytvořte řešení, jak je znázorněno v následujícím příkazu. Příznak `-o` (nebo `--output`) určuje výstupní adresář, který se vytvoří v aktuálním adresáři, pokud ještě neexistuje. Řešení má stejný název jako adresář: `TraderSys.sln`. Pomocí příznaku `-n` (nebo `--name`) můžete zadat jiný název.

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 obsahuje šablonu CLI pro služby gRPC Services. Vytvořte nový projekt pomocí této šablony a zadáte ho do podadresáře `src`, stejně jako se jedná o konvenční pro ASP.NET Core projekty. Projekt je pojmenován za adresářem (`TraderSys.Portfolios.csproj`), pokud neurčíte jiný název s příznakem `-n`.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Nakonec přidejte projekt do řešení pomocí příkazu `dotnet sln`:

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Vzhledem k tomu, že konkrétní adresář obsahuje pouze jeden soubor `.csproj`, můžete zadat pouze adresář a uložit tak jeho zadání.

Toto řešení teď můžete otevřít v aplikaci Visual Studio 2019, Visual Studio Code nebo libovolnému editoru, kterému dáváte přednost.

## <a name="clean-up-the-example-code"></a>Vyčištění ukázkového kódu

Nyní jste vytvořili ukázkovou službu pomocí šablony gRPC, která byla přezkoumána dříve v knize. To není užitečné v našem obchodním kontextu zásob, takže budeme upravovat věci našeho prvního projektu.

### <a name="rename-and-edit-the-proto-file"></a>Přejmenujte a upravte soubor.

Pokračujte a přejmenujte soubor `Protos/greet.proto` na `Protos/portfolios.proto`a otevřete ho v editoru. Odstraňte vše za `package` řádek. Pak změňte `option csharp_namespace`, `package` a `service` jména a odeberte výchozí `SayHello` službu. Kód nyní vypadá takto:

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

V cílících sestavení gRPC je k dispozici prvek `Protobuf` položky, který umožňuje určit, které `.proto` soubory by měly být kompilovány a jaký formulář pro generování kódu je vyžadován (tj. "Server" nebo "klient").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Přejmenovat třídu `GreeterService`

Třída `GreeterService` je ve složce `Services` a dědí z `Greeter.GreeterBase`. Přejmenujte jej na `PortfolioService`a změňte základní třídu na `Portfolios.PortfoliosBase`. Odstraňte metody `override`.

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
