---
title: Co je nového v rozhraní .NET Core 2.1
description: Další informace o nových funkcích v rozhraní .NET Core 2.1 nalezen.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 241ac0195e5edcd17ac67ea7ea0fac159af97414
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826929"
---
# <a name="whats-new-in-net-core-21"></a>Co je nového v rozhraní .NET Core 2.1

.NET core 2.1 obsahuje vylepšení a nové funkce v těchto oblastech:

- [Nástrojů](#tooling)
- [Dopředné posunutí](#roll-forward)
- [Nasazení](#deployment)
- [Kompatibilita sady Windows](#windows-compatibility-pack)
- [Vylepšení kompilace JIT](#jit-compiler-improvements)
- [Rozhraní API změny](#api-changes)

## <a name="tooling"></a>Nástrojů

.NET Core 2.1 SDK (v 2.1.300), nástrojů .NET Core 2.1, které jsou součástí obsahuje následující změny a vylepšení:

### <a name="build-performance-improvements"></a>Sestavení vylepšení výkonu

Hlavní fokus .NET Core 2.1 je zvýšení výkonu době sestavení, zejména pro přírůstkové sestavení. Tato vylepšení výkonu platí pro obě sestavení příkazového řádku pomocí `dotnet build` a sestavení v sadě Visual Studio. Některé jednotlivé oblasti zlepšování patří:

- Balíček asset překlad IP adres řešení pouze prostředky používané build, ne všechny prostředky.

- Ukládání do mezipaměti odkazy na sestavení.

- Použití sady SDK dlouho běžící sestavení serverů, které jsou procesy, které jsou rozmístěny napříč individuální `dotnet build` volání. Odstraňují potřebu JIT – kompilace velké bloky kódu pokaždé, když `dotnet build` běží. Vytvořit server pro procesy můžete automaticky ukončena s následující příkaz:

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nové příkazy rozhraní příkazového řádku

Několik nástrojů, které byly k dispozici pouze na jednotlivých projektů za použití [ `DotnetCliToolReference` ](../tools/extensibility.md) jsou nyní k dispozici jako součást .NET Core SDK. Mezi tyto nástroje patří:

- `dotnet watch` poskytuje sledovací proces systému souboru, který čeká na soubor, který chcete změnit před provedením určenou sadu příkazů. Následující příkaz například automaticky znovu sestaví aktuální projekt a generuje podrobný výstup, vždy, když je soubor v ní změny:

   ```console
   dotnet watch -- --verbose build
   ```
  
   Poznámka: `--` možnost, která předchází `--verbose` možnost. Ji vymezuje možnosti předán přímo `dotnet watch` příkaz z argumentů, které se předávají podřízená `dotnet` procesu. Bez toho `--verbose` možnost se vztahuje `dotnet watch` příkaz není `dotnet build` příkaz.
  
   Další informace najdete v tématu [ASP.NET Core vyvíjet aplikace pomocí sledování dotnet.](/aspnet/core/tutorials/dotnet-watch)

- `dotnet dev-certs` generuje a spravuje certifikáty používané během vývoje v aplikacích ASP.NET Core.

- `dotnet user-secrets` spravuje tajných klíčů v tajný úložiště uživatele v aplikacích ASP.NET Core.

- `dotnet sql-cache` vytvoří tabulku a indexy v databázi Microsoft SQL Server má být použit pro distribuované ukládání do mezipaměti.

- `dotnet ef` je nástroj pro správu databází, <xref:Microsoft.EntityFrameworkCore.DbContext> objekty a migrace v aplikacích Entity Framework Core. Další informace najdete v tématu [nástroje příkazového řádku .NET Core EF](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Globální nástroje

.NET core 2.1 podporuje *globální nástroje* – to znamená, vlastních nástrojů, které jsou k dispozici globálně z příkazového řádku. Model rozšiřitelnosti v předchozích verzích .NET Core zpřístupněn vlastních nástrojů na projektu na základě pouze pomocí [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).

Chcete-li nainstalovat nástroj globální, je použít [instalace nástroje pro dotnet](..\tools\dotnet-tool-install.md) příkaz. Příklad:

```console
dotnet tool install -g dotnetsay
```

Po instalaci nástroj můžete spustit z příkazového řádku zadáním názvu nástroj. Další informace najdete v tématu [.NET Core globální nástroje Přehled](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Nástroj pro správu pomocí `dotnet tool` příkaz

V rozhraní .NET Core SDK 2.1 (v 2.1.300), všechny operace nástroje pro použití `dotnet tool` příkaz. K dispozici jsou následující možnosti:

- [`dotnet tool install`](../tools/dotnet-tool-install.md) Chcete-li nainstalovat nástroj.

- [`dotnet tool update`](../tools/dotnet-tool-update.md) odinstalovat a znovu nainstalovat nástroj, který efektivně se aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md) seznam aktuálně nainstalovaných nástrojů.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) Chcete-li odinstalovat aktuálně nainstalovaného nástroje.

## <a name="roll-forward"></a>Dopředné posunutí

Všechny aplikace .NET Core od verze rozhraní .NET 2.0 základní automaticky Posunutí vpřed na nejnovější *podverze* nainstalovaná v systému. 

Od verze rozhraní .NET 2.0 jádra, pokud není k dispozici v době běhu verzi .NET Core, který byl aplikace vytvořené s nástroji, aplikace automaticky spouští nejnovější nainstalované *podverze* z .NET Core. Jinými slovy Pokud je aplikace vytvořené s .NET Core 2.0 a .NET Core 2.0 není v hostitelském systému, ale .NET Core 2.1, aplikace bude spuštěna s .NET Core 2.1.

> [!IMPORTANT]
> Toto chování úplné dopředné nezávisle na verze preview. Ani se nevztahuje na hlavní verze. Aplikace .NET Core 1.0 by například Posunutí vpřed .NET Core 2.0 nebo .NET Core 2.1.

Můžete také zakázat podverze dopředné posunutí v jednom ze tří způsobů:

- Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnnou prostředí na hodnotu 0.

- Přidejte následující řádek do souboru runtimeconfig.json:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Při použití [nástrojů příkazového řádku .NET Core](../tools/index.md), obsahují následující možnost pomocí příkazu .NET Core, například `run`:

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a>Nasazení

### <a name="self-contained-application-servicing"></a>Samostatný aplikace údržby

`dotnet publish` nyní publikuje nezávislý aplikace s verzí obsluhované runtime. Když publikujete samostatné aplikace pomocí .NET SDK 2.1 jádra (v 2.1.300), vaše aplikace obsahuje nejnovější verzi modulu runtime obsluhované známého této sady SDK. Při upgradu na nejnovější SDK, budete publikovat na nejnovější verzi modulu runtime .NET Core. To platí pro moduly runtime .NET Core 1.0 nebo novější.

Samostatná publikování závisí na modulu runtime verze na NuGet.org. Není nutné mít obsluhované modul runtime na váš počítač.

Pomocí .NET SDK 2.0 jádra, úplný a samostatný aplikace jsou publikovány s modulem runtime .NET Core 2.0.0 prostřednictvím je uvedeno jinou verzi `RuntimeFrameworkVersion` vlastnost. Pomocí této nové chování už musíte nastavit tuto vlastnost na vybrat vyšší verzi modulu runtime pro samostatné aplikace. Nejjednodušší způsob do budoucna, je vždy publikovat s .NET Core 2.1 SDK (v 2.1.300).

## <a name="windows-compatibility-pack"></a>Kompatibilita sady Windows

Pokud je to port existující kód z rozhraní .NET Framework na .NET Core, můžete použít [Windows kompatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Poskytuje přístup na 20 000 další rozhraní API, než je k dispozici v .NET Core. Tato rozhraní API obsahovat typy v <xref:System.Drawing?displayProperty="nameWithType"> obor názvů, <xref:System.Diagnostics.EventLog> třídy, rozhraní WMI, čítače výkonu, služby systému Windows a typy registru systému Windows a členů.

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

.NET core zahrnuje novou technologií kompilátoru JIT názvem *vrstvené kompilace* (také označované jako *Adaptivní optimalizace*), může výrazně zlepšit výkon. Nastavení přihlášení je vrstvené kompilace.

Jeden z nejdůležitějších úkolů provádí kompilátoru za běhu je optimalizace provádění kódu. Pro kód málo používané cesty ale kompilátor může trávit déle než modulu runtime stráví spuštěním kódu neoptimalizované optimalizace kódu. Vrstvený kompilace zavádí dvou fázích v JIT – kompilace:

- A **první úroveň**, který generuje kód co nejrychleji.

- A **druhé vrstvy**, který generuje optimalizovaného kódu pro tyto metody, které jsou spouštěny často. Druhé vrstvy kompilace se provádí současně pro lepší výkon.

Můžete se taky rozhodnout do vrstvené kompilace v některém ze dvou způsobů.

- Chcete-li vrstvené kompilace použít na všechny projekty, které používají .NET Core 2.1 SDK, nastavte následující proměnnou prostředí:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Chcete-li použít vrstvené kompilace na jednotlivých projektů, přidejte `<TieredCompilation>` vlastnost, která má `<PropertyGroup>` části souboru projektu nástroje MSBuild, jak ukazuje následující příklad:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Rozhraní API změny

### <a name="spant-and-memoryt"></a>`Span<T>` A `Memory<T>`

.NET core 2.1 obsahuje některé nové typy, které práci s poli a dalších typů paměti mnohem efektivnější. Nové typy patří:

- <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez těchto typů, při předávání takové položky jako část pole nebo jeho část vyrovnávací paměti budete muset vytvořit kopii některé část dat před jeho odesláním metodu. Tyto typy poskytují virtuální zobrazení data, která eliminuje potřebu další paměť přidělení a operace kopírování.

Následující příklad používá <xref:System.Span%601> instance zajistit virtuální zobrazení 10 prvky pole.

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a>Komprese Brotli

.NET core 2.1 přidává podporu pro Brotli komprese a dekomprese. Brotli je algoritmus pro obecné účely beze ztrát komprese, která je definována v [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a podporuje většina webových prohlížečů a hlavní webové servery. Můžete použít datový proud na základě <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> třídu nebo výkonné na základě rozpětí <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> a <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> třídy. Následující příklad ilustruje komprese s <xref:System.IO.Compression.BrotliStream> třídy:

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<xref:System.IO.Compression.BrotliStream> Chování je stejné jako <xref:System.IO.Compression.DeflateStream> a <xref:System.IO.Compression.GZipStream>, což usnadňuje převést kód, který volá tyto rozhraní API pro <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Kryptografie nové rozhraní API a vylepšení kryptografie

.NET core 2.1 zahrnuje množství vylepšení cryptography API:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> je k dispozici v balíčku System.Security.Cryptography.Pkcs. Implementace je stejný jako <xref:System.Security.Cryptography.Pkcs.SignedCms> – třída v rozhraní .NET Framework.

- Nové přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody přijímají identifikátor algoritmus hash povolit volající získat hodnoty kryptografického otisku certifikátu pomocí algoritmů než SHA-1.

- Nové <xref:System.Span%601>-založené na kryptografii rozhraní API jsou k dispozici pro použití algoritmu hash, klíčem HMAC, kryptografické náhodné generování čísel, generování podpisů asymetrické, zpracování asymetrické podpis a šifrování RSA.

- Výkon <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> je vylepšený o 15 % pomocí <xref:System.Span%601>– na základě implementace.

- Nové <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> třída obsahuje dvě nové metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> trvá pevné množství času se chcete vrátit všechny dva vstupy stejnou délku, takže je vhodné pro použití v kryptografických ověření předejdete přispívání do časování informace o kanálu straně.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> je rutinou mažou paměti, která nelze optimalizovat.

- Statické <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> metoda výplněmi <xref:System.Span%601> s náhodných hodnot.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Se teď podporuje na Linuxu a maxOS.

- Elliptic Curve Diffie-Hellman (ECDH) je nyní k dispozici v <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> třídy rodiny. Možnosti útoku je stejný jako v rozhraní .NET Framework.

- Instance vrácený <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> můžete zašifrovat nebo dešifrovat s OAEP pomocí hodnotu hash SHA-2, a také vygenerovat nebo ověřit podpisy pomocí RSA-PSS.

### <a name="sockets-improvements"></a>Vylepšení Sockets

.NET core zahrnuje nový typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>a přepsaná <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, které tvoří základ sítě vyšší úrovně rozhraní API.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, například je základem <xref:System.Net.Http.HttpClient> implementace. V předchozích verzích .NET Core jsou vyšší úrovně rozhraní API založené na nativní implementace sítě.

Implementace sockets byla zavedená v rozhraní .NET Core 2.1 má několik výhod:

- Zlepšování významně zvýšit výkon ve srovnání s předchozí implementací.

- Odstranění závislosti platformy, což zjednodušuje nasazení a údržby.

- Konzistentní chování pro všechny platformy .NET Core.

<xref:System.Net.Http.SocketsHttpHandler> je výchozí implementace v rozhraní .NET Core 2.1. Ale můžete nakonfigurovat aplikace pomocí starší <xref:System.Net.Http.HttpClientHandler> třída voláním <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> metoda:

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", False)
```

Můžete taky prostředí proměnnou pro vyjádření výslovného nesouhlasu pomocí soketů implementací na základě <xref:System.Net.Http.SocketsHttpHandler>. Chcete-li to provést, nastavte `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` buď `false` nebo rovna 0.

V systému Windows, můžete také použít <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, které závisí na nativní implementaci nebo <xref:System.Net.Http.SocketsHttpHandler> třída předáním instance třídy k <xref:System.Net.Http.HttpClient> konstruktor.

V systému macOS a Linux, můžete konfigurovat pouze <xref:System.Net.Http.HttpClient> na základě procesů. V systému Linux, je třeba nasadit [libcurl](https://curl.haxx.se/libcurl/) Pokud chcete použít starý <xref:System.Net.Http.HttpClient> implementace. (Je nainstalovaná s .NET Core 2.0.)

## <a name="see-also"></a>Viz také:

[Co je nového v .NET Core](index.md)  
[Nové funkce v EF základní 2.1](/ef/core/what-is-new/ef-core-2.1)  
[Co je nového v technologii ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
