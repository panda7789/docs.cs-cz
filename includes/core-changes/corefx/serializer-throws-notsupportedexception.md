---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119280"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="cef95-101">Typ výjimky serializátoru JSON se `JsonException` změnil z na.`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="cef95-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="cef95-102">V .NET Core 3,0 Preview 6 až 8, serializátor vyvolá výjimku <xref:System.Text.Json.JsonException> , když zjistila nepodporovaný odvozený typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="cef95-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="cef95-103">Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá <xref:System.NotSupportedException> serializátor místo toho.</span><span class="sxs-lookup"><span data-stu-id="cef95-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cef95-104">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="cef95-104">Change description</span></span>

<span data-ttu-id="cef95-105">V .NET Core 3,0 Preview 6 až Preview 8, serializátor vyvolá výjimku <xref:System.Text.Json.JsonException> , když narazil na nepodporovaný odvozený typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="cef95-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="cef95-106">*Nepodporovaný typ odvozené kolekce* je libovolný typ kolekce, který není možné přiřadit k jednomu z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="cef95-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [<span data-ttu-id="cef95-107">Řetězec\<IDictionary, T ></span><span class="sxs-lookup"><span data-stu-id="cef95-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="cef95-108">Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá <xref:System.NotSupportedException> serializátor při zjištění nepodporovaného typu kolekce.</span><span class="sxs-lookup"><span data-stu-id="cef95-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="cef95-109">Nový typ výjimky lépe odráží důvod selhání operace deserializace.</span><span class="sxs-lookup"><span data-stu-id="cef95-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cef95-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="cef95-110">Version introduced</span></span>

<span data-ttu-id="cef95-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="cef95-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cef95-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="cef95-112">Recommended action</span></span>

<span data-ttu-id="cef95-113">Pokud při deserializaci <xref:System.Text.Json.JsonException> zachytíte, možná budete chtít zvážit také jejich <xref:System.NotSupportedException>zachycení.</span><span class="sxs-lookup"><span data-stu-id="cef95-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="cef95-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="cef95-114">Category</span></span>

<span data-ttu-id="cef95-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="cef95-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cef95-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cef95-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
