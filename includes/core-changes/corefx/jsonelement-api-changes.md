---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237332"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="271ca-101">Změny rozhraní API JsonElement</span><span class="sxs-lookup"><span data-stu-id="271ca-101">JsonElement API changes</span></span>

<span data-ttu-id="271ca-102">Od verze .NET Core 3,0 Preview 7 se některá rozhraní API <xref:System.Text.Json.JsonElement> změnila tak, aby umožňovala snazší zjišťování a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="271ca-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="271ca-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="271ca-103">Change description</span></span>

<span data-ttu-id="271ca-104">V rozhraní .NET Core 3,0 Preview 7 se rozhraní API <xref:System.Text.Json.JsonElement> změnila následujícím způsobem, aby bylo umožněno snazší zjišťování a větší použitelnost.</span><span class="sxs-lookup"><span data-stu-id="271ca-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="271ca-105">Všechna přetížení metod `WriteProperty` byla z <xref:System.Text.Json.JsonElement> odstraněna.</span><span class="sxs-lookup"><span data-stu-id="271ca-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="271ca-106">To má vliv na následující kód:</span><span class="sxs-lookup"><span data-stu-id="271ca-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="271ca-107">`WriteValue` bylo přejmenováno na <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="271ca-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="271ca-108">To má vliv na následující kód:</span><span class="sxs-lookup"><span data-stu-id="271ca-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="271ca-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> nyní vyvolá <xref:System.ArgumentNullException>, pokud je jeho parametr metody `null`.</span><span class="sxs-lookup"><span data-stu-id="271ca-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="271ca-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="271ca-110">Version introduced</span></span>

<span data-ttu-id="271ca-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="271ca-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="271ca-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="271ca-112">Recommended action</span></span>

<span data-ttu-id="271ca-113">Pokud je váš kód ovlivněn těmito změnami, můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="271ca-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="271ca-114">Neexistuje žádné náhradní rozhraní API pro přetížení `WriteProperty` v <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="271ca-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="271ca-115">Místo toho můžete zavolat jedno z přetížení <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> spolu s metodou <xref:System.Text.Json.JsonElement.WriteTo%2A>, aby se zajištění stejný výsledek.</span><span class="sxs-lookup"><span data-stu-id="271ca-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="271ca-116">Například:</span><span class="sxs-lookup"><span data-stu-id="271ca-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="271ca-117">Přejmenujte metodu `WriteValue` na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span><span class="sxs-lookup"><span data-stu-id="271ca-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="271ca-118">Parametr metody zůstává beze změny.</span><span class="sxs-lookup"><span data-stu-id="271ca-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="271ca-119">Například předchozí kód by měl být změněn na následující:</span><span class="sxs-lookup"><span data-stu-id="271ca-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="271ca-120">Zpracovává <xref:System.ArgumentNullException> v volání metody <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="271ca-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="271ca-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="271ca-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
