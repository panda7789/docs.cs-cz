---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237330"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Změnil se podpis JsonFactoryConverter. CreateConverter.

Aby se usnadnilo složení <xref:System.Text.Json.Serialization.JsonConverterFactory>, metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> byla veřejná a měla by mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="change-description"></a>Změnit popis

Signatura metody `CreateConverter` v .NET Core před verzí 3,0 Preview 8 byla: 

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

Před touto změnou bylo obtížné vytvořit zapečetěné převaděče pro vytváření, protože neexistoval žádný snadný způsob, jak z něho získat @no__t 0. Zpřístupnění metody pro vytváření veřejnosti a také předání aktuální <xref:System.Text.Json.JsonSerializerOptions> umožňuje mnohem flexibilnější kompozici.

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
