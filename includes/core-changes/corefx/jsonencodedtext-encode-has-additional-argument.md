---
ms.openlocfilehash: 101740e828589d7d210527e3db82a1c949a6e0fd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117139"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.

Počínaje rozhraním .NET Core 3,0 Preview 8 tyto <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> metody obsahují volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument. 

#### <a name="details"></a>Podrobnosti

.NET Core 3,0 obsahuje nový typ odkazy XREF: System. text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType >. Od verze .NET Core 3,0 Preview 8 se signatura všech <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> přetížení metod změnila tak, aby zahrnovala volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> parametr. Tato změna byla provedena za účelem povolení pro jiný nebo vlastní kodér.

Signatura `Encode` metod v .NET Core 3,0 Preview 7 je:

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

Signatura stejných `Encode` metod v .NET Core 3,0 Preview 8 a novějších verzích je:

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

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Jedná se o binární zásadní změnu. Opětovná kompilace proti .NET Core 3,0 Preview 8 nebo novější verzi vyřeší jakékoli problémy s modulem runtime.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs 

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->