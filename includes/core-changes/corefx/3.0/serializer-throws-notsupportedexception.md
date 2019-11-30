---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568088"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="495d7-101">Typ výjimky serializátoru JSON se změnil z `JsonException` na `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="495d7-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="495d7-102">V .NET Core 3,0 Preview 6 až 8 by serializátor vyvolal <xref:System.Text.Json.JsonException>, když narazil na nepodporovaný odvozený typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="495d7-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="495d7-103">Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá serializátor místo toho <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="495d7-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="495d7-104">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="495d7-104">Change description</span></span>

<span data-ttu-id="495d7-105">V .NET Core 3,0 Preview 6 až Preview 8 by serializátor vyvolal <xref:System.Text.Json.JsonException>, když narazil na nepodporovaný odvozený typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="495d7-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="495d7-106">*Nepodporovaný typ odvozené kolekce* je libovolný typ kolekce, který není možné přiřadit k jednomu z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="495d7-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="495d7-107">Řetězec IDictionary\<, T ></span><span class="sxs-lookup"><span data-stu-id="495d7-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="495d7-108">Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá serializátor při zjištění nepodporovaného typu kolekce <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="495d7-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="495d7-109">Nový typ výjimky lépe odráží důvod selhání operace deserializace.</span><span class="sxs-lookup"><span data-stu-id="495d7-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="495d7-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="495d7-110">Version introduced</span></span>

<span data-ttu-id="495d7-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="495d7-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="495d7-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="495d7-112">Recommended action</span></span>

<span data-ttu-id="495d7-113">Pokud při deserializaci zachytíte <xref:System.Text.Json.JsonException>, možná budete chtít zvážit také zachytávání <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="495d7-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="495d7-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="495d7-114">Category</span></span>

<span data-ttu-id="495d7-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="495d7-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="495d7-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="495d7-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
