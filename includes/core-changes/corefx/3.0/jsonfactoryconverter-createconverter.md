---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147559"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="39d72-101">JsonFactoryConverter.CreateConverter podpis změněn</span><span class="sxs-lookup"><span data-stu-id="39d72-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="39d72-102">Pro usnadnění složení <xref:System.Text.Json.Serialization.JsonConverterFactory> tříd <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> byla metoda zveřejněna a byl jí <xref:System.Text.Json.JsonSerializerOptions>dán druhý argument typu .</span><span class="sxs-lookup"><span data-stu-id="39d72-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="39d72-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="39d72-103">Change description</span></span>

<span data-ttu-id="39d72-104">Podpis `CreateConverter` metody v rozhraní .NET Core před verzí 3.0 Preview 8 byl:</span><span class="sxs-lookup"><span data-stu-id="39d72-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="39d72-105">V rozhraní .NET Core 3.0 Preview 8 a novějších verzích je to:</span><span class="sxs-lookup"><span data-stu-id="39d72-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="39d72-106">Před touto změnou bylo obtížné sestavit uzavřené tovární konvertory, protože <xref:System.Text.Json.Serialization.JsonConverter%601> z ní nebyl snadný způsob, jak z ní dostat.</span><span class="sxs-lookup"><span data-stu-id="39d72-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="39d72-107">Zveřejnění tovární metody a také <xref:System.Text.Json.JsonSerializerOptions> předání proudu umožňuje mnohem flexibilnější složení.</span><span class="sxs-lookup"><span data-stu-id="39d72-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39d72-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="39d72-108">Version introduced</span></span>

<span data-ttu-id="39d72-109">3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="39d72-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39d72-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="39d72-110">Recommended action</span></span>

<span data-ttu-id="39d72-111">Odvozené třídy je třeba aktualizovat a znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="39d72-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39d72-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="39d72-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
