---
title: Co je nového v .NET Core 2.1
description: Přečtěte si o nových funkcích, které najdete v .NET Core 2,1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 94f3db14046ad5d63975d0ca44425abed5d52062
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281534"
---
# <a name="whats-new-in-net-core-21"></a>Co je nového v .NET Core 2.1

.NET Core 2,1 obsahuje vylepšení a nové funkce v následujících oblastech:

- [Nástroje](#tooling)
- [Posunout nahoru](#roll-forward)
- [Nasazení](#deployment)
- [Sada Compatibility Pack pro Windows](#windows-compatibility-pack)
- [Vylepšení kompilace JIT](#jit-compiler-improvements)
- [Změny rozhraní API](#api-changes)

## <a name="tooling"></a>Nástroje

Sada SDK .NET Core 2,1 (v 2.1.300), nástroje, které jsou součástí .NET Core 2,1, obsahují tyto změny a vylepšení:

### <a name="build-performance-improvements"></a>Vylepšení výkonu sestavení

Hlavní zaměření rozhraní .NET Core 2,1 zvyšuje výkon při sestavování, zejména pro přírůstková sestavení. Tato vylepšení výkonu platí pro sestavení příkazového řádku pomocí `dotnet build` a pro sestavení v aplikaci Visual Studio. Mezi jednotlivé oblasti vylepšení patří:

- Pro účely řešení Asset Resolution vyřešte pouze prostředky využívané sestavením místo všech prostředků.

- Ukládání odkazů na sestavení do mezipaměti.

- Použití dlouhotrvajících serverů sestavení sady SDK, které jsou procesy, které jsou rozloženy mezi jednotlivá `dotnet build` volání. Eliminují potřebu JIT zkompilovat velké bloky kódu pokaždé, když `dotnet build` se spustí. Procesy sestavení serveru mohou být automaticky ukončeny pomocí následujícího příkazu:

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nové příkazy rozhraní příkazového řádku

K dispozici je řada nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí, `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK. Mezi tyto nástroje patří:

- `dotnet watch`poskytuje sledovací proces systému souborů, který čeká na změnu souboru před spuštěním určené sady příkazů. Například následující příkaz automaticky znovu sestaví aktuální projekt a generuje podrobný výstup pokaždé, když se změní soubor:

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   Všimněte si `--` Možnosti, která předchází této `--verbose` Možnosti. Omezuje možnosti předané přímo na `dotnet watch` příkaz z argumentů, které jsou předány podřízenému `dotnet` procesu. Bez této `--verbose` možnosti platí pro `dotnet watch` příkaz, nikoli `dotnet build` příkaz.
  
   Další informace najdete v tématu [vývoj aplikací ASP.NET Core pomocí příkazu dotnet Watch](/aspnet/core/tutorials/dotnet-watch).

- `dotnet dev-certs`generuje a spravuje certifikáty používané během vývoje v aplikacích ASP.NET Core.

- `dotnet user-secrets`spravuje tajné klíče v úložišti tajného uživatele v aplikacích ASP.NET Core.

- `dotnet sql-cache`Vytvoří tabulku a indexy v databázi Microsoft SQL Server, která se má použít pro distribuované ukládání do mezipaměti.

- `dotnet ef`je nástroj pro správu databází, <xref:Microsoft.EntityFrameworkCore.DbContext> objektů a migrací v aplikacích Entity Framework Core. Další informace najdete v tématu [EF Core nástroje příkazového řádku .NET](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Globální nástroje

.NET Core 2,1 podporuje *globální nástroje* – tedy vlastní nástroje, které jsou k dispozici globálně z příkazového řádku. Model rozšiřitelnosti v předchozích verzích rozhraní .NET Core, které jsou k dispozici pro jednotlivé projekty, pouze pomocí nástroje `DotnetCliToolReference` .

K instalaci globálního nástroje použijte příkaz [dotnet Tool Install](../tools/dotnet-tool-install.md) . Příklad:

```dotnetcli
dotnet tool install -g dotnetsay
```

Po instalaci můžete nástroj spustit z příkazového řádku zadáním názvu nástroje. Další informace najdete v tématu [Přehled globálních nástrojů .NET Core](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Správa nástrojů pomocí `dotnet tool` příkazu

V sadě .NET Core 2,1 SDK všechny operace nástrojů používají `dotnet tool` příkaz. Dostupné jsou tyto možnosti:

- [`dotnet tool install`](../tools/dotnet-tool-install.md)pro instalaci nástroje.

- [`dotnet tool update`](../tools/dotnet-tool-update.md)k odinstalaci a přeinstalaci nástroje, který ji efektivně aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md)k vypsání aktuálně nainstalovaných nástrojů.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)k odinstalaci aktuálně nainstalovaných nástrojů.

## <a name="roll-forward"></a>Posunout nahoru

Všechny aplikace .NET Core počínaje platformou .NET Core 2,0 se automaticky předají do nejnovější *dílčí verze* nainstalované v systému.

Od verze .NET Core 2,0, pokud není k dispozici verze .NET Core, se kterou byla aplikace sestavena v době běhu, aplikace se automaticky spustí s nejnovější nainstalovanou *podverzí* rozhraní .NET Core. Jinými slovy, pokud je aplikace sestavená pomocí .NET Core 2,0 a .NET Core 2,0 není v hostitelském systému k dispozici, ale .NET Core 2,1 je, aplikace se spouští s .NET Core 2,1.

> [!IMPORTANT]
> Toto chování při přeposílání se nevztahuje na verze Preview. Ve výchozím nastavení se ani na hlavní verze nevztahují, ale dá se změnit pomocí níže uvedených nastavení.

Toto chování můžete upravit tak, že změníte nastavení pro přeposílání na žádné kandidátské sdílené rozhraní. K dispozici jsou následující nastavení:

- `0`– Zakažte chování při přeposílání dílčí verze. S tímto nastavením bude aplikace vytvořená pro .NET Core 2.0.0 předána do .NET Core 2.0.1, ale ne do .NET Core 2.2.0 nebo .NET Core 3.0.0.
- `1`– povolí chování při přeposílání dílčí verze. Toto je výchozí hodnota pro nastavení. S tímto nastavením se aplikace sestavená pro .NET Core 2.0.0 bude převádět na rozhraní .NET Core 2.0.1 nebo .NET Core 2.2.0, podle toho, která z nich je nainstalovaná, ale nebude se převádět do .NET Core 3.0.0.
- `2`– umožňuje povolit menší a hlavní verzi – chování při přeposílání. V případě, že je nastavena i jiná hlavní verze, bude aplikace vytvořená pro .NET Core 2.0.0 předána do .NET Core 3.0.0.

Toto nastavení můžete upravit některým ze tří způsobů:

- Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnnou prostředí na požadovanou hodnotu.

- Přidejte následující řádek s požadovanou hodnotou do *.runtimeconfig.js* souboru:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Při použití [.NET Core CLI](../tools/index.md)přidejte následující možnost s požadovanou hodnotou do příkazu .NET Core, například `run` :

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Přeposílání opravné verze je nezávisle na tomto nastavení a je provedeno po použití jakékoli případné nepatrné nebo hlavní verze posunutí.

## <a name="deployment"></a>Nasazení

### <a name="self-contained-application-servicing"></a>Samoobslužná Údržba aplikací

`dotnet publish`nyní publikuje samostatné aplikace s verzí modulu runtime, který je součástí služby. Když publikujete samostatnou aplikaci se sadou SDK .NET Core 2,1 (v 2.1.300), vaše aplikace zahrnuje nejnovější verzi služby runtime známou danou sadou SDK. Když upgradujete na nejnovější sadu SDK, publikujete s nejnovější verzí modulu runtime .NET Core. To platí pro modul runtime .NET Core 1,0 a novější.

Samoobslužné publikování spoléhá na verze modulu runtime v NuGet.org. V počítači nemusíte mít službu runtime, která je v provozu.

Pomocí sady .NET Core 2,0 SDK jsou samostatně obsažené aplikace publikovány s modulem runtime .NET Core 2.0.0, pokud není zadána jiná verze prostřednictvím `RuntimeFrameworkVersion` Vlastnosti. S tímto novým chováním už nebudete muset tuto vlastnost nastavovat, aby se pro samostatnou aplikaci vybrala vyšší verze modulu runtime. Nejjednodušší způsob, jak dál, je publikovat vždy pomocí .NET Core 2,1 SDK (v 2.1.300).

Další informace najdete v tématu implementace [modulu runtime pro samostatné nasazení](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Sada Compatibility Pack pro Windows

Při portování existujícího kódu z .NET Framework do .NET Core můžete použít [sadu Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Poskytuje přístup k 20 000 více rozhraním API, než je k dispozici v .NET Core. Tato rozhraní API zahrnují typy v <xref:System.Drawing?displayProperty=nameWithType> oboru názvů, <xref:System.Diagnostics.EventLog> třídy, rozhraní WMI, čítače výkonu, služby systému Windows a typy a členy registru systému Windows.

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

.NET Core zahrnuje novou technologii kompilátoru JIT nazvanou *vrstvená kompilace* (označovaná také jako *adaptivní optimalizace*), která může významně zlepšit výkon. Vrstvená kompilace je nastavení pro výslovný souhlas.

Jedním z důležitých úloh prováděných kompilátorem JIT je optimalizace provádění kódu. Pro málo používané cesty kódu však může kompilátor strávit více času optimalizací kódu, než modul runtime stráví neoptimalizovaným kódem. Vrstvená kompilace přináší dvě fáze kompilace JIT:

- **První vrstva**, která generuje kód co nejrychleji.

- **Druhá vrstva**, která generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často. Druhá vrstva kompilace se paralelně provádí za účelem zvýšení výkonu.

Můžete vyjádřit souhlas s vrstvenými kompilacemi jedním ze dvou způsobů.

- Chcete-li použít vrstvenou kompilaci ve všech projektech, které používají sadu .NET Core 2,1 SDK, nastavte následující proměnnou prostředí:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Chcete-li použít vrstvenou kompilaci pro každý projekt, přidejte `<TieredCompilation>` vlastnost do `<PropertyGroup>` oddílu souboru projektu MSBuild, jak ukazuje následující příklad:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Změny rozhraní API

### <a name="spant-and-memoryt"></a>`Span<T>` a `Memory<T>`

.NET Core 2,1 obsahuje některé nové typy, které umožňují pracovat s poli a dalšími typy paměti mnohem efektivnější. Mezi nové typy patří:

- <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez těchto typů při předávání takových položek jako části pole nebo oddílu vyrovnávací paměti je nutné vytvořit kopii určité části dat před předáním do metody. Tyto typy poskytují virtuální pohled na tato data, který eliminuje nutnost dodatečného přidělení paměti a operací kopírování.

V následujícím příkladu se používá <xref:System.Span%601> <xref:System.Memory%601> instance a k poskytnutí virtuálního zobrazení 10 prvků pole.

[!code-csharp[Span\<T>](./snippets/dotnet-core-2-1/csharp/program.cs)]

[!code-vb[Memory\<T>](./snippets/dotnet-core-2-1/vb/program.vb)]

### <a name="brotli-compression"></a>Komprese Brotli

.NET Core 2,1 přidává podporu pro kompresi a dekompresi Brotli. Brotli je univerzální bezeztrátová kompresní algoritmus, který je definovaný v [dokumentu RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a který podporuje většina webových prohlížečů a hlavních webových serverů. Můžete použít třídu založenou na datovém proudu <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> nebo vysoce výkonné rozsahy <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> a <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> třídy. Následující příklad znázorňuje kompresi s <xref:System.IO.Compression.BrotliStream> třídou:

[!code-csharp[Brotli compression](./snippets/dotnet-core-2-1/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](./snippets/dotnet-core-2-1/vb/brotli.vb#1)]

<xref:System.IO.Compression.BrotliStream>Chování je stejné jako <xref:System.IO.Compression.DeflateStream> a <xref:System.IO.Compression.GZipStream> , což usnadňuje převod kódu, který volá tato rozhraní API na <xref:System.IO.Compression.BrotliStream> .

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Nová kryptografická rozhraní API a kryptografická vylepšení

.NET Core 2,1 obsahuje řadu vylepšení rozhraní API kryptografie:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>je k dispozici v balíčku System. Security. Cryptography. PKCS. Implementace je stejná jako <xref:System.Security.Cryptography.Pkcs.SignedCms> Třída v .NET Framework.

- Nová přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metod a přijímají identifikátor algoritmu hash, aby mohli volajícím získat hodnoty kryptografického otisku certifikátu pomocí jiných algoritmů než SHA-1.

- Nová <xref:System.Span%601> kryptografická rozhraní API jsou k dispozici pro generování hodnot hash, HMAC, kryptografické generování náhodných čísel, generování asymetrických podpisů, zpracování asymetrického podpisu a šifrování RSA.

- Výkon systému <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> byl vylepšen o 15% pomocí <xref:System.Span%601> implementace založené na.

- Nová <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> Třída obsahuje dvě nové metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>vybere pevně určenou dobu pro všechny dva vstupy stejné délky, což usnadňuje použití v kryptografickém ověřování, aby se předešlo tomu, že by bylo možné přispívat k načasování informací o kanálu na straně.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>je rutina pro mazání paměti, která nemůže být optimalizována.

- Statická <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> Metoda vyplní <xref:System.Span%601> náhodné hodnoty.

- Rozhraní <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> se teď podporuje v systémech Linux a MacOS.

- Eliptická Vlnová třída Diffie-Hellman (ECDH) je teď dostupná v <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> rodině tříd. Oblast Surface je stejná jako v .NET Framework.

- Instance vrácená nástrojem <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> může šifrovat nebo dešifrovat pomocí výplně OAEP s využitím algoritmu SHA-2 a generovat nebo ověřovat podpisy pomocí technologie RSA-PSS.

### <a name="sockets-improvements"></a>Vylepšení soketů

.NET Core obsahuje nový typ, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> a přepsaný <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> , který tvoří základ rozhraní API sítě vyšší úrovně.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>Například je základem <xref:System.Net.Http.HttpClient> implementace. V předchozích verzích rozhraní .NET Core rozhraní API na vyšší úrovni byly založeny na nativních implementacích sítě.

Implementace soketů představená v .NET Core 2,1 má několik výhod:

- Významné zlepšení výkonu při porovnání s předchozí implementací.

- Eliminujte závislosti platforem, což zjednodušuje nasazení a údržbu.

- Konzistentní chování napříč všemi platformami .NET Core.

<xref:System.Net.Http.SocketsHttpHandler>je výchozí implementací v rozhraní .NET Core 2,1. Můžete však nakonfigurovat aplikaci tak, aby používala starší <xref:System.Net.Http.HttpClientHandler> třídu voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Můžete také použít proměnnou prostředí pro výslovný souhlas s používáním implementací soketů založených na <xref:System.Net.Http.SocketsHttpHandler> . To provedete tak, že nastavíte hodnotu `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` na `false` nebo 0.

V systému Windows můžete také zvolit použití <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType> , který spoléhá na nativní implementaci, nebo na <xref:System.Net.Http.SocketsHttpHandler> třídu předáním instance třídy do <xref:System.Net.Http.HttpClient> konstruktoru.

V systémech Linux a macOS můžete nakonfigurovat pouze <xref:System.Net.Http.HttpClient> jednotlivé procesy. Pokud chcete použít starou implementaci, musíte v systému Linux nasadit [libcurl](https://curl.haxx.se/libcurl/) <xref:System.Net.Http.HttpClient> . (Instaluje se s .NET Core 2,0.)

### <a name="breaking-changes"></a>Změny způsobující chyby

Informace o zásadních změnách najdete v tématu zásadní [změny migrace z verze 2,0 na 2,1](../compatibility/2.0-2.1.md).

## <a name="see-also"></a>Viz také

- [Co je nového v .NET Core 3.1](dotnet-core-3-1.md)
- [Nové funkce v EF Core 2,1](/ef/core/what-is-new/ef-core-2.1)
- [Co je nového v ASP.NET Core 2,1](/aspnet/core/aspnetcore-2.1)
