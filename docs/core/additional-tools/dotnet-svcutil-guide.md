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
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>WCF dotnet-svcutil nástroj pro .NET Core

Nástroj WCF (Windows Communication Foundation) **dotnet-svcutil** je nástroj .NET, který načítá metadata z webové služby v síťovém umístění nebo ze souboru WSDL a generuje třídu WCF obsahující metody proxy klienta, které přistupují k operacím webové služby.

Podobně jako [**u nástroje Metadata modelu služby - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro projekty rozhraní .NET Framework je **dotnet-svcutil** nástroj příkazového řádku pro generování odkazu webové služby kompatibilního s projekty .NET Core a .NET Standard.

Nástroj **dotnet-svcutil** je alternativou k poskytovateli připojených služeb [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio, který byl poprvé dodán s Visual Studio 2017 verze 15.5. Nástroj **dotnet-svcutil** jako nástroj .NET je k dispozici napříč platformami v systémech Linux, macOS a Windows.

> [!IMPORTANT]
> Měli byste odkazovat pouze na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2,x](#tab/dotnetsvcutil2x)

- [Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze
- Váš oblíbený editor kódu

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1,x](#tab/dotnetsvcutil1x)

- [Sada .NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) nebo novější verze
- Váš oblíbený editor kódu

---

## <a name="getting-started"></a>Začínáme

Následující příklad vás provede kroky potřebné k přidání odkazu webové služby na webový projekt .NET Core a vyvolání služby. Vytvoříte webovou aplikaci .NET Core s názvem *HelloSvcutil* a přidáte odkaz na webovou službu, která implementuje následující kontrakt:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

V tomto příkladu předpokládejme, že webová služba bude hostována na následující adrese:`http://contoso.com/SayHello.svc`

Z příkazového okna Windows, macOS nebo Linux uvádějí težcí kroky:

1. Vytvořte adresář s názvem _HelloSvcutil_ pro váš projekt a udělejte z něj aktuální adresář, jako v následujícím příkladu:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Vytvořte nový webový projekt jazyka C# v tomto adresáři pomocí příkazu [`dotnet new`](../tools/dotnet-new.md) následujícím způsobem:

    ```dotnetcli
    dotnet new web
    ```

3. Nainstalujte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako nástroj cli: <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2,x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1,x](#tab/dotnetsvcutil1x)
    Otevřete `HelloSvcutil.csproj` soubor projektu v editoru, `Project` upravte prvek a přidejte [balíček `dotnet-svcutil` NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na nástroj rozhraní příkazového příkazu pomocí následujícího kódu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Potom obnovte balíček _dotnet-svcutil_ pomocí příkazu [`dotnet restore`](../tools/dotnet-restore.md) následujícím způsobem:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Spusťte příkaz _dotnet-svcutil_ a vygenerujte referenční soubor webové služby následujícím způsobem:

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2,x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1,x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Generovaný soubor je uložen jako _HelloSvcutil/ServiceReference/Reference.cs_. Nástroj _dotnet-svcutil_ také přidá do projektu příslušné balíčky WCF vyžadované proxy kódem jako odkazy na balíček.

## <a name="using-the-service-reference"></a>Použití odkazu na službu

1. Obnovte balíčky WCF pomocí příkazu [`dotnet restore`](../tools/dotnet-restore.md) následujícím způsobem:

    ```dotnetcli
    dotnet restore
    ```

2. Vyhledejte název třídy klienta a operace, kterou chcete použít. `Reference.cs`bude obsahovat třídu, `System.ServiceModel.ClientBase`která dědí z , s metodami, které lze použít k volání operací ve službě. V tomto příkladu chcete volat operace _Hello_ služby _SayHello._ `ServiceReference.SayHelloClient`je název třídy klienta a má `HelloAsync` metodu, která je volána, kterou lze použít k volání operace.

3. Otevřete `Startup.cs` soubor v editoru a nahoře přidejte příkaz using pro obor názvů odkazů na službu:

    ```csharp
    using ServiceReference;
    ```

4. Upravte `Configure` metodu pro vyvolání webové služby. To provést vytvořením instance třídy, která `ClientBase` dědí z a volání metody na objekt klienta:

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

5. Spusťte aplikaci pomocí příkazu [`dotnet run`](../tools/dotnet-run.md) následujícím způsobem:

    ```dotnetcli
    dotnet run
    ```

6. Přejděte na adresu URL uvedenou `http://localhost:5000`v konzole (například) ve webovém prohlížeči.

Měli byste vidět následující výstup: "Hello dotnet-svcutil!"

Podrobný popis parametrů `dotnet-svcutil` nástroje zobrazíte následujícím způsobem, když předá nástroj parametrnápovědy takto:
# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2,x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1,x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Zpětná vazba & otázky

Pokud máte nějaké dotazy nebo zpětnou [vazbu, otevřete problém na GitHubu](https://github.com/dotnet/wcf/issues/new). Můžete také zkontrolovat všechny existující otázky nebo problémy [na wcf úložiště na GitHubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Poznámky k verzi

- Aktualizované informace o verzi, včetně známých problémů, naleznete v [poznámkách k verzi.](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md)

## <a name="information"></a>Informace

- [dotnet-svcutil NuGet balíček](https://nuget.org/packages/dotnet-svcutil)
