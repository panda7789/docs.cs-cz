---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568199"
---
### <a name="jsonelement-api-changes"></a>Změny rozhraní API Prvku JsonElement

Počínaje rozhraním .NET Core 3.0 Preview 7 se některá <xref:System.Text.Json.JsonElement> rozhraní API změnila, aby bylo možné snadněji vykreslovat a větší použitelnost.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 3.0 Preview 7 se rozhraní API změnila takto, <xref:System.Text.Json.JsonElement> aby bylo možné snadněji vykreslovat a větší použitelnost.

1. Všechny `WriteProperty` přetížení metody byly <xref:System.Text.Json.JsonElement>odebrány z . To má vliv na kód, jako je například následující:

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

1. `WriteValue`byl přejmenován <xref:System.Text.Json.JsonElement.WriteTo%2A>na . To má vliv na kód, jako je například následující:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>nyní vyvolá, <xref:System.ArgumentNullException> když je `null`parametr metody .

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 7

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód je ovlivněna těmito změnami, můžete provést následující kroky:

- Neexistuje žádné náhradní rozhraní `WriteProperty` API <xref:System.Text.Json.JsonElement>pro přetížení v . Místo toho můžete volat <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> jeden z přetížení <xref:System.Text.Json.JsonElement.WriteTo%2A> spolu s metodou k dosažení stejného výsledku. Například:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Přejmenujte `WriteValue` metodu na <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>. Parametr metody zůstane nezměněn. Například předchozí kód by měl být změněn na následující:

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Zpracování <xref:System.ArgumentNullException> příchozí volání <xref:System.Text.Json.JsonElement.WriteTo%2A> metody.

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
