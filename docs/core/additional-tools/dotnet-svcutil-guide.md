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
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Nástroj dotnet svcutil WCF pro .NET Core

Windows Communication Foundation (WCF) **dotnet svcutil** nástroj je nástroj příkazového řádku .NET Core, načte metadata z webové služby v umístění v síti nebo ze souboru WSDL, který generuje WCF třídu obsahující metody proxy serveru klienta, který přístup k operací webové služby.

Podobně jako [ **metadat modelu služby - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroje pro projekty .NET Framework **dotnet svcutil** je nástroj příkazového řádku pro generování odkaz webové služby kompatibilní s projekty .NET Core a .NET Standard.

**Dotnet svcutil** alternativní možnost je nástroj [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) sady Visual Studio zprostředkovatel připojené služby, která se poprvé dodáváno pomocí sady Visual Studio 2017 v15.5. **Dotnet svcutil** nástroj jako nástroj příkazového řádku .NET Core, je k dispozici na různých platformách Windows, Linux a macOS.

> [!IMPORTANT]
> Služby by měly odkazovat pouze z důvěryhodného zdroje. Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)
* [Sady SDK .NET core 2.1](https://dotnet.microsoft.com/download) nebo novější verze
* Váš oblíbený editor kódu

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet – svcutil 1.x](#tab/dotnetsvcutil1x)
* [.NET core 1.0.4 SDK](https://dotnet.microsoft.com/download) nebo novější verze
* Váš oblíbený editor kódu

---

## <a name="getting-started"></a>Začínáme

Následující příklad vás provede kroky potřebné k přidání odkaz webové služby do webového projektu .NET Core a vyvolat službu. Vytvoříte webovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidejte odkaz na webovou službu, která implementuje kontrakt následující:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

V tomto příkladu předpokládejme, že webová služba bude možné hostovat na následující adrese: `http://contoso.com/SayHello.svc`

Z příkazového okna Windows, macOS nebo Linux postupujte následovně:

1. Vytvořte adresář _HelloSvcutil_ pro váš projekt a nastavte ji váš aktuální adresář, jako v následujícím příkladu:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Vytvořte nový C# webový projekt v tomto adresáři pomocí [ `dotnet new` ](../tools/dotnet-new.md) takto:

    ```console
    dotnet new web
    ```

3. Nainstalujte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako nástroj příkazového řádku:  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet – svcutil 1.x](#tab/dotnetsvcutil1x)
    Otevřít `HelloSvcutil.csproj` souboru v editoru projektu, upravit `Project` prvek a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na rozhraní příkazového řádku nástroje, pomocí následujícího kódu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Obnovte _dotnet svcutil_ balíček pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:

    ```console
    dotnet restore
    ```

    ---

4. Spustit _dotnet svcutil_ příkazu vygenerujte soubor odkaz webové služby následujícím způsobem:

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet – svcutil 1.x](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Vygenerovaný soubor je uložen jako _HelloSvcutil/ServiceReference/Reference.cs_. _Dotnet svcutil_ nástroj také přidá do projektu odpovídající balíčky WCF vyžaduje proxy kód jako odkazy na balíček.

## <a name="using-the-service-reference"></a>Pomocí odkazu na službu

1. Obnovení balíčků WCF pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:

    ```console
    dotnet restore
    ```

2. Vyhledejte název klienta, třídy a operace, kterou chcete použít. `Reference.cs` bude obsahovat třídu, která dědí z `System.ServiceModel.ClientBase`, metodami, které slouží k volání operací služby. V tomto příkladu chcete volat _SayHello_ služby _Hello_ operace. `ServiceReference.SayHelloClient` je název třídy klienta a je volána metoda `HelloAsync` , který je možné volat operaci.

3. Otevřít `Startup.cs` souboru ve svém editoru a přidejte sadu pomocí příkazu pro obor názvů odkazu služby v horní části:

    ```csharp
    using ServiceReference;
    ```

4. Upravit `Configure` metoda k vyvolání webové služby. To provedete tak, že vytvoříte instanci, která dědí z třídy `ClientBase` a volání metody u objektu klienta:

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

5. Spuštění aplikace pomocí [ `dotnet run` ](../tools/dotnet-run.md) takto:

    ```console
    dotnet run
    ```

6. Přejděte na adresu URL uvedená v konzole (například `http://localhost:5000`) ve webovém prohlížeči.

Byste měli vidět následující výstup: "Hello dotnet-svcutil!"

Podrobný popis `dotnet-svcutil` nástroj parametry, vyvolají nástroj předávání parametru nápovědy následujícím způsobem:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[DotNet – svcutil 1.x](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Zpětná vazba a otázky

Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new). Můžete také zkontrolovat všechny stávající dotazy nebo potíže [v WCF úložišti na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Zpráva k vydání verze

* Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) aktualizovanou verzi informace, včetně známých problémů.

## <a name="information"></a>Informace o

* [Balíček NuGet DotNet svcutil](https://nuget.org/packages/dotnet-svcutil)
