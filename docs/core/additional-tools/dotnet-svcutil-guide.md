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
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Nástroj Microsoft WCF svcutil dotnet.

Windows Communication Foundation (WCF) **dotnet svcutil** nástroj je nástroj .NET Core rozhraní příkazového řádku, který získává metadata z webové služby v umístění v síti nebo ze souboru WSDL a generuje WCF třída obsahující metody proxy serveru klienta, přístup k operace webové služby.

Podobně jako [ **Metadata modelu služby - svcutil** ](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro projekty rozhraní .NET Framework **dotnet svcutil** je nástroj příkazového řádku pro generování odkazu na webovou službu kompatibilní s projekty .NET Core a .NET Standard.

**Dotnet svcutil** nástroj je alternativní možnost [ **odkaz na službu WCF Web** ](wcf-web-service-reference-guide.md) Visual Studio připojené poskytovatele služeb, která nejprve odeslaná pomocí sady Visual Studio 2017 v15.5. **Dotnet svcutil** nástroj jako nástroj pro .NET Core rozhraní příkazového řádku, je k dispozici platformy Linux, systému macOS a systému Windows.

> [!IMPORTANT]
> Služby by měl odkazovat jenom z důvěryhodného zdroje. Přidání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.

## <a name="prerequisites"></a>Požadavky

* [.NET core SDK](https://www.microsoft.com/net/download) v1.0.4 nebo novější verze
* Editor vaše oblíbené kódu

## <a name="getting-started"></a>Začínáme

Následující příklad vás provede kroky potřebné k přidání odkazu na webovou službu do projektu konzoly .NET Core a vyvolání služby. Vytvoříte konzolovou aplikaci .NET Core s názvem _HelloSvcutil_ a přidá odkaz na webová služba, která implementuje kontrakt následující:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

V tomto příkladu se webová služba bude předpokládat pro hostování na následující adrese: `http://contoso.com/SayHello.svc`

Z příkazového okna Windows, systému macOS nebo Linux proveďte následující kroky:

1. Vytvořte adresář s názvem _HelloSvcutil_ pro svůj projekt a nastavit jej jako aktuální adresář, jako v následujícím příkladu:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Vytvořit nový projekt konzolové C# do tohoto adresáře pomocí [ `dotnet new` ](../tools/dotnet-new.md) příkaz takto:

```console
dotnet new console
```

3. Otevřete `HelloSvcutil.csproj` souboru ve svém editoru projektu, upravit `Project` elementu a přidejte [ `dotnet-svcutil` balíček NuGet](https://nuget.org/packages/dotnet-svcutil) jako odkaz nástroj příkazového řádku, pomocí následujícího kódu:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. Obnovit _dotnet svcutil_ balíček pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz takto:

```console
dotnet restore
```

5. Spustit _dotnet_ s _svcutil_ příkazu vygenerujte soubor webové služby odkaz následujícím způsobem:

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
Vygenerovaný soubor je uložena jako _HelloSvcutil/ServiceReference1/Reference.cs_. _Dotnet_svcutil_ nástroj také přidá do projektu odpovídající balíčky WCF vyžaduje kód proxy jako balíček odkazuje.

6. Obnovení balíčků WCF pomocí [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz takto:

```console
dotnet restore
```

7. Otevřete `Program.cs` souboru ve svém editoru, upravit `Main()` metodu a nahraďte automaticky generovaného kódu pomocí následující kód k vyvolání webové služby:

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. Spuštění aplikace pomocí [ `dotnet run` ](../tools/dotnet-run.md) příkaz takto:

```console
dotnet run
```
Měli byste vidět následující výstup: "Hello dotnet svcutil!"

Podrobný popis `dotnet-svcutil` nástroj parametry, vyvolání nástroje předání parametru nápovědy následujícím způsobem:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Další kroky

### <a name="feedback--questions"></a>Názory a dotazy

Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new). Můžete také zkontrolovat existující dotazy nebo problémy [v úložišti WCF na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Zpráva k vydání verze

* Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) aktualizované verze informace, včetně známých problémů.

### <a name="information"></a>Informace o

* [Balíček NuGet svcutil DotNet.](https://nuget.org/packages/dotnet-svcutil)
