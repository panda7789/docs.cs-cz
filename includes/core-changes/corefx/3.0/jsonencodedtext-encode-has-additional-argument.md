---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147585"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="df283-101">Metody JsonEncodedText.Encode mají další argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="df283-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="df283-102">Počínaje rozhraním .NET Core 3.0 Preview 8 obsahují <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> metody volitelný <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span><span class="sxs-lookup"><span data-stu-id="df283-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="df283-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="df283-103">Change description</span></span>

<span data-ttu-id="df283-104">.NET Core 3.0 obsahuje nový typ, externí reference:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df283-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="df283-105">Počínaje rozhraním .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8 se podpis všech <xref:System.Text.Encodings.Web.JavaScriptEncoder> přetížení metody změnil tak, aby zahrnoval volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="df283-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="df283-106">Tato změna byla provedena, aby bylo možné použít jiný nebo vlastní kodér.</span><span class="sxs-lookup"><span data-stu-id="df283-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="df283-107">Podpis `Encode` metod v rozhraní .NET Core 3.0 Preview 7 je:</span><span class="sxs-lookup"><span data-stu-id="df283-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="df283-108">Podpis stejných `Encode` metod v rozhraní .NET Core 3.0 Preview 8 a novějších verzích je:</span><span class="sxs-lookup"><span data-stu-id="df283-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="df283-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="df283-109">Version introduced</span></span>

<span data-ttu-id="df283-110">.NET Core 3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="df283-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="df283-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="df283-111">Recommended action</span></span>

<span data-ttu-id="df283-112">Toto je pouze binární změna. překompilovat proti .NET Core 3.0 Náhled 8 nebo novější verze opraví všechny problémy s časem runtime.</span><span class="sxs-lookup"><span data-stu-id="df283-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="df283-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="df283-113">Category</span></span>

<span data-ttu-id="df283-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="df283-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="df283-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="df283-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
