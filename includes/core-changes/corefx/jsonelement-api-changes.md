---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237332"
---
### <a name="jsonelement-api-changes"></a>Změny rozhraní API JsonElement

Od verze .NET Core 3,0 Preview 7 se některá rozhraní API <xref:System.Text.Json.JsonElement> změnila tak, aby umožňovala snazší zjišťování a větší použitelnost.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 3,0 Preview 7 se rozhraní API <xref:System.Text.Json.JsonElement> změnila následujícím způsobem, aby bylo umožněno snazší zjišťování a větší použitelnost.

1. Všechna přetížení metod `WriteProperty` byla z <xref:System.Text.Json.JsonElement> odstraněna. To má vliv na následující kód:

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

1. `WriteValue` bylo přejmenováno na <xref:System.Text.Json.JsonElement.WriteTo%2A>. To má vliv na následující kód:

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> nyní vyvolá <xref:System.ArgumentNullException>, pokud je jeho parametr metody `null`.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 7

#### <a name="recommended-action"></a>Doporučená akce

Pokud je váš kód ovlivněn těmito změnami, můžete provést následující:

- Neexistuje žádné náhradní rozhraní API pro přetížení `WriteProperty` v <xref:System.Text.Json.JsonElement>. Místo toho můžete zavolat jedno z přetížení <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> spolu s metodou <xref:System.Text.Json.JsonElement.WriteTo%2A>, aby se zajištění stejný výsledek. Například:

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

- Zpracovává <xref:System.ArgumentNullException> v volání metody <xref:System.Text.Json.JsonElement.WriteTo%2A>.

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
