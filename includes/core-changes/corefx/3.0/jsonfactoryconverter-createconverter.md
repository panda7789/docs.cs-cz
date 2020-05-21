---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721044"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="f09e1-101">Změnil se podpis JsonFactoryConverter. CreateConverter.</span><span class="sxs-lookup"><span data-stu-id="f09e1-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="f09e1-102">Aby bylo možné zjednodušit složení <xref:System.Text.Json.Serialization.JsonConverterFactory> tříd, byla metoda zveřejněna a měla by <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> mít druhý argument typu <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="f09e1-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f09e1-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="f09e1-103">Change description</span></span>

<span data-ttu-id="f09e1-104">Signatura `CreateConverter` metody v .NET Core starší než verze 3,0 Preview 8 byla:</span><span class="sxs-lookup"><span data-stu-id="f09e1-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="f09e1-105">V .NET Core 3,0 Preview 8 a novějších verzích je:</span><span class="sxs-lookup"><span data-stu-id="f09e1-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="f09e1-106">Před touto změnou bylo obtížné vytvořit zapečetěné převaděče objektu pro vytváření, protože z ní neexistoval snadný způsob, jak <xref:System.Text.Json.Serialization.JsonConverter%601> z něho získat.</span><span class="sxs-lookup"><span data-stu-id="f09e1-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="f09e1-107">Zajištění veřejné metody výroby a také předání současného <xref:System.Text.Json.JsonSerializerOptions> povolení pro mnohem flexibilnější složení.</span><span class="sxs-lookup"><span data-stu-id="f09e1-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f09e1-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f09e1-108">Version introduced</span></span>

<span data-ttu-id="f09e1-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f09e1-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f09e1-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f09e1-110">Recommended action</span></span>

<span data-ttu-id="f09e1-111">Odvozené třídy musí být aktualizovány a znovu zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="f09e1-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f09e1-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f09e1-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
