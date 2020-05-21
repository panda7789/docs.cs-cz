---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721044"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Změnil se podpis JsonFactoryConverter. CreateConverter.

Aby bylo možné zjednodušit složení <xref:System.Text.Json.Serialization.JsonConverterFactory> tříd, byla metoda zveřejněna a měla by <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions> .

#### <a name="change-description"></a>Popis změny

Signatura `CreateConverter` metody v .NET Core starší než verze 3,0 Preview 8 byla:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

V .NET Core 3,0 Preview 8 a novějších verzích je:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Před touto změnou bylo obtížné vytvořit zapečetěné převaděče objektu pro vytváření, protože z ní neexistoval snadný způsob, jak <xref:System.Text.Json.Serialization.JsonConverter%601> z něho získat. Zajištění veřejné metody výroby a také předání současného <xref:System.Text.Json.JsonSerializerOptions> povolení pro mnohem flexibilnější složení.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Odvozené třídy musí být aktualizovány a znovu zkompilovány.

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
