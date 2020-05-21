---
ms.openlocfilehash: 13da0ef6155d65fbc894c5747cc36bb3483ba518
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721587"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="1d385-101">Změna v sémantikě `(string)null` v Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="1d385-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="1d385-102">V rozhraní .NET Core 3,0 Preview 7 je řetězec s hodnotou null považován za prázdný řetězec v <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="1d385-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="1d385-103">Počínaje rozhraním .NET Core 3,0 Preview 8 vygeneruje řetězec null výjimku při použití jako názvu vlastnosti a vygeneruje token JSON s hodnotou null, pokud se používá jako hodnota.</span><span class="sxs-lookup"><span data-stu-id="1d385-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1d385-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="1d385-104">Change description</span></span>

<span data-ttu-id="1d385-105">V rozhraní .NET Core 3,0 Preview 7 `null` byl řetězec `""` při psaní názvů vlastností a při psaní hodnot považován za obojí.</span><span class="sxs-lookup"><span data-stu-id="1d385-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="1d385-106">Počínaje rozhraním .NET Core 3,0 Preview 8 je `null` název vlastnosti vyvolána `ArgumentNullException` a `null` hodnota je považována za volání <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> nebo <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1d385-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1d385-107">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="1d385-107">Consider the following code:</span></span>

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

<span data-ttu-id="1d385-108">Pokud spustíte s .NET Core 3,0 Preview 7, modul pro zápis vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1d385-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="1d385-109">Počínaje rozhraním .NET Core 3,0 Preview 8 volání `writer.WriteString(propertyName1, propertyValue1)` vyvolá výjimku <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="1d385-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="1d385-110">Pokud `propertyName1 = null` je nahrazeno `propertyName1 = string.Empty` , výstup by nyní byl:</span><span class="sxs-lookup"><span data-stu-id="1d385-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="1d385-111">Tato změna byla provedena pro lepší zarovnání se očekáváním volajícího pro `null` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1d385-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1d385-112">Představená verze</span><span class="sxs-lookup"><span data-stu-id="1d385-112">Version introduced</span></span>

<span data-ttu-id="1d385-113">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="1d385-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1d385-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1d385-114">Recommended action</span></span>

<span data-ttu-id="1d385-115">Při psaní názvů vlastností a hodnot pomocí <xref:System.Text.Json.Utf8JsonWriter> třídy:</span><span class="sxs-lookup"><span data-stu-id="1d385-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="1d385-116">Zajistěte `null` , aby jako názvy vlastností byly použity jiné než řetězce.</span><span class="sxs-lookup"><span data-stu-id="1d385-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="1d385-117">Pokud je požadované předchozí chování, použijte volání slučování s hodnotou null; například `writer.WriteString(propertyName1 ?? "", propertyValue1)` .</span><span class="sxs-lookup"><span data-stu-id="1d385-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="1d385-118">Pokud zápis `null` literálu pro `null` řetězcovou hodnotu není žádoucí, použijte volání slučování s hodnotou null, například `writer.WriteString(propertyName2, propertyValue2 ?? "")` .</span><span class="sxs-lookup"><span data-stu-id="1d385-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="1d385-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1d385-119">Category</span></span>

<span data-ttu-id="1d385-120">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="1d385-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1d385-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1d385-121">Affected APIs</span></span>

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

#### Affected APIs

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
