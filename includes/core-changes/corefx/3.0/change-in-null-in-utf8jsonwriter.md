---
ms.openlocfilehash: c9547cdc2f127cf13a3610118a26736930fcd8bd
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021577"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="c98bc-101">Změna sémantiky `(string)null` v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="c98bc-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="c98bc-102">V rozhraní .NET Core 3.0 Preview 7 je nulový <xref:System.Text.Json.Utf8JsonWriter>řetězec považován za prázdný řetězec v .</span><span class="sxs-lookup"><span data-stu-id="c98bc-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="c98bc-103">Počínaje .NET Core 3.0 Preview 8, nulový řetězec vyvolá výjimku při použití jako název vlastnosti a vydává token null JSON při použití jako hodnota.</span><span class="sxs-lookup"><span data-stu-id="c98bc-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c98bc-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="c98bc-104">Change description</span></span>

<span data-ttu-id="c98bc-105">V .NET Core 3.0 `null` Preview 7 byl `""` řetězec považován za při psaní názvů vlastností i při psaní hodnot.</span><span class="sxs-lookup"><span data-stu-id="c98bc-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="c98bc-106">Počínaje rozhraním .NET Core 3.0 Preview 8, `null` název vlastnosti vyvolá `ArgumentNullException`a <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType> `null` hodnota je považována za volání nebo .</span><span class="sxs-lookup"><span data-stu-id="c98bc-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c98bc-107">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="c98bc-107">Consider the following code:</span></span>

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

<span data-ttu-id="c98bc-108">Při spuštění s rozhraním .NET Core 3.0 Preview 7 vytvoří zapisovač následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c98bc-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="c98bc-109">Počínaje rozhraním .NET Core 3.0 `writer.WriteString(propertyName1, propertyValue1)` Preview 8 <xref:System.ArgumentNullException>vyvolá volání .</span><span class="sxs-lookup"><span data-stu-id="c98bc-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="c98bc-110">Pokud `propertyName1 = null` je nahrazen `propertyName1 = string.Empty`, výstup by nyní:</span><span class="sxs-lookup"><span data-stu-id="c98bc-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="c98bc-111">Tato změna byla provedena lépe sladit s očekávání volajícího pro `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c98bc-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c98bc-112">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="c98bc-112">Version introduced</span></span>

<span data-ttu-id="c98bc-113">3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="c98bc-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c98bc-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c98bc-114">Recommended action</span></span>

<span data-ttu-id="c98bc-115">Při psaní názvů vlastností <xref:System.Text.Json.Utf8JsonWriter> a hodnot s třídou:</span><span class="sxs-lookup"><span data-stu-id="c98bc-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="c98bc-116">Ujistěte`null` se, že jako názvy vlastností se používají jiné řetězce.</span><span class="sxs-lookup"><span data-stu-id="c98bc-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="c98bc-117">Pokud je požadováno předchozí chování, použijte null coalescing vyvolání; například `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="c98bc-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="c98bc-118">Pokud zápis `null` literálu `null` pro hodnotu řetězce není žádoucí, použijte null coalescing vyvolání; například `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span><span class="sxs-lookup"><span data-stu-id="c98bc-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="c98bc-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c98bc-119">Category</span></span>

<span data-ttu-id="c98bc-120">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="c98bc-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c98bc-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c98bc-121">Affected APIs</span></span>

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->
