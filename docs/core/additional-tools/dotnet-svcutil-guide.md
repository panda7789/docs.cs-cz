---
title: Přehled nástroje WCF Svcutil
description: Přehled nástroje Microsoft WCF dotnet-Svcutil, který přidává funkce pro projekty .NET Core a ASP.NET Core podobně jako nástroj WCF Svcutil pro projekty .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: fde42f7d040fba91f51ce6faa58282ed0206a853
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396220"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>WCF dotnet – nástroj Svcutil pro .NET Core

Nástroj Windows Communication Foundation (WCF) **dotnet-Svcutil** je nástroj .NET, který načítá metadata z webové služby v umístění v síti nebo ze souboru WSDL a GENERUJE třídu WCF obsahující metody proxy klienta, které přistupují k operacím webové služby.

Podobně jako nástroj [**Service Model Metadata-Svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework Projects ( **dotnet-Svcutil** ) je nástroj příkazového řádku pro generování odkazu webové služby kompatibilního s projekty .NET Core a .NET Standard.

Nástroj **dotnet-Svcutil** je alternativou k [**webové službě WCF reference**](wcf-web-service-reference-guide.md) k poskytovateli propojené služby sady Visual Studio, který se poprvé dodává se sadou visual Studio 2017 verze 15,5. Nástroj **dotnet-Svcutil** jako nástroj .NET je k dispozici pro různé platformy v systémech Linux, MacOS a Windows.

> [!IMPORTANT]
> Měli byste odkazovat jenom na služby z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet – Svcutil 2. x](#tab/dotnetsvcutil2x)

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější verze
- Váš oblíbený editor kódu

# <a name="dotnet-svcutil-1x"></a>[dotnet – Svcutil 1. x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) nebo novější verze
- Váš oblíbený editor kódu

---

## <a name="getting-started"></a>Začínáme

Následující příklad vás provede kroky potřebnými k přidání odkazu webové služby do webového projektu .NET Core a vyvolání služby. Vytvoříte webovou aplikaci .NET Core s názvem *HelloSvcutil* a přidáte odkaz na webovou službu, která implementuje následující kontrakt:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

V tomto příkladu Předpokládejme, že webová služba bude hostována na následující adrese:`http://contoso.com/SayHello.svc`

V okně příkazového řádku Windows, macOS nebo Linux proveďte následující kroky:

1. Vytvořte pro svůj projekt adresář s názvem _HelloSvcutil_ a nastavte ho jako aktuální adresář, jako v následujícím příkladu:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Pomocí příkazu vytvořte v tomto adresáři nový webový projekt v jazyce C# následujícím [`dotnet new`](../tools/dotnet-new.md) způsobem:

    ```dotnetcli
    dotnet new web
    ```

3. Nainstalujte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako nástroj rozhraní příkazového řádku: <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet – Svcutil 2. x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet – Svcutil 1. x](#tab/dotnetsvcutil1x)
    Otevřete `HelloSvcutil.csproj` soubor projektu v editoru, upravte `Project` element a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na nástroj rozhraní příkazového řádku, a to pomocí následujícího kódu:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Pak obnovte balíček _dotnet-Svcutil_ pomocí [`dotnet restore`](../tools/dotnet-restore.md) příkazu následujícím způsobem:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Spusťte příkaz _dotnet-Svcutil_ pro vytvoření referenčního souboru webové služby následujícím způsobem:

    # <a name="dotnet-svcutil-2x"></a>[dotnet – Svcutil 2. x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet – Svcutil 1. x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Vygenerovaný soubor je uložený jako _HelloSvcutil/ServiceReference/reference. cs_. Nástroj _dotnet-Svcutil_ také přidá do projektu příslušné balíčky WCF vyžadované proxy kódem jako odkazy na balíčky.

## <a name="using-the-service-reference"></a>Použití odkazu na službu

1. Pomocí příkazu obnovte balíčky služby WCF následujícím [`dotnet restore`](../tools/dotnet-restore.md) způsobem:

    ```dotnetcli
    dotnet restore
    ```

2. Vyhledejte název klientské třídy a operace, kterou chcete použít. `Reference.cs`bude obsahovat třídu, která dědí z `System.ServiceModel.ClientBase` , s metodami, které lze použít k volání operací ve službě. V tomto příkladu chcete zavolat operaci _Hello_ služby _sayHello_ . `ServiceReference.SayHelloClient`je název třídy klienta a má metodu nazvanou `HelloAsync` , která může být použita k volání operace.

3. Otevřete `Startup.cs` soubor v editoru a přidejte `using` direktivu pro obor názvů referencí na službu v horní části:

    ```csharp
    using ServiceReference;
    ```

4. Upravte `Configure` metodu pro vyvolání webové služby. To provedete vytvořením instance třídy, která dědí z `ClientBase` a voláním metody v objektu klienta:

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
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

5. Spusťte aplikaci pomocí příkazu následujícím [`dotnet run`](../tools/dotnet-run.md) způsobem:

    ```dotnetcli
    dotnet run
    ```

6. Přejděte na adresu URL uvedenou v konzole (například `http://localhost:5000` ) ve webovém prohlížeči.

Měl by se zobrazit následující výstup: Hello dotnet-Svcutil!

Podrobný popis `dotnet-svcutil` parametrů nástroje získáte tak, že vyvoláte nástroj, který předává parametr help následujícím způsobem:
# <a name="dotnet-svcutil-2x"></a>[dotnet – Svcutil 2. x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet – Svcutil 1. x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Názory & dotazů

Pokud máte nějaké dotazy nebo připomínky, [otevřete problém na GitHubu](https://github.com/dotnet/wcf/issues/new). V [ÚLOŽIŠTI WCF na GitHubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)můžete také zkontrolovat všechny existující otázky nebo problémy.

## <a name="release-notes"></a>Zpráva k vydání verze

- Aktualizované informace o verzi, včetně známých problémů, najdete v [poznámkách k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) .

## <a name="information"></a>Informace

- [dotnet – balíček NuGet pro Svcutil](https://nuget.org/packages/dotnet-svcutil)
