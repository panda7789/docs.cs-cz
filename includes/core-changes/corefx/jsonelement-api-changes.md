---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119301"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="1621b-101">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="1621b-101">JsonElement API changes</span></span>

<span data-ttu-id="1621b-102">Od verze .NET Core 3,0 Preview 7 se některá <xref:System.Text.Json.JsonElement> rozhraní API změnila tak, aby umožňovala snazší zjišťování a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="1621b-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1621b-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="1621b-103">Change description</span></span>

<span data-ttu-id="1621b-104">V rozhraní .NET Core 3,0 Preview 7 <xref:System.Text.Json.JsonElement> se rozhraní API změnila následujícím způsobem, aby bylo možné snazší zjišťování a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="1621b-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="1621b-105">Všechna `WriteProperty` přetížení metody se odebrala z <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="1621b-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="1621b-106">To má vliv na následující kód:</span><span class="sxs-lookup"><span data-stu-id="1621b-106">This affects code such as the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. <span data-ttu-id="1621b-107">`WriteValue`byla přejmenována jako <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="1621b-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="1621b-108">To má vliv na následující kód:</span><span class="sxs-lookup"><span data-stu-id="1621b-108">This affects code such as the following:</span></span>

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <span data-ttu-id="1621b-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>nyní vyvolá <xref:System.ArgumentNullException> výjimku, když je `null`jeho parametr metody.</span><span class="sxs-lookup"><span data-stu-id="1621b-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1621b-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="1621b-110">Version introduced</span></span>

<span data-ttu-id="1621b-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="1621b-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1621b-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1621b-112">Recommended action</span></span>

<span data-ttu-id="1621b-113">Pokud je váš kód ovlivněn těmito změnami, můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="1621b-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="1621b-114">Pro `WriteProperty` přetížení<xref:System.Text.Json.JsonElement>není k dispozici žádné náhradní rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1621b-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="1621b-115">Místo toho můžete zavolat jedno z <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> přetížení spolu <xref:System.Text.Json.JsonElement.WriteTo%2A> s metodou pro zajištění stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="1621b-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="1621b-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1621b-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="1621b-117">Přejmenujte <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>metoduna `WriteValue` .</span><span class="sxs-lookup"><span data-stu-id="1621b-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="1621b-118">Parametr metody zůstává beze změny.</span><span class="sxs-lookup"><span data-stu-id="1621b-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="1621b-119">Například předchozí kód by měl být změněn na následující:</span><span class="sxs-lookup"><span data-stu-id="1621b-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="1621b-120">Zpracujte v volání <xref:System.Text.Json.JsonElement.WriteTo%2A>metody. <xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="1621b-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1621b-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1621b-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
