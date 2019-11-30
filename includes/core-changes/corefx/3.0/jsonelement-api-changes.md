---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568199"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="2ba70-101">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="2ba70-101">JsonElement API changes</span></span>

<span data-ttu-id="2ba70-102">Od verze .NET Core 3,0 Preview 7 se některá rozhraní <xref:System.Text.Json.JsonElement> API změnila tak, aby umožňovala snazší zjišťování a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="2ba70-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2ba70-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="2ba70-103">Change description</span></span>

<span data-ttu-id="2ba70-104">V rozhraní .NET Core 3,0 Preview 7 se <xref:System.Text.Json.JsonElement> rozhraní API změnila takto, aby bylo umožněno snazší zjišťování a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="2ba70-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="2ba70-105">Všechna přetížení metody `WriteProperty` byla z <xref:System.Text.Json.JsonElement>odebrána.</span><span class="sxs-lookup"><span data-stu-id="2ba70-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="2ba70-106">To má vliv na následující kód:</span><span class="sxs-lookup"><span data-stu-id="2ba70-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="2ba70-107">`WriteValue` byla přejmenována jako <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ba70-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="2ba70-108">To má vliv na následující kód:</span><span class="sxs-lookup"><span data-stu-id="2ba70-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="2ba70-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> nyní vyvolá <xref:System.ArgumentNullException>, když je jeho parametr metody `null`.</span><span class="sxs-lookup"><span data-stu-id="2ba70-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ba70-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2ba70-110">Version introduced</span></span>

<span data-ttu-id="2ba70-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="2ba70-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ba70-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2ba70-112">Recommended action</span></span>

<span data-ttu-id="2ba70-113">Pokud je váš kód ovlivněn těmito změnami, můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="2ba70-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="2ba70-114">Neexistuje žádné náhradní rozhraní API pro `WriteProperty` přetížení v <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="2ba70-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="2ba70-115">Místo toho můžete zavolat jedno z <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> přetížení společně s metodou <xref:System.Text.Json.JsonElement.WriteTo%2A>, abyste dosáhli stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="2ba70-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="2ba70-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2ba70-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="2ba70-117">Přejmenujte metodu `WriteValue` na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span><span class="sxs-lookup"><span data-stu-id="2ba70-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="2ba70-118">Parametr metody zůstává beze změny.</span><span class="sxs-lookup"><span data-stu-id="2ba70-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="2ba70-119">Například předchozí kód by měl být změněn na následující:</span><span class="sxs-lookup"><span data-stu-id="2ba70-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="2ba70-120">Zpracování <xref:System.ArgumentNullException> v volání metody <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ba70-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ba70-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2ba70-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
