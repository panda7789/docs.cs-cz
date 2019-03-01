---
title: Co je nového v .NET Core 2.1
description: Informace o nových funkcích v .NET Core 2.1.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 10/10/2018
ms.openlocfilehash: e28ff83d673951a978e24d9c89621fbbe950f50e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975209"
---
# <a name="whats-new-in-net-core-21"></a>Co je nového v .NET Core 2.1

.NET core 2.1 obsahuje vylepšení a nových funkcí v těchto oblastech:

- [Nástroje](#tooling)
- [Posunout vpřed](#roll-forward)
- [Nasazení](#deployment)
- [Windows Compatibility Pack](#windows-compatibility-pack)
- [Vylepšení kompilace JIT](#jit-compiler-improvements)
- [Změny rozhraní API](#api-changes)

## <a name="tooling"></a>Nástroje

.NET Core 2.1 SDK (v 2.1.300), nástroje, které jsou součástí rozhraní .NET Core 2.1 obsahuje následující změny a vylepšení:

### <a name="build-performance-improvements"></a>Vylepšení výkonu sestavení

Hlavní fokus .NET Core 2.1 je zkracuje čas sestavení, zejména pro přírůstkové sestavení. Tato vylepšení výkonu platí pro obě sestavení příkazového řádku pomocí `dotnet build` a sestavení v sadě Visual Studio. Některé jednotlivé oblasti vylepšení patří:

- Rozlišení prostředků balíčku řešení pouze prostředky používané sestavení, ne všechny prostředky.

- Ukládání do mezipaměti odkazy na sestavení.

- Použití sady SDK dlouho probíhající sestavení servery, které jsou procesy, které jsou rozmístěny napříč jednotlivých `dotnet build` volání. Tyto funkce odstraňují potřebu JIT-kompilovat velkých bloků kódu pokaždé, když `dotnet build` běží. Buildovací server, které procesy mohou automaticky ukončeny následujícím příkazem:

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nové příkazy rozhraní příkazového řádku

Různé nástroje, které byly k dispozici pouze v jednotlivých projektů pomocí [ `DotnetCliToolReference` ](../tools/extensibility.md) jsou teď k dispozici jako součást sady .NET Core SDK. Mezi tyto nástroje patří:

- `dotnet watch` poskytuje sledování systému souborů, které čeká na soubor, chcete-li změnit před spuštěním určenou sadu příkazů. Následující příkaz například automaticky znovu sestaví projekt a vygeneruje podrobný výstup pokaždé, když se změní soubor v ní:

   ```console
   dotnet watch -- --verbose build
   ```

   Poznámka: `--` možnost, která předchází `--verbose` možnost. Vymezuje možnosti předané přímo `dotnet watch` z argumentů, které jsou předány do podřízeného `dotnet` procesu. Bez toho `--verbose` možnost se vztahuje `dotnet watch` příkaz nebyl `dotnet build` příkazu.
  
   Další informace najdete v tématu [aplikace vyvíjet ASP.NET Core s využitím dotnet watch](/aspnet/core/tutorials/dotnet-watch)

- `dotnet dev-certs` generuje a spravuje certifikáty používané při vývoji aplikace ASP.NET Core.

- `dotnet user-secrets` slouží ke správě tajných kódů v úložišti tajných kódů uživatelů v aplikacích ASP.NET Core.

- `dotnet sql-cache` vytvoří tabulky a indexy v databázi Microsoft SQL serveru, který má být použit pro distribuované ukládání do mezipaměti.

- `dotnet ef` je nástroj pro správu databází, <xref:Microsoft.EntityFrameworkCore.DbContext> objekty a migrace v aplikacích Entity Framework Core. Další informace najdete v tématu [nástroje příkazového řádku .NET Core EF](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Globální nástroje

.NET core 2.1 podporuje *globální nástroje* – to znamená, vlastních nástrojů, které jsou k dispozici globálně z příkazového řádku. Model rozšiřitelnosti v předchozích verzích .NET Core zpřístupněn vlastních nástrojů na základě jednotlivých projektů pouze pomocí [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).

Instalovat nástroj globální, použijte [instalace nástrojů dotnet](../tools/dotnet-tool-install.md) příkazu. Příklad:

```console
dotnet tool install -g dotnetsay
```

Po instalaci, můžete nástroj spustit z příkazového řádku tak, že zadáte název nástroje. Další informace najdete v tématu [globální nástroje .NET Core přehled](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Nástroj pro správu s `dotnet tool` příkaz

V .NET Core SDK 2.1 a použít všechny operace nástroje `dotnet tool` příkazu. Jsou k dispozici následující možnosti:

- [`dotnet tool install`](../tools/dotnet-tool-install.md) Chcete-li nainstalovat nástroj.

- [`dotnet tool update`](../tools/dotnet-tool-update.md) Chcete-li odinstalovat a znovu nainstalovat nástroj, který efektivně aktualizuje.

- [`dotnet tool list`](../tools/dotnet-tool-list.md) seznam aktuálně nainstalovaných nástrojů.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) Odinstalace nástrojů pro aktuálně nainstalovanou.

## <a name="roll-forward"></a>Posunout vpřed

Všechny aplikace .NET Core od verze rozhraní .NET Core 2.0 automaticky posunout vpřed na nejnovější verzi *podverze* nainstalované v systému.

Počínaje .NET Core 2.0, pokud není k dispozici za běhu verze .NET Core, která byla aplikace vytvořena, aplikace automaticky spouští nainstaluje *podverze* .NET Core. Jinými slovy Pokud je aplikace sestavena s .NET Core 2.0 a .NET Core 2.0 není k dispozici v hostitelském systému, ale je .NET Core 2.1, aplikace bude spuštěna s .NET Core 2.1.

> [!IMPORTANT]
> Toto chování vpřed neplatí pro verze preview. Ve výchozím nastavení také informace neplatí pro hlavní verze, ale dá se změnit na nastavení uvedená níže.

Toto chování můžete upravit tak, že změníte nastavení vpřed v žádné sdílené architektuře Release candidate. Jsou k dispozici nastavení:
- `0` -podverze vpřed chování zakázat. S tímto nastavením aplikace sestavené pro .NET Core 2.0.0 se posunout vpřed až po .NET Core 2.0.1, ale ne k .NET Core 2.2.0 nebo .NET Core 3.0.0.
- `1` -povolit chování vpřed podverze. Toto je výchozí hodnota pro nastavení. S tímto nastavením aplikace sestavené pro .NET Core 2.0.0 bude vrácen předat buď .NET Core 2.0.1 nebo .NET Core 2.2.0, podle toho, která je nainstalovaná jedna, ale nebude až po .NET Core 3.0.0 posunout vpřed.
- `2` -povolit chování vpřed vedlejší a hlavní verze. Pokud jsou považovány za nastaveno, dokonce i jiné hlavní verze, takže aplikace vytvořené pro .NET Core 2.0.0 se posunout vpřed až po .NET Core 3.0.0.

Můžete upravit toto nastavení v libovolné ze tří způsobů:

- Nastavte `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` proměnné prostředí na požadovanou hodnotu.

- Přidejte následující řádek s hodnotou požadované do `runtimeconfig.json` souboru:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Při použití [nástroje rozhraní příkazového řádku .NET Core](../tools/index.md), jako například přidat následující možnost s požadovanou hodnotu příkazu .NET Core `run`:

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Vrácení verze opravy vpřed je nezávislý na toto nastavení a je proveden po menších potenciální nebo pokud je použita hlavní verze Posunutí vpřed.

## <a name="deployment"></a>Nasazení

### <a name="self-contained-application-servicing"></a>Údržba samostatné aplikace

`dotnet publish` nyní publikuje samostatné aplikace s obsluhované modulem runtime verze. Při publikování samostatné aplikace pomocí sady .NET Core 2.1 SDK (v 2.1.300), vaše aplikace obsahuje nejnovější verze modulu runtime obsluhované platná pro tuto sadu SDK. Když upgradujete na nejnovější sadu SDK, budete publikovat pomocí nejnovější verze modulu runtime .NET Core. To platí pro moduly runtime .NET Core 1.0 nebo novější.

Samostatné publikování se spoléhá na verze modulu runtime na NuGet.org. Nemusíte mít obsluhované runtime na vašem počítači.

Pomocí sady .NET Core 2.0 SDK, samostatné aplikace jsou publikované s modulem runtime .NET Core 2.0.0 jinou verzi není určena prostřednictvím `RuntimeFrameworkVersion` vlastnost. S toto nové chování už nebude potřeba nastavte tuto vlastnost na zvolte vyšší verze modulu runtime pro samostatné aplikace. Nejjednodušší způsob do budoucna, je vždy publikovat s .NET Core 2.1 SDK (v 2.1.300).

Další informace najdete v tématu [samostatná nasazení modulu runtime dopředné posunutí](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Windows Compatibility Pack

Když portujete existující kód z rozhraní .NET Framework do .NET Core, můžete použít [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Poskytuje přístup k 20 000 další rozhraní API, než je k dispozici v .NET Core. Tato rozhraní API patří typy v <xref:System.Drawing?displayProperty=nameWithType> obor názvů, <xref:System.Diagnostics.EventLog> třídy, rozhraní WMI, čítače výkonu, služby Windows a Windows registru typy a členy.

## <a name="jit-compiler-improvements"></a>Vylepšení kompilátoru JIT

.NET core zahrnuje novou technologii kompilátor JIT volá *vrstvené kompilace* (označované také jako *Adaptivní optimalizace*), který může výrazně zlepšit výkon. Nastavení přihlášení je vrstvený kompilace.

Mezi důležité úlohy prováděné kompilátorem JIT je optimalizace spuštění kódu. Cesty málo používané kódu ale může kompilátor věnovat víc času optimalizace kódu, než modul runtime stráví spuštěním neoptimalizované kódu. Vrstvené kompilace zavádí dvě fáze kompilace JIT:

- A **první úroveň**, který generuje kód co nejrychleji.

- A **druhé vrstvy**, který generuje optimalizovaný kód pro tyto metody, které jsou spouštěny často. Druhá vrstva kompilace provádí paralelní pro lepší výkon.

Můžete se rozhodnout do vrstvené kompilace v některém ze dvou způsobů.

- Pokud chcete použít ve všech projektech, které používají sadu .NET Core 2.1 SDK vrstvenou kompilace, nastavte následující proměnné prostředí:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Použití vrstveného kompilace na základě jednotlivých projektů, přidejte `<TieredCompilation>` vlastnost `<PropertyGroup>` část souboru projektu MSBuild, jako v následujícím příkladu:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Změny rozhraní API

### <a name="spant-and-memoryt"></a>`Span<T>` a `Memory<T>`

.NET core 2.1 zahrnuje několik nových typů, které usnadňuje práci s poli a jiné druhy paměti mnohem efektivnější. Nové typy patří:

- <xref:System.Span%601?displayProperty=nameWithType> a <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> a <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bez těchto typů, při předávání takové položky jako část pole nebo jeho část vyrovnávací paměti budete muset vytvořit kopii nějakou část dat před předáním na metodu. Tyto typy poskytují virtuální zobrazení data, která eliminuje potřebu další paměť přidělení a operací kopírování.

Následující příklad používá <xref:System.Span%601> a <xref:System.Memory%601> instance virtuální zviditelňují 10 prvků pole.

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!CODE-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Brotli komprese

.NET core 2.1 přidává podporu pro Brotli komprese a dekomprese. Brotli je algoritmus pro obecné účely beze ztrát komprese, který je definován v [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) a podporuje většina webových prohlížečů a hlavní webové servery. Můžete použít datový proud podle <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> třídy nebo vysoce výkonné založených na rozsahu <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> a <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> třídy. Následující příklad ukazuje komprese se <xref:System.IO.Compression.BrotliStream> třídy:

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<xref:System.IO.Compression.BrotliStream> Chování je stejné jako <xref:System.IO.Compression.DeflateStream> a <xref:System.IO.Compression.GZipStream>, což usnadňuje převést kód, který volá tato rozhraní API pro <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Šifrování nových rozhraní API a vylepšení kryptografie

.NET core 2.1 obsahuje četná vylepšení rozhraní API kryptografie:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> je k dispozici v balíčku System.Security.Cryptography.Pkcs. Implementace je stejné jako <xref:System.Security.Cryptography.Pkcs.SignedCms> třídy v rozhraní .NET Framework.

- Nové přetížení <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> metody přijímají identifikátor algoritmu hash a umožnit tak volajícím získat hodnoty kryptografického otisku certifikátu pomocí algoritmů než SHA-1.

- Nové <xref:System.Span%601>-založené na kryptografii rozhraní API jsou k dispozici pro vytvoření hodnoty hash, HMAC kryptografických náhodné generování čísel, generování asymetrického podpisu, zpracování asymetrického podpisu a šifrování RSA.

- Výkon <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> je vylepšené o 15 % pomocí <xref:System.Span%601>– na základě implementace.

- Nové <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> třída obsahuje dvě nové metody:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> používá pevné množství času má být vrácen pro jakékoli dva vstupy stejnou délku, která je vhodná pro použití v ověření šifrování, aby přispívání do vypršení časového limitu na straně kanálu informace.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> je paměť vymazání rutinu, která nemůže být optimalizované.

- Statické <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> metoda výplně <xref:System.Span%601> s náhodné hodnoty.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Je nyní podporována v systému Linux a maxOS.

- Skupina Diffie-Hellman eliptické křivky (ECDH) je teď dostupná v <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> třídy řady. Styčné plochy je stejný jako v rozhraní .NET Framework.

- Instanci vrácenou <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> můžete šifrování nebo dešifrování pomocí OAEP pomocí algoritmu SHA-2 digest, jakož i generovat nebo ověřování podpisů pomocí RSA služby PSS.

### <a name="sockets-improvements"></a>Vylepšení Sockets

.NET core zahrnuje nový typ <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>a přepsaný <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, které tvoří základ sítí vyšší úrovně rozhraní API.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, například je základem <xref:System.Net.Http.HttpClient> implementace. V předchozích verzích .NET Core byly vyšší úrovně rozhraní API podle nativní implementace sítě.

Implementaci soketů zavedena v rozhraní .NET Core 2.1 má několik výhod:

- Významné výkonnostní zlepšení ve srovnání s předchozím implementací.

- Úplného oproštění od závislostí platformy, která zjednodušuje nasazení a obsluhy.

- Konzistentní chování na všech platformách .NET Core.

<xref:System.Net.Http.SocketsHttpHandler> je výchozí implementace v .NET Core 2.1. Ale můžete nakonfigurovat vaší aplikaci použít starší <xref:System.Net.Http.HttpClientHandler> třídy voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Můžete použít také prostředí proměnnou můžete kdykoliv zrušit pomocí soketů implementací na základě <xref:System.Net.Http.SocketsHttpHandler>. Chcete-li to provést, nastavte `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` buď `false` nebo 0.

Na Windows, můžete také použít <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, které spoléhá na nativní implementaci nebo <xref:System.Net.Http.SocketsHttpHandler> třídy to předáním instance třídy, která se <xref:System.Net.Http.HttpClient> konstruktoru.

V Linuxu a macOS, můžete konfigurovat pouze <xref:System.Net.Http.HttpClient> na základě na úrovni jednotlivého procesu. V systému Linux, budete muset nasadit [libcurl](https://curl.haxx.se/libcurl/) Pokud chcete používat starý <xref:System.Net.Http.HttpClient> implementace. (To se instaluje s .NET Core 2.0).

## <a name="see-also"></a>Viz také:

- [Co je nového v .NET Core](index.md)
- [Novinky v EF Core 2.1](/ef/core/what-is-new/ef-core-2.1)
- [Co je nového v ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
