---
title: Co je nového v .NET Core 2.1
description: Další informace o nových funkcích v rozhraní .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 54ace52fc6a8f4614c1f762b65453979bcb92c7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398865"
---
# <a name="whats-new-in-net-core-21"></a>Co je nového v .NET Core 2.1

.NET Core 2.1 obsahuje vylepšení a nové funkce v následujících oblastech:

- [Nástroje](#tooling)
- [Posunout vpřed](#roll-forward)
- [Nasazení](#deployment)
- [Sada Kompatibilita systému Windows](#windows-compatibility-pack)
- [Vylepšení kompilace JIT](#jit-compiler-improvements)
- [Změny rozhraní API](#api-changes)

## <a name="tooling"></a>Nástroje

Sada .NET Core 2.1 SDK (v 2.1.300), nástroj, který je součástí .NET Core 2.1, obsahuje následující změny a vylepšení:

### <a name="build-performance-improvements"></a>Vytváření vylepšení výkonu

Hlavním zaměřením .NET Core 2.1 je zlepšení výkonu sestavení, zejména pro přírůstkové sestavení. Tato vylepšení výkonu platí pro sestavení `dotnet build` příkazového řádku pomocí a sestavení v sadě Visual Studio. Některé jednotlivé oblasti zlepšení patří:

- Pro řešení aktiv balíčku řešení pouze prostředky používané sestavení, nikoli všechny prostředky.

- Ukládání odkazů na sestavení do mezipaměti.

- Použití dlouho běžících serverů sestavení sady SDK, což `dotnet build` jsou procesy, které se rozprostírají mezi jednotlivými vyvoláními. Eliminují potřebu JIT kompilovat `dotnet build` velké bloky kódu při každém spuštění. Procesy sestavení serveru lze automaticky ukončit pomocí následujícího příkazu:

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nové příkazy příkazu cli

Řada nástrojů, které byly k dispozici pouze `DotnetCliToolReference` na základě projektu pomocí jsou nyní k dispozici jako součást .NET Core SDK. Mezi tyto nástroje patří:

- `dotnet watch`Poskytuje sledovací proces systému souborů, který čeká na změnu souboru před provedením určené sady příkazů. Například následující příkaz automaticky znovu vytvoří aktuální projekt a generuje podrobný výstup při každé změně souboru v něm:

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   Všimněte `--` si možnosti, která předchází `--verbose` možnost. Vymezuje možnosti `dotnet watch` předané přímo příkazu z `dotnet` argumentů, které jsou předány podřízenému procesu. Bez ní `--verbose` se tato možnost `dotnet watch` vztahuje na `dotnet build` příkaz, nikoli na příkaz.
  
   Další informace najdete [v tématu Vývoj aplikací ASP.NET Core pomocí hodinek Dotnet](/aspnet/core/tutorials/dotnet-watch)Watch .

- `dotnet dev-certs`generuje a spravuje certifikáty používané při vývoji v ASP.NET základních aplikacích.

- `dotnet user-secrets`spravuje tajné klíče v úložišti tajných klíčů uživatele v ASP.NET základních aplikacích.

- `dotnet sql-cache`vytvoří tabulku a indexuje v databázi serveru Microsoft SQL Server, která se použije pro distribuované ukládání do mezipaměti.

- `dotnet ef`je nástroj pro správu <xref:Microsoft.EntityFrameworkCore.DbContext> databází, objektů a migrací v aplikacích Core frameworku entit. Další informace naleznete v tématu [EF Core .NET Nástroje příkazového řádku](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Globální nástroje

.NET Core 2.1 podporuje *globální nástroje* – to znamená vlastní nástroje, které jsou k dispozici globálně z příkazového řádku. Model rozšiřitelnosti v předchozích verzích rozhraní .NET Core zpřístupnil `DotnetCliToolReference`vlastní nástroje pro projekt pouze pomocí .

Chcete-li nainstalovat globální nástroj, použijte příkaz [instalace nástroje dotnet.](../tools/dotnet-tool-install.md) Například:

```dotnetcli
dotnet tool install -g dotnetsay
```

Po instalaci lze nástroj spustit z příkazového řádku zadáním názvu nástroje. Další informace naleznete v tématu [.NET Core Global Tools overview](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Správa nástrojů `dotnet tool` pomocí příkazu

V sdk.net core 2.1 sdk všechny nástroje operace použít `dotnet tool` příkaz. K dispozici jsou následující možnosti:

- [`dotnet tool install`](../tools/dotnet-tool-install.md)pro instalaci nástroje.

- [`dotnet tool update`](../tools/dotnet-tool-update.md)odinstalovat a znovu nainstalovat nástroj, který jej účinně aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md)do seznamu aktuálně nainstalovaných nástrojů.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)odinstalovat aktuálně nainstalované nástroje.

## <a name="roll-forward"></a>Posunout vpřed

Všechny aplikace .NET Core začínající na rozhraní .NET Core 2.0 se automaticky přepínají na nejnovější *dílčí verzi* nainstalovanou v systému.

Počínaje rozhraním .NET Core 2.0, pokud verze rozhraní .NET Core, se kterou byla aplikace vytvořena, není k dispozici za běhu, aplikace se automaticky spustí s nejnovější *nainstalovanou dílčí verzí* rozhraní .NET Core. Jinými slovy, pokud je aplikace vytvořena s rozhraním .NET Core 2.0 a rozhraní .NET Core 2.0 není v hostitelském systému k dispozici, ale je .NET Core 2.1, aplikace je spuštěna s rozhraním .NET Core 2.1.

> [!IMPORTANT]
> Toto chování pro přechod vpřed se nevztahuje na verze preview. Ve výchozím nastavení se také nevztahuje na hlavní verze, ale to lze změnit pomocí níže uvedených nastavení.

Toto chování můžete změnit změnou nastavení pro roll-forward na žádný kandidát sdílené rozhraní. Dostupná nastavení jsou:

- `0`- zakázat chování dílčí verze roll-forward. Při tomto nastavení se aplikace vytvořená pro rozhraní .NET Core 2.0.0 posune dopředu na .NET Core 2.0.1, ale ne na .NET Core 2.2.0 nebo .NET Core 3.0.0.
- `1`- povolit chování dílčí verze roll-forward. Toto je výchozí hodnota pro nastavení. Při tomto nastavení se aplikace vytvořená pro rozhraní .NET Core 2.0.0 posune dopředu buď na .NET Core 2.0.1 nebo .NET Core 2.2.0, v závislosti na tom, který z nich je nainstalován, ale nebude se posunout dopředu na .NET Core 3.0.0.
- `2`- povolit chování dílčí ch a hlavních verzí. Pokud je nastavena, jsou považovány i různé hlavní verze, takže aplikace vytvořená pro rozhraní .NET Core 2.0.0 se posune dopředu na .NET Core 3.0.0.

Toto nastavení můžete upravit libovolným ze tří způsobů:

- Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnnou prostředí na požadovanou hodnotu.

- Do souboru *.runtimeconfig.json* přidejte následující řádek s požadovanou hodnotou:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Při použití [rozhraní PŘÍKAZU .NET Core](../tools/index.md)přidejte do příkazu .NET `run`Core následující možnost s požadovanou hodnotou, například :

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Posun out verze opravy je nezávislý na tomto nastavení a provádí se po použití jakékoli potenciální vedlejší nebo hlavní verze.

## <a name="deployment"></a>Nasazení

### <a name="self-contained-application-servicing"></a>Samostatný servis aplikací

`dotnet publish`nyní publikuje samostatné aplikace s obsluhovnou runtime verzí. Při publikování samostatné aplikace s .NET Core 2.1 SDK (v 2.1.300), aplikace obsahuje nejnovější verzi runtime s obsluhou známou tímto sadou SDK. Při upgradu na nejnovější sadu SDK budete publikovat s nejnovější verzí za běhu .NET Core. To platí pro běhové časy .NET Core 1.0 a novější.

Samostatné publikování závisí na runtime verzích na NuGet.org. Není nutné mít v počítači servisní runtime.

Pomocí sady .NET Core 2.0 SDK jsou samostatné aplikace publikovány pomocí runtime .NET Core 2.0.0, pokud není prostřednictvím vlastnosti `RuntimeFrameworkVersion` zadána jiná verze. S tímto novým chováním již nebudete muset tuto vlastnost nastavit, abyste vybrali vyšší verzi runtime pro samostatnou aplikaci. Nejjednodušší přístup do budoucna je vždy publikovat s .NET Core 2.1 SDK (v 2.1.300).

Další informace naleznete [v tématu Samostatné nasazení runtime posun vpřed](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Sada Kompatibilita systému Windows

Při přenosu existujícího kódu z rozhraní .NET Framework do rozhraní .NET Core můžete použít [sadu Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Poskytuje přístup k 20 000 více rozhraní API, než jsou k dispozici v .NET Core. Tato api zahrnují typy <xref:System.Drawing?displayProperty=nameWithType> v oboru <xref:System.Diagnostics.EventLog> názvů, třídy, služby WMI, čítače výkonu, služby systému Windows a typy a členy registru systému Windows.

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

.NET Core obsahuje novou technologii kompilátoru JIT nazvanou *vrstvená kompilace (označovaná* také jako *adaptivní optimalizace),* která může výrazně zlepšit výkon. Vrstvená kompilace je nastavení opt-in.

Jedním z důležitých úkolů prováděných kompilátorem JIT je optimalizace spuštění kódu. Pro málo používané cesty kódu však kompilátor může strávit více času optimalizací kódu, než runtime stráví spuštěním neoptimalizovaného kódu. Vrstvená kompilace zavádí dvě fáze kompilace JIT:

- **První vrstva**, která generuje kód co nejrychleji.

- **Druhá vrstva**, která generuje optimalizovaný kód pro ty metody, které jsou často spouštěny. Druhá vrstva kompilace se provádí paralelně pro zvýšení výkonu.

Můžete se přihlásit do vrstvené kompilace v obou způsobech.

- Chcete-li použít vrstvenou kompilaci ve všech projektech, které používají sadu .NET Core 2.1 SDK, nastavte následující proměnnou prostředí:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Chcete-li použít vrstvenou kompilaci pro `<TieredCompilation>` jednotlivý `<PropertyGroup>` projekt, přidejte vlastnost do části souboru projektu MSBuild, jak ukazuje následující příklad:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Změny rozhraní API

### <a name="spant-and-memoryt"></a>`Span<T>` a `Memory<T>`

.NET Core 2.1 obsahuje některé nové typy, které usnadňují práci s poli a jinými typy paměti. Mezi nové typy patří:

- <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez těchto typů při předávání těchto položek jako část pole nebo část vyrovnávací paměti, je nutné vytvořit kopii některé části dat před předáním metodě. Tyto typy poskytují virtuální zobrazení těchto dat, které eliminuje potřebu další přidělení paměti a operace kopírování.

Následující příklad používá <xref:System.Span%601> <xref:System.Memory%601> a instance poskytnout virtuální zobrazení 10 prvků pole.

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Brotli komprese

.NET Core 2.1 přidává podporu pro kompresi a dekompresi Brotli. Brotli je univerzální bezeztrátový kompresní algoritmus, který je definován v [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a je podporován většinou webových prohlížečů a hlavních webových serverů. Můžete použít třídu <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> založenou na datovém proudu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> nebo <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> vysoce výkonné rozsah založené a třídy. Následující příklad ilustruje kompresi s třídou: <xref:System.IO.Compression.BrotliStream>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

Chování <xref:System.IO.Compression.BrotliStream> je stejné <xref:System.IO.Compression.DeflateStream> jako <xref:System.IO.Compression.GZipStream>a , což usnadňuje převod kódu, <xref:System.IO.Compression.BrotliStream>který volá tato api na .

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Nová rozhraní API kryptografie a vylepšení kryptografie

.NET Core 2.1 obsahuje řadu vylepšení rozhraní API kryptografie:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>je k dispozici v balíčku System.Security.Cryptography.Pkcs. Implementace je stejná <xref:System.Security.Cryptography.Pkcs.SignedCms> jako třída v rozhraní .NET Framework.

- Nové přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody přijmout identifikátor algoritmu hash umožnit volajícím získat hodnoty kryptografického otisku certifikátu pomocí algoritmů než SHA-1.

- Nová <xref:System.Span%601>kryptografická rozhraní API jsou k dispozici pro hašování, HMAC, kryptografické generování náhodných čísel, generování asymetrických podpisů, zpracování asymetrických podpisů a šifrování RSA.

- Výkon <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> se zlepšil a to asi o <xref:System.Span%601>15 % pomocí implementace založené na článku.

- Nová <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> třída obsahuje dvě nové metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>trvá pevně dobu vrátit pro všechny dva vstupy stejné délky, což je vhodné pro použití v kryptografické ověření, aby se zabránilo přispívání k časování informace o postranním kanálu.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>je rutina vymazání paměti, kterou nelze optimalizovat.

- Statická <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> metoda vyplní <xref:System.Span%601> náhodné hodnoty.

- Nyní <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> je podporován na Linuxu a macOS.

- Elliptic-Curve Diffie-Hellman (ECDH) je <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> nyní k dispozici v řadě rodiny. Plocha je stejná jako v rozhraní .NET Framework.

- Instance vrácená <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> pomocí aplikace OAEP pomocí metody OAEP pomocí výtahu SHA-2, stejně jako generování nebo ověřování podpisů pomocí RSA-PSS.

### <a name="sockets-improvements"></a>Vylepšení soketů

Jádro .NET obsahuje nový <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>typ a <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>přepsaný , které tvoří základ síťových rozhraní API vyšší úrovně.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, je například základem <xref:System.Net.Http.HttpClient> provádění. V předchozích verzích rozhraní .NET Core byla rozhraní API vyšší úrovně založena na nativních síťových implementacích.

Implementace soketů zavedená v rozhraní .NET Core 2.1 má řadu výhod:

- Významné zlepšení výkonu ve srovnání s předchozí implementací.

- Eliminace závislostí platformy, což zjednodušuje nasazení a obsluhu.

- Konzistentní chování na všech platformách .NET Core.

<xref:System.Net.Http.SocketsHttpHandler>je výchozí implementace v rozhraní .NET Core 2.1. Aplikaci však můžete nakonfigurovat <xref:System.Net.Http.HttpClientHandler> tak, aby <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> používala starší třídu voláním metody:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Proměnnou prostředí můžete také použít k odhlášení z <xref:System.Net.Http.SocketsHttpHandler>používání implementací soketů založených na aplikaci . Chcete-li to `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` provést, `false` nastavte buď nebo 0.

V systému Windows můžete <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>také použít , který spoléhá na <xref:System.Net.Http.SocketsHttpHandler> nativní implementaci nebo třídu <xref:System.Net.Http.HttpClient> předáním instance třídy konstruktoru.

V Linuxu a macOS <xref:System.Net.Http.HttpClient> můžete konfigurovat pouze na základě procesu. V systému Linux je třeba nasadit [libcurl,](https://curl.haxx.se/libcurl/) pokud chcete použít starou <xref:System.Net.Http.HttpClient> implementaci. (Je nainstalován s rozhraním .NET Core 2.0.)

### <a name="breaking-changes"></a>Změny způsobující chyby

Informace o narušujících změnách naleznete v [tématu Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).

## <a name="see-also"></a>Viz také

- [Co je nového v .NET Core](index.md)
- [Nové funkce v EF Core 2.1](/ef/core/what-is-new/ef-core-2.1)
- [Co je nového v ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
