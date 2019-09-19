---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119301"
---
### <a name="jsonelement-api-changes"></a>Změny rozhraní API JsonElement

Od verze .NET Core 3,0 Preview 7 se některá <xref:System.Text.Json.JsonElement> rozhraní API změnila tak, aby umožňovala snazší zjišťování a větší použitelnost.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 3,0 Preview 7 <xref:System.Text.Json.JsonElement> se rozhraní API změnila následujícím způsobem, aby bylo možné snazší zjišťování a větší použitelnost.

1. Všechna `WriteProperty` přetížení metody se odebrala z <xref:System.Text.Json.JsonElement>. To má vliv na následující kód:

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

1. `WriteValue`byla přejmenována jako <xref:System.Text.Json.JsonElement.WriteTo%2A>. To má vliv na následující kód:

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>nyní vyvolá <xref:System.ArgumentNullException> výjimku, když je `null`jeho parametr metody.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 7

#### <a name="recommended-action"></a>Doporučená akce

Pokud je váš kód ovlivněn těmito změnami, můžete provést následující:

- Pro `WriteProperty` přetížení<xref:System.Text.Json.JsonElement>není k dispozici žádné náhradní rozhraní API. Místo toho můžete zavolat jedno z <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> přetížení spolu <xref:System.Text.Json.JsonElement.WriteTo%2A> s metodou pro zajištění stejného výsledku. Příklad:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Přejmenujte <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>metoduna `WriteValue` . Parametr metody zůstává beze změny. Například předchozí kód by měl být změněn na následující:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Zpracujte v volání <xref:System.Text.Json.JsonElement.WriteTo%2A>metody. <xref:System.ArgumentNullException>

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
