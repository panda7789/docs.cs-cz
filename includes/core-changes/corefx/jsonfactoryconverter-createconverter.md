---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117122"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Změnil se podpis JsonFactoryConverter. CreateConverter.

Aby bylo možné zjednodušit <xref:System.Text.Json.Serialization.JsonConverterFactory> složení tříd, <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> byla metoda zveřejněna a měla by mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="details"></a>Podrobnosti

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

Před touto změnou bylo obtížné vytvořit zapečetěné převaděče objektu pro vytváření, protože <xref:System.Text.Json.Serialization.JsonConverter%601> z ní neexistoval snadný způsob, jak z něho získat. Zajištění veřejné metody výroby a také předání současného <xref:System.Text.Json.JsonSerializerOptions> povolení pro mnohem flexibilnější složení.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="recommended-action"></a>Doporučená akce

Odvozené třídy musí být aktualizovány a znovu zkompilovány.

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
