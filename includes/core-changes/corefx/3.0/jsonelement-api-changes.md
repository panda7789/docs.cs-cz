---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568199"
---
### <a name="jsonelement-api-changes"></a>Změny rozhraní API JsonElement

Od verze .NET Core 3,0 Preview 7 se některá rozhraní <xref:System.Text.Json.JsonElement> API změnila tak, aby umožňovala snazší zjišťování a větší použitelnost.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 3,0 Preview 7 se <xref:System.Text.Json.JsonElement> rozhraní API změnila takto, aby bylo umožněno snazší zjišťování a větší použitelnost.

1. Všechna přetížení metody `WriteProperty` byla z <xref:System.Text.Json.JsonElement>odebrána. To má vliv na následující kód:

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

1. `WriteValue` byla přejmenována jako <xref:System.Text.Json.JsonElement.WriteTo%2A>. To má vliv na následující kód:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> nyní vyvolá <xref:System.ArgumentNullException>, když je jeho parametr metody `null`.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 7

#### <a name="recommended-action"></a>Doporučená akce

Pokud je váš kód ovlivněn těmito změnami, můžete provést následující:

- Neexistuje žádné náhradní rozhraní API pro `WriteProperty` přetížení v <xref:System.Text.Json.JsonElement>. Místo toho můžete zavolat jedno z <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> přetížení společně s metodou <xref:System.Text.Json.JsonElement.WriteTo%2A>, abyste dosáhli stejného výsledku. Příklad:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Přejmenujte metodu `WriteValue` na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>. Parametr metody zůstává beze změny. Například předchozí kód by měl být změněn na následující:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Zpracování <xref:System.ArgumentNullException> v volání metody <xref:System.Text.Json.JsonElement.WriteTo%2A>.

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
