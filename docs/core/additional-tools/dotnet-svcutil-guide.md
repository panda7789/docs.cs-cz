---
title: Nástroj dotnet svcutil Microsoft WCF
description: Přehled nástroje dotnet svcutil Microsoft WCF, který přidá funkce pro projekty .NET Core a ASP.NET Core, podobný nástroj svcutil WCF pro projekty .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.openlocfilehash: bb4d8e5f3997318b720535b0f1e07fc33d13338a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511883"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Nástroj dotnet svcutil Microsoft WCF

Windows Communication Foundation (WCF) **dotnet svcutil** nástroj je nástroj příkazového řádku .NET Core, načte metadata z webové služby v umístění v síti nebo ze souboru WSDL, který generuje WCF třídu obsahující metody proxy serveru klienta, který přístup k operací webové služby.

Podobně jako [ **metadat modelu služby - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroje pro projekty .NET Framework **dotnet svcutil** je nástroj příkazového řádku pro generování odkaz webové služby kompatibilní s projekty .NET Core a .NET Standard.

**Dotnet svcutil** alternativní možnost je nástroj [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) sady Visual Studio zprostředkovatel připojené služby, která se poprvé dodáváno pomocí sady Visual Studio 2017 v15.5. **Dotnet svcutil** nástroj jako nástroj příkazového řádku .NET Core, je k dispozici na různých platformách Windows, Linux a macOS.

> [!IMPORTANT]
> Služby by měly odkazovat pouze z důvěryhodného zdroje. Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

* [Sada .NET core SDK](https://www.microsoft.com/net/download) verzi v1.0.4 nebo novější verze
* Váš oblíbený editor kódu

## <a name="getting-started"></a>Začínáme

Následující příklad vás provede kroky potřebné k přidání odkaz webové služby na projekt konzoly .NET Core a vyvolat službu. Vytvoříte konzolovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidá odkaz na webovou službu, která implementuje kontrakt následující:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

V tomto příkladu bude považovat za webové službě hostované na následující adrese: `http://contoso.com/SayHello.svc`

Z příkazového okna Windows, macOS nebo Linux postupujte následovně:

1. Vytvořte adresář _HelloSvcutil_ pro váš projekt a nastavte ji váš aktuální adresář, jako v následujícím příkladu:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Vytvořte nový projekt konzoly C# v tomto adresáři pomocí [ `dotnet new` ](../tools/dotnet-new.md) takto:

```console
dotnet new console
```

3. Otevřít `HelloSvcutil.csproj` souboru v editoru projektu, upravit `Project` prvek a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz na rozhraní příkazového řádku nástroje, pomocí následujícího kódu:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. Obnovit _dotnet svcutil_ balíček pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:

```console
dotnet restore
```

5. Spustit _dotnet_ s _svcutil_ příkazu vygenerujte soubor odkaz webové služby následujícím způsobem:

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
Vygenerovaný soubor je uložen jako _HelloSvcutil/ServiceReference1/Reference.cs_. _Dotnet_svcutil_ nástroj také přidá do projektu odpovídající balíčky WCF vyžaduje proxy kód jako odkazy na balíček.

6. Obnovení balíčků WCF pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) takto:

```console
dotnet restore
```

7. Otevřít `Program.cs` souboru v editoru, upravit `Main()` metoda a nahradit automaticky generovaný kód následujícím kódem, abyste mohli vyvolat službu web:

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. Spuštění aplikace pomocí [ `dotnet run` ](../tools/dotnet-run.md) takto:

```console
dotnet run
```
Zobrazí se následující výstup: "dotnet svcutil Hello!"

Podrobný popis `dotnet-svcutil` nástroj parametry, vyvolají nástroj předávání parametru nápovědy následujícím způsobem:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Další kroky

### <a name="feedback--questions"></a>Zpětná vazba a otázky

Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new). Můžete také zkontrolovat všechny stávající dotazy nebo potíže [v WCF úložišti na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Zpráva k vydání verze

* Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) aktualizovanou verzi informace, včetně známých problémů.

### <a name="information"></a>Informace o

* [Balíček NuGet DotNet svcutil](https://nuget.org/packages/dotnet-svcutil)
