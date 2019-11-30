---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568223"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="77750-101">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="77750-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="77750-102">Pro usnadnění složení <xref:System.Text.Json.Serialization.JsonConverterFactory>ch tříd byla metoda <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> zveřejněna a měla by mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="77750-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="77750-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="77750-103">Change description</span></span>

<span data-ttu-id="77750-104">Signatura metody `CreateConverter` v .NET Core starší než verze 3,0 Preview 8 byla:</span><span class="sxs-lookup"><span data-stu-id="77750-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="77750-105">V .NET Core 3,0 Preview 8 a novějších verzích je:</span><span class="sxs-lookup"><span data-stu-id="77750-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="77750-106">Před touto změnou bylo obtížné vytvořit zapečetěné převaděče pro vytváření, protože neexistoval snadný způsob, jak z něho získat <xref:System.Text.Json.Serialization.JsonConverter%601>.</span><span class="sxs-lookup"><span data-stu-id="77750-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="77750-107">Zpřístupnění metody pro vytváření veřejnosti a také předání aktuální <xref:System.Text.Json.JsonSerializerOptions> umožňuje mnohem flexibilnější kompozici.</span><span class="sxs-lookup"><span data-stu-id="77750-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="77750-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="77750-108">Version introduced</span></span>

<span data-ttu-id="77750-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="77750-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="77750-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="77750-110">Recommended action</span></span>

<span data-ttu-id="77750-111">Odvozené třídy musí být aktualizovány a znovu zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="77750-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="77750-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="77750-112">Affected APIs</span></span>

<span data-ttu-id="77750-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="77750-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
