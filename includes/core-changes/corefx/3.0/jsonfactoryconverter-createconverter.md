---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147559"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter.CreateConverter podpis změněn

Pro usnadnění složení <xref:System.Text.Json.Serialization.JsonConverterFactory> tříd <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> byla metoda zveřejněna a byl jí <xref:System.Text.Json.JsonSerializerOptions>dán druhý argument typu .

#### <a name="change-description"></a>Popis změny

Podpis `CreateConverter` metody v rozhraní .NET Core před verzí 3.0 Preview 8 byl:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

V rozhraní .NET Core 3.0 Preview 8 a novějších verzích je to:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Před touto změnou bylo obtížné sestavit uzavřené tovární konvertory, protože <xref:System.Text.Json.Serialization.JsonConverter%601> z ní nebyl snadný způsob, jak z ní dostat. Zveřejnění tovární metody a také <xref:System.Text.Json.JsonSerializerOptions> předání proudu umožňuje mnohem flexibilnější složení.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 8

#### <a name="recommended-action"></a>Doporučená akce

Odvozené třídy je třeba aktualizovat a znovu zkompilovat.

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
