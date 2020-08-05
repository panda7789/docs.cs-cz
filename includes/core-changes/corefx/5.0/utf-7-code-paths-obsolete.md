---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455769"
---
### <a name="utf-7-code-paths-are-obsolete"></a>Cesty kódu UTF-7 jsou zastaralé.

Kódování UTF-7 se už mezi aplikacemi nepoužívá a mnoho specifikací teď [zakazuje použití](https://security.stackexchange.com/a/68609/3573) při výměně. V aplikacích, které nepředpokládá nahlašování dat kódovaných v kódování UTF-7, se někdy [používá také jako vektor útoku](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) . Microsoft upozorňuje na použití, <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> protože neposkytuje detekci chyb.

V důsledku toho <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding.%23ctor%2A> jsou nyní zastaraly vlastnosti a konstruktory. Navíc <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> a <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> již neumožňuje zadat `UTF-7` .

#### <a name="change-description"></a>Popis změny

Dřív jste mohli vytvořit instanci kódování UTF-7 pomocí <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> rozhraní API. Zde je příklad:

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

Kromě toho instance, která představuje kódování UTF-7, byla vytvořena pomocí <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> metody, která vytvoří výčet všech <xref:System.Text.Encoding> instancí zaregistrovaných v systému.

Počínaje rozhraním .NET 5,0 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> jsou vlastnosti a <xref:System.Text.UTF7Encoding.%23ctor%2A> konstruktory zastaralé a jsou vyprodukovány upozornění `SYSLIB0001` (nebo `MSLIB0001` ve verzi Preview). Chcete-li však omezit počet upozornění, která volající obdrží při použití <xref:System.Text.UTF7Encoding> třídy, <xref:System.Text.UTF7Encoding> samotný typ není označen jako zastaralý.

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

Kromě toho <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> metody zacházejí s názvem kódování `utf-7` a znakovou stránkou `65000` jako `unknown` . Ošetření kódování jako `unknown` způsobí, že metoda vyvolá výjimku <xref:System.ArgumentException> .

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

Nakonec <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> Metoda nezahrnuje kódování UTF-7 v poli <xref:System.Text.EncodingInfo> , které vrací. Kódování je vyloučeno, protože nemůže být vytvořena instance.

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a>Důvod změny

Mnoho aplikací volá `Encoding.GetEncoding("encoding-name")` s hodnotou názvu kódování, která je poskytnuta nedůvěryhodným zdrojem. Například webový klient nebo server může převzít `charset` část `Content-Type` hlavičky a předat hodnotu přímo do `Encoding.GetEncoding` bez ověření. To by mohlo umožňovat zadat škodlivý koncový bod `Content-Type: ...; charset=utf-7` , což by mohlo způsobit nesprávné chování přijímající aplikace.

Kromě toho zakázání cest kódu ve formátu UTF-7 umožňuje optimalizace kompilátorů, jako jsou ty, které používá Blazor, k odebrání těchto cest kódu zcela ze výsledné aplikace. V důsledku toho zkompilované aplikace pracují efektivněji a zabírají méně místa na disku.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Ve většině případů není nutné provádět žádnou akci. Pro aplikace, které dříve aktivovaly cesty kódu související s kódováním UTF-7, je však vhodné postupovat podle pokynů.

- Pokud vaše aplikace volá <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> s neznámými názvy kódování poskytnutými nedůvěryhodným zdrojem:

  Místo toho Porovnejte názvy kódování s konfigurovatelným seznamem povolených. Seznam konfigurovatelných povolených možností by měl obsahovat minimální standardní kódování UTF-8. V závislosti na vašich klientech a zákonných požadavcích možná budete muset také zapnout kódování pro konkrétní oblast, například "GB18030".

  Pokud neimplementujete seznam povolených, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> vrátí všechny <xref:System.Text.Encoding> , které jsou součástí systému nebo které jsou zaregistrovány prostřednictvím vlastního <xref:System.Text.EncodingProvider> . Auditujte požadavky služby a ověřte, zda se jedná o požadované chování. Kódování UTF-7 bude ve výchozím nastavení nadále zakázáno, pokud vaše aplikace znovu nepovolí přepínač kompatibility, který je uveden dále v tomto článku.

- Pokud používáte <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> nebo <xref:System.Text.UTF7Encoding> máte ve svém vlastním protokolu nebo formátu souboru:

  Přepněte na použití <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> nebo <xref:System.Text.UTF8Encoding> . UTF-8 je oborová Standard a je široce podporovaná napříč jazyky, operačními systémy a moduly runtime. Použití UTF-8 usnadňuje budoucí údržbu kódu a usnadňuje spolupráci se zbytkem ekosystému.

- Pokud porovnáváte <xref:System.Text.Encoding> instanci proti <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :

  Místo toho zvažte možnost provést kontrolu na dobře známé znakové stránce UTF-7, což je `65000` . Porovnáním s znakovou stránkou se vyhnete varování a také zpracovává některé hraniční případy, například pokud někdo volal `new UTF7Encoding()` nebo podtřídí typ.

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- Pokud musíte použít <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> nebo <xref:System.Text.UTF7Encoding> :

  Můžete potlačit `SYSLIB0001` upozornění v kódu nebo v souboru *. csproj* projektu.

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > Potlačení `SYSLIB0001` zakáže jenom <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> Upozornění a <xref:System.Text.UTF7Encoding> obsoletion. Nevypne žádná další upozornění ani nemění chování rozhraní API, jako je <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .

- Pokud potřebujete podporu `Encoding.GetEncoding("utf-7", ...)` :

  Podporu této služby můžete znovu povolit prostřednictvím přepínače kompatibility. Tento přepínač kompatibility lze zadat v souboru *. csproj* aplikace nebo v [konfiguračním souboru run-time](../../../../docs/core/run-time-config/index.md), jak je znázorněno v následujících příkladech.

  V souboru *. csproj* aplikace:

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  V *runtimeconfig.template.jsaplikace v* souboru:

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > Pokud znovu povolíte podporu UTF-7, měli byste provést kontrolu zabezpečení kódu, který volá <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategorie

- Knihovny Core .NET
- Zabezpečení

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
