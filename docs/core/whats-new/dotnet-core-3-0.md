---
title: Co je nového v .NET Core 3.0
description: Informace o nových funkcích v rozhraní .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 3ca833031eb8bb0f43a334f833f2e0075842d57d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155480"
---
# <a name="whats-new-in-net-core-30-preview-1"></a>Co je nového v .NET Core 3.0 (ve verzi Preview 1)

Tento článek popisuje, co je nového v .NET Core 3.0 (ve verzi preview 1). Jedním z největších vylepšení je podpora aplikací klasické pracovní plochy Windows (jenom Windows). S využitím .NET Core 3.0 komponenty s názvem Windows Desktop, můžete port aplikace Windows Forms Windows Presentation Foundation (WPF). Aby bylo jasno, komponenta Windows Desktop se podporuje jenom na Windows. Další informace najdete v části [Windows desktop](#windows-desktop) níže.

Přidává podporu pro .NET core 3.0 C# 8.0.

[Stáhnout a začít pracovat s .NET Core 3 Preview 1](https://aka.ms/netcore3download) teď na Windows, Mac a Linux. Zobrazí se podrobné informace o verzi v [poznámky k verzi .NET Core 3 Preview 1](https://aka.ms/netcore3releasenotes).

Další informace najdete v tématu [.NET Core 3.0 ve verzi Preview 1 oznámení](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).

## <a name="net-standard-21"></a>.NET standard 2.1

.NET core 3.0 implementuje .NET Standard 2.1.

## <a name="default-executables"></a>Výchozí spustitelné soubory

.NET core teď bude vytvářet spustitelné soubory ve výchozím nastavení. Toto je nová pro aplikace, které používají globálně nainstalovanou verzi .NET Core. Až doteď jenom [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) měl spustitelné soubory.

Během `dotnet build` nebo `dotnet publish`, spustitelný soubor je vytvořen, za předpokladu, který odpovídá prostředí a platforma sady SDK, kterou používáte. Můžete očekávat, že stejné operace tyto spustitelné soubory stejně jako další nativní spustitelné soubory, jako například:

* Můžete dvakrát kliknout na spustitelný soubor.
* Aplikace z příkazového řádku můžete spustit přímo, jako například `myapp.exe` na Windows, a `./myapp` v Linuxu a macOS.

> [!NOTE]
> Určení konkrétního modulu runtime s `dotnet publish -r` nebo `dotnet build -r` argumenty pro jiná prostředí modulu runtime není podporován.

## <a name="build-copies-dependencies"></a>Vytvoření kopie závislosti

`dotnet build` Nyní zkopíruje závislostí NuGet pro vaši aplikaci z mezipaměti NuGet k výstupní složce sestavení. Dříve byly závislosti pouze zkopírovány jako součást `dotnet publish`. 

Existují některé operace, jako je stránka propojení a razor publikování, který se stále vyžadují publikování.


## <a name="local-dotnet-tools"></a>Nástroje pro místní dotnet

I když .NET Core 2.1 podporuje globální nástroje, .NET Core 3.0 teď má místní nástroje. Místní nástroje se podobají globální nástroje, ale jsou spojeny s konkrétní umístění na disku. Díky tomu jednotlivých projektů a nástrojů na úložiště. Libovolný nástroj nainstalovaný místně není k dispozici globálně.

Místní nástroje spoléhají na název souboru manifestu `dotnet-tools.json` v aktuálním adresáři. Tento soubor manifestu definuje nástroje k dispozici. Vytvořením tento soubor manifestu v kořenovém adresáři vašeho úložiště, zajistíte všem uživatelům klonování kódu obnovit a použít nástroje, které jsou potřeba k úspěšné práci s kódem.

Pokud je k dispozici soubor manifestu místní nástroje, použijte následující příkaz automaticky stáhnout a nainstalovat místně tyto nástroje:

```console
dotnet tool restore
```

Místní nástroj spusťte pomocí následujícího příkazu:

```console
dotnet tool run <tool-command-name>
```

Při volání místní nástroj vyhledá dotnet manifestu do struktury adresářů. Když je nalezen soubor manifestu nástroj, se hledá požadovaný nástroj. Pokud se nástroj nachází, obsahuje informace potřebné k vyhledání nástroje v umístění globálních balíčků NuGet. 

Pokud nástroj je nalezena v manifestu, ale ne do mezipaměti, zobrazí se uživateli chybu. Zpráva se vylepší po 1 ve verzi Preview požádat o uživateli spustit `dotnet tool restore`.

Přidat místní nástroje do adresáře, musíte nejprve vytvořit soubor manifestu nástroje. Po 1 ve verzi Preview nabízíme mechanismus pro nástroj pro vytváření souborů manifestu, jako je například dotnet novou šablonu. Pro verzi Preview 1, musíte vytvořit soubor s názvem `dotnet-tools.json` s následujícím obsahem:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Po vytvoření manifestu můžete přidat místní nástroje pomocí:

```console
dotnet tool install <toolPackageId>
```

Tento příkaz nainstaluje nejnovější verzi nástroje, pokud není zadána jiná verze.  I v případě, že jste vybrali na nejnovější verzi automaticky verzi nástroje jsou zapsána do souboru manifestu nástroj umožňující správnou verzi nástroje pro obnovení nebo spustit.

Soubor manifestu nástroje je navržena k umožnění ruční úpravě – které můžete využít k aktualizaci požadovaná verze pro práci s úložištěm.

Tady je příklad `dotnet-tools.json` souboru:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

K odebrání nástroje ze souboru manifestu nástroje, spusťte následující příkaz:

```console
dotnet tool uninstall <toolPackageId>
```

Pro globální a místní nástroje se vyžaduje kompatibilní verze modulu runtime. Mnoho nástrojů aktuálně na NuGet.org cílit na .NET Core Runtime 2.1. Instalovat ty, globálně nebo místně, je stále třeba k instalaci [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Další informace najdete v tématu [místní nástroje dřívější verze Preview dokumentace](https://github.com/dotnet/cli/issues/10288).

## <a name="windows-desktop"></a>Plocha Windows

Od verze rozhraní .NET Core 3.0 ve verzi Preview 1, můžete vytvářet aplikace klasické pracovní plochy Windows pomocí technologií WPF a Windows Forms. Tyto architektury podporují také pomocí moderních ovládací prvky a Fluent stylů v knihovně Windows uživatelského rozhraní XAML (WinUI) prostřednictvím [XAML ostrovy](/windows/uwp/xaml-platform/xaml-host-controls).

Komponenta Windows Desktop je součástí Windows .NET Core 3.0 SDK.

Můžete vytvořit novou aplikaci WPF nebo Windows Forms s následujícími `dotnet` příkazy:

```console
dotnet new wpf
dotnet new winforms
```

Můžete také otevřít, spuštění a ladění projektů .NET Core 3.0 WPF a Windows Forms v sadě Visual Studio. 2019 ve verzi Preview 1. Je aktuálně možné otevřít ve Visual Studio 2017 15.9, ale není podporovaný scénář (a je potřeba [povolit náhledy](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).

Nové projekty jsou stejné jako existující projekty .NET Core, s několika doplňky. Tady je porovnání základní projekt konzoly .NET Core a základního projektu Windows Forms a WPF.

V projektu aplikace konzoly .NET Core, že projekt používá `Microsoft.NET.Sdk` sady SDK a deklaruje závislost na rozhraní .NET Core 3.0 prostřednictvím `netcoreapp3.0` cílovou architekturu. K vytvoření aplikace pro Windows Desktop, použijte `Microsoft.NET.Sdk.WindowsDesktop` sady SDK a zvolte který uživatelského rozhraní framework použít:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Chcete-li tlačítko Windows Forms přes WPF, nastavte `UseWindowsForms` místo `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Obě `UseWPF` a `UseWindowsForms` může být nastaven na `true` Pokud aplikace používá obě architektury, například když dialogové okno Windows Forms je hostování ovládacího prvku WPF.

Podělte se prosím o svůj názor na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) a [dotnet/jádro](https://github.com/dotnet/core/issues) úložišť.

## <a name="fast-built-in-json-support"></a>Rychlé integrovanou podporou JSON

`System.Text.Json.Utf8JsonReader` je vysoce výkonné, s nízkou přidělení, dopředné čtecí modul pro kódování UTF-8 kódovaný JSON čtení z textu `ReadOnlySpan<byte>`. `Utf8JsonReader` Je nízké úrovně, základní typ, který můžete využít k vytváření vlastních analyzátorů a deserializers. Přečtení datovou část JSON pomocí nového `Utf8JsonReader` je 2 × rychleji než při použití reader od [Json.NET](https://www.newtonsoft.com/json). Nástroj nepřidělí dokud budete muset actualize tokeny JSON jako řetězce (UTF-16).

Toto nové rozhraní API bude zahrnovat následující součásti:

* Ve verzi Preview 1: Čtečka JSON (sekvenční přístup)
* Chystá: Zápis JSON, modelu DOM (RAM) objektů poco serializátor, objektů poco deserializátor

Tady je smyčka čtečku pro `Utf8JsonReader` , který může sloužit jako výchozí bod:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

Má spoléhat ekosystému .NET [Json.NET](https://www.newtonsoft.com/json) a dalších oblíbených knihoven JSON, které dál vhodná rozhodnutí. JSON.NET používá .NET řetězce jako jeho základní datový typ, které jsou pod pokličkou UTF-16. 

V rozhraní .NET Core 2.1 a 3.0, jsme přidali nová rozhraní API, která umožňuje zápis JSON API (například `Utf8JsonReader`), které vyžadují mnohem méně paměti, na základě `Span<T>` a řetězce UTF-8 a lepší sloužit potřebám vysoce propustné aplikace jako Kestrel ASP. .NET Core webový server.

## <a name="ranges-and-indices"></a>Rozsahy a indexy

Nové `Index` typ lze použít k indexování. Můžete je vytvořit z `int` , které se počítá od začátku, nebo s předponou `^` – operátor (C#), které se počítá od konce:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

K dispozici je také `Range` typ, který se skládá ze dvou `Index` hodnoty, jeden pro spuštění a jeden pro ukončení a může být zapsaný s `x..y` výrazu v rozsahu (C#). Potom můžete index s využitím `Range` aby vytvářela řez:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> Pouze [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) podporuje syntaxi pro `Range` a `Index`.

## <a name="async-streams"></a>Asynchronní datové proudy

`IAsyncEnumerable<T>` Typ je nový asynchronní verze `IEnumerable<T>`. Jazyk umožňuje `await foreach` přes tyto využívat jejich prvky a `yield return` k nim pro produkci prvků.

Následující příklad ukazuje produkční scénáře i využití asynchronních streamů. `foreach` Příkaz je asynchronní a sama používá `yield return` vytvoří na asynchronní datový proud pro volající. Tento model (pomocí `yield return`) je doporučený model pro vytváření asynchronních streamů.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> .NET core 3.0 ve verzi Preview 1 nyní obsahuje chybu s `await foreach`. Místo toho použijte `GetEnumerator` a `MoveNext` prvkům procesu. Další informace najdete v tématu [roslyn / #31268](https://github.com/dotnet/roslyn/issues/31268).

Kromě toho, že možnost `await foreach`, můžete také vytvořit asynchronní iterátory, například iterátoru, který vrátí `IAsyncEnumerable/IAsyncEnumerator` , můžete obě `await` a `yield` v. Pro objekty, které je potřeba se dá uvolnit, můžete použít `IAsyncDisposable`, které různé typy BCL implementovat jako `Stream` a `Timer`.

> [!NOTE]
> Pouze [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) podporuje `await foreach` syntaxe.

## <a name="type-sequencereader"></a>Zadejte: SequenceReader

V rozhraní .NET Core 3.0 `System.Buffers.SequenceReader` se přidala, který může sloužit jako čtečku `ReadOnlySequence<T>`. To umožňuje snadné, vysoký výkon s nízkou přidělení parsování `System.IO.Pipelines` data, která lze napříč více vyrovnávacích pamětí zálohování. 

Následující příklad přeruší vstup `Sequence` do platné `CR/LF` oddělených řádky:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Zadejte: MetadataLoadContext

`MetadataLoadContext` Byl přidán typ, který umožňuje čtení sestavení metadat, aniž by to ovlivnilo doméně aplikace volajícího. Sestavení se číst jako data, včetně sestavení vytvořená pro rozdílné architektury a platformy než aktuální běhové prostředí. `MetadataLoadContext` se překrývá s <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, který je k dispozici pouze v rozhraní .NET Framework.

`MetdataLoadContext` je k dispozici v [System.Reflection.MetadataLoadContext balíčku](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). Jedná se o balíček rozhraní .NET Standard 2.0.

`MetadataLoadContext` Zveřejňuje rozhraní API, podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale není na základě tohoto typu. Podobně jako <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` povolí načítání sestavení v rámci izolovaného sestavení načítání universe. `MetdataLoadContext` Rozhraní API vrací <xref:System.Reflection.Assembly> objekty povoluje použití známých reflexe rozhraní API. Spuštění orientované rozhraní API, jako například [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nejsou povoleny a vyvolá výjimku InvalidOperationException.

Následující příklad ukazuje, jak najít konkrétní typy v sestavení, který implementuje v příslušném rozhraní:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Scénáře pro `MetadataLoadContext` obsahují funkce návrhu, nástrojů, čas sestavení a funkce modulu runtime vytáčené světla, které je potřeba zkontrolovat sadu sestavení jako data a mít všech zámků souboru a probíhá po kontrole uvolněná paměť.

`MetadataLoadContext` Má třídu překladač předaný konstruktoru. Úlohy překladače je načtení `Assembly` zadaný jeho `AssemblyName`. Překladač třída je odvozena z abstraktní `MetadataAssemblyResolver` třídy. Je součástí implementace překladače pro scénáře na základě cest `PathAssemblyResolver`.

[MetadataLoadContext testy](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) ukazují, případy použití, mnoho. [Sestavení testů](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) jsou dobrým začátkem.

## <a name="tls-13--openssl-111-on-linux"></a>TLS verze 1.3 & OpenSSL 1.1.1 v Linuxu

.NET core se nově využít výhod [podpora protokolu TLS 1.3 v OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), až bude k dispozici v daném prostředí. Existuje více výhod TLS 1,3 za [OpenSSL týmu](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Čas vylepšené připojení z důvodu snížení počet zpátečních cest vyžaduje mezi klientem a serverem.

* Vyšší úroveň zabezpečení z důvodu odstranění různých zastaralé a nezabezpečené kryptografické algoritmy a šifrování větší metoda handshake připojení.

.NET core 3.0 ve verzi Preview 1 je schopen využitím **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, nebo **OpenSSL 1.0.2** (cokoli, co nejlepší nalezená verze se v systému Linux).  Při **OpenSSL 1.1.1** je k dispozici bude používat typy SslStream a HttpClient **TLS 1.3** při použití `SslProtocols.None` (protokoly systému výchozí), za předpokladu, že klient i server podpory **TLS 1.3**.

Následující příklad ukazuje .NET Core 3.0 ve verzi Preview 1 na Ubuntu 18.10 propojíte <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows a macOS zatím ještě nepodporují **TLS 1.3**. Bude podporovat .NET core 3.0 **TLS 1.3** v těchto operačních systémech, jakmile je k dispozici podpora.

## <a name="cryptography"></a>Kryptografie

Byla přidána podpora pro **AES-GCM** a **AES-CCM** šifry, prostřednictvím rozhraní `System.Security.Cryptography.AesGcm` a `System.Security.Cryptography.AesCcm`. Tyto algoritmy jsou obě [ověření šifrování pomocí algoritmů přidružení dat (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)a první ověření šifrování (AE) algoritmy přidané do .NET Core.

Následující kód ukazuje použití **AesGcm** šifer k šifrování a dešifrování náhodná data.

Kód pro **AesCcm** by vypadalo téměř identické (pouze názvy tříd, které proměnné by lišit).

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Kryptografické klíče Import/Export

.NET core 3.0 ve verzi Preview 1 podporuje import a export asymetrického veřejné a soukromé klíče ze standardní formáty, aniž by bylo nutné použít certifikát X.509.

Všechny klíče podpora typy (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** formát pro veřejné klíče a **PKCS #8 PrivateKeyInfo** a **PKCS #8 EncryptedPrivateKeyInfo**  formáty pro privátní klíče. Kromě toho podporuje RSA **PKCS #1 RSAPublicKey** a **PKCS #1 RSAPrivateKey**. Všechny metody export vytvářejí kódování DER binární data, a metod importu očekávají, že stejné. Pokud je klíč uložený ve formátu PEM popisný text, volajícího bude nutné base64 – dekódování obsahu před voláním metody importu.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

Soubory PKCS č. 8 můžete prozkoumat pomocí `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` třídy.

Soubory PFX/PKCS #12, můžete ho zkontrolovat a manipulovat s `System.Security.Cryptography.Pkcs.Pkcs12Info` a `System.Security.Cryptography.Pkcs.Pkcs12Builder`v uvedeném pořadí.

## <a name="serialport-for-linux"></a>SerialPort pro Linux

.NET core 3.0 nyní podporuje <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> v Linuxu.

Dříve, .NET Core, které jsou podporovány pouze při použití `SerialPort` typu na Windows.

## <a name="more-bcl-improvements"></a>Další vylepšení BCL

`Span<T>`, `Memory<T>`, A souvisejících typů, které byly zavedeny v .NET Core 2.1, byly optimalizovány odstraněním v .NET Core 3.0. Běžné operace, jako span konstrukce, dělení, analýzy a formátování nyní líp fungovat. 

Kromě toho, jako jsou typy `String` viděli v rámci titulní vylepšení je zefektivňují při použití jako klíče s `Dictionary<TKey, TValue>` i další kolekce. Abyste využili výhod těchto vylepšení nevyžaduje žádné změny kódu.

Tato vylepšení jsou také nové v rozhraní .NET Core 3 Preview 1:

* Podpora Brotli součástí HttpClient
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Komplexní aritmetické operátory
* Zachování soketu rozhraní API pro protokol TCP
* StringBuilder.GetChunks
* IPEndPoint analýza kódu
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Vrstvené kompilace

[Vrstvené kompilace](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) je ve výchozím s .NET Core 3.0. To je funkce, která umožňuje modulu runtime více Adaptivně pomocí kompilátor za běhu (JIT), můžete dosáhnout lepšího výkonu, jak při spuštění a maximalizuje propustnost.

Tato funkce byla přidána jako funkce opt-in v [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) a potom byla povolená ve výchozím nastavení v [.NET Core 2.2 ve verzi Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/). Následně ji byl vrácen zpět do optimalizované pomocí verze rozhraní .NET Core 2.2.

## <a name="arm64-linux-support"></a>Podpora Linuxu ARM64

Přidáváme podporu pro ARM64 pro tuto verzi systému Linux. Pro kontext přidali jsme podporu pro ARM32 pro Linux s .NET Core 2.1 a Windows s nástroji .NET Core 2.2. Případem primárního použití pro ARM64 je aktuálně s scénáře IoT.

Nástroj Alpine, Debian a Ubuntu [imagí Dockeru, které jsou dostupné pro .NET Core pro ARM64](https://hub.docker.com/r/microsoft/dotnet/).

Zkontrolujte prosím [.NET Core ARM64 stav](https://github.com/dotnet/announcements/issues/82) Další informace.

>[!NOTE]
> **ARM64** podporu Windows ještě není k dispozici.
