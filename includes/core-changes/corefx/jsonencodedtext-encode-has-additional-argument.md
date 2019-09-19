---
ms.openlocfilehash: 101740e828589d7d210527e3db82a1c949a6e0fd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117139"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="12558-101">Metody JsonEncodedText. Encode mají další argument JavaScriptEncoder.</span><span class="sxs-lookup"><span data-stu-id="12558-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="12558-102">Počínaje rozhraním .NET Core 3,0 Preview 8 tyto <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> metody obsahují volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span><span class="sxs-lookup"><span data-stu-id="12558-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span> 

#### <a name="details"></a><span data-ttu-id="12558-103">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="12558-103">Details</span></span>

<span data-ttu-id="12558-104">.NET Core 3,0 obsahuje nový typ odkazy XREF: System. text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType >.</span><span class="sxs-lookup"><span data-stu-id="12558-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="12558-105">Od verze .NET Core 3,0 Preview 8 se signatura všech <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> přetížení metod změnila tak, aby zahrnovala volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> parametr.</span><span class="sxs-lookup"><span data-stu-id="12558-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="12558-106">Tato změna byla provedena za účelem povolení pro jiný nebo vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="12558-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="12558-107">Signatura `Encode` metod v .NET Core 3,0 Preview 7 je:</span><span class="sxs-lookup"><span data-stu-id="12558-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="12558-108">Signatura stejných `Encode` metod v .NET Core 3,0 Preview 8 a novějších verzích je:</span><span class="sxs-lookup"><span data-stu-id="12558-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="12558-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="12558-109">Version introduced</span></span>

<span data-ttu-id="12558-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="12558-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12558-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="12558-111">Recommended action</span></span>

<span data-ttu-id="12558-112">Jedná se o binární zásadní změnu. Opětovná kompilace proti .NET Core 3,0 Preview 8 nebo novější verzi vyřeší jakékoli problémy s modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="12558-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="12558-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="12558-113">Category</span></span>

<span data-ttu-id="12558-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="12558-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12558-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="12558-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs 

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->