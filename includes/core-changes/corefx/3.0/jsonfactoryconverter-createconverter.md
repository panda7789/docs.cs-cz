---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568223"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Změnil se podpis JsonFactoryConverter. CreateConverter.

Pro usnadnění složení <xref:System.Text.Json.Serialization.JsonConverterFactory>ch tříd byla metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> zveřejněna a měla by mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="change-description"></a>Změnit popis

Signatura metody `CreateConverter` v .NET Core starší než verze 3,0 Preview 8 byla:

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

Před touto změnou bylo obtížné vytvořit zapečetěné převaděče pro vytváření, protože neexistoval snadný způsob, jak z něho získat <xref:System.Text.Json.Serialization.JsonConverter%601>. Zpřístupnění metody pro vytváření veřejnosti a také předání aktuální <xref:System.Text.Json.JsonSerializerOptions> umožňuje mnohem flexibilnější kompozici.

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
