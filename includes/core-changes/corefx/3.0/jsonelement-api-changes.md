---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568199"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="c765d-101">Změny rozhraní API Prvku JsonElement</span><span class="sxs-lookup"><span data-stu-id="c765d-101">JsonElement API changes</span></span>

<span data-ttu-id="c765d-102">Počínaje rozhraním .NET Core 3.0 Preview 7 se některá <xref:System.Text.Json.JsonElement> rozhraní API změnila, aby bylo možné snadněji vykreslovat a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="c765d-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c765d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="c765d-103">Change description</span></span>

<span data-ttu-id="c765d-104">V rozhraní .NET Core 3.0 Preview 7 se rozhraní API změnila takto, <xref:System.Text.Json.JsonElement> aby bylo možné snadněji vykreslovat a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="c765d-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="c765d-105">Všechny `WriteProperty` přetížení metody byly <xref:System.Text.Json.JsonElement>odebrány z .</span><span class="sxs-lookup"><span data-stu-id="c765d-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="c765d-106">To má vliv na kód, jako je například následující:</span><span class="sxs-lookup"><span data-stu-id="c765d-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="c765d-107">`WriteValue`byl přejmenován <xref:System.Text.Json.JsonElement.WriteTo%2A>na .</span><span class="sxs-lookup"><span data-stu-id="c765d-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="c765d-108">To má vliv na kód, jako je například následující:</span><span class="sxs-lookup"><span data-stu-id="c765d-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="c765d-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>nyní vyvolá, <xref:System.ArgumentNullException> když je `null`parametr metody .</span><span class="sxs-lookup"><span data-stu-id="c765d-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c765d-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="c765d-110">Version introduced</span></span>

<span data-ttu-id="c765d-111">3.0 Náhled 7</span><span class="sxs-lookup"><span data-stu-id="c765d-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c765d-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c765d-112">Recommended action</span></span>

<span data-ttu-id="c765d-113">Pokud váš kód je ovlivněna těmito změnami, můžete provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="c765d-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="c765d-114">Neexistuje žádné náhradní rozhraní `WriteProperty` API <xref:System.Text.Json.JsonElement>pro přetížení v .</span><span class="sxs-lookup"><span data-stu-id="c765d-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="c765d-115">Místo toho můžete volat <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> jeden z přetížení <xref:System.Text.Json.JsonElement.WriteTo%2A> spolu s metodou k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="c765d-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="c765d-116">Například:</span><span class="sxs-lookup"><span data-stu-id="c765d-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="c765d-117">Přejmenujte `WriteValue` metodu na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span><span class="sxs-lookup"><span data-stu-id="c765d-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="c765d-118">Parametr metody zůstane nezměněn.</span><span class="sxs-lookup"><span data-stu-id="c765d-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="c765d-119">Například předchozí kód by měl být změněn na následující:</span><span class="sxs-lookup"><span data-stu-id="c765d-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="c765d-120">Zpracování <xref:System.ArgumentNullException> příchozí volání <xref:System.Text.Json.JsonElement.WriteTo%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c765d-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c765d-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c765d-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
