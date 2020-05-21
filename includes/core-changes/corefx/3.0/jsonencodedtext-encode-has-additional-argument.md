---
ms.openlocfilehash: d90996ae1b87cdea815daf979bece094d8602f70
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721445"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="f1c4d-101">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="f1c4d-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="f1c4d-102">Počínaje rozhraním .NET Core 3,0 Preview 8 tyto <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> metody obsahují volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span><span class="sxs-lookup"><span data-stu-id="f1c4d-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f1c4d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="f1c4d-103">Change description</span></span>

<span data-ttu-id="f1c4d-104">.NET Core 3,0 obsahuje nový typ odkazy XREF: System. text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1c4d-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f1c4d-105">Od verze .NET Core 3,0 Preview 8 se signatura všech <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> přetížení metod změnila tak, aby zahrnovala volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> parametr.</span><span class="sxs-lookup"><span data-stu-id="f1c4d-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="f1c4d-106">Tato změna byla provedena za účelem povolení pro jiný nebo vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="f1c4d-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="f1c4d-107">Signatura `Encode` metod v .NET Core 3,0 Preview 7 je:</span><span class="sxs-lookup"><span data-stu-id="f1c4d-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="f1c4d-108">Signatura stejných `Encode` metod v .NET Core 3,0 Preview 8 a novějších verzích je:</span><span class="sxs-lookup"><span data-stu-id="f1c4d-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="f1c4d-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f1c4d-109">Version introduced</span></span>

<span data-ttu-id="f1c4d-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f1c4d-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f1c4d-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f1c4d-111">Recommended action</span></span>

<span data-ttu-id="f1c4d-112">Jedná se o binární zásadní změnu. Opětovná kompilace proti .NET Core 3,0 Preview 8 nebo novější verzi vyřeší jakékoli problémy s modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="f1c4d-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="f1c4d-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f1c4d-113">Category</span></span>

<span data-ttu-id="f1c4d-114">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="f1c4d-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f1c4d-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f1c4d-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
