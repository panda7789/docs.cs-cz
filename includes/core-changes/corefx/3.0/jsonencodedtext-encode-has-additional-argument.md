---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021633"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Metody JsonEncodedText.Encode mají další argument JavaScriptEncoder

Počínaje rozhraním .NET Core 3.0 Preview 8 obsahují <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> metody volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.

#### <a name="change-description"></a>Popis změny

.NET Core 3.0 obsahuje nový typ, externí reference:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>. Počínaje rozhraním .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8 se podpis všech <xref:System.Text.Encodings.Web.JavaScriptEncoder> přetížení metody změnil tak, aby zahrnoval volitelný parametr. Tato změna byla provedena, aby bylo možné použít jiný nebo vlastní kodér.

Podpis `Encode` metod v rozhraní .NET Core 3.0 Preview 7 je:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

Podpis stejných `Encode` metod v rozhraní .NET Core 3.0 Preview 8 a novějších verzích je:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a>Zavedená verze

.NET Core 3.0 Náhled 8

#### <a name="recommended-action"></a>Doporučená akce

Toto je pouze binární změna. překompilovat proti .NET Core 3.0 Náhled 8 nebo novější verze opraví všechny problémy s časem runtime.

#### <a name="category"></a>Kategorie

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
