---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237330"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="911c6-101">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="911c6-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="911c6-102">Aby se usnadnilo složení <xref:System.Text.Json.Serialization.JsonConverterFactory>, metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> byla veřejná a měla by mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="911c6-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="911c6-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="911c6-103">Change description</span></span>

<span data-ttu-id="911c6-104">Signatura metody `CreateConverter` v .NET Core před verzí 3,0 Preview 8 byla:</span><span class="sxs-lookup"><span data-stu-id="911c6-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="911c6-105">V .NET Core 3,0 Preview 8 a novějších verzích je:</span><span class="sxs-lookup"><span data-stu-id="911c6-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="911c6-106">Před touto změnou bylo obtížné vytvořit zapečetěné převaděče pro vytváření, protože neexistoval žádný snadný způsob, jak z něho získat @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="911c6-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="911c6-107">Zpřístupnění metody pro vytváření veřejnosti a také předání aktuální <xref:System.Text.Json.JsonSerializerOptions> umožňuje mnohem flexibilnější kompozici.</span><span class="sxs-lookup"><span data-stu-id="911c6-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="911c6-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="911c6-108">Version introduced</span></span>

<span data-ttu-id="911c6-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="911c6-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="911c6-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="911c6-110">Recommended action</span></span>

<span data-ttu-id="911c6-111">Odvozené třídy musí být aktualizovány a znovu zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="911c6-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="911c6-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="911c6-112">Affected APIs</span></span>

<span data-ttu-id="911c6-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="911c6-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
