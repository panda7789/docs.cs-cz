---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021644"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="4ee05-101">Typ výjimky serializátoru Json byl změněn z `JsonException` na`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="4ee05-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="4ee05-102">V .NET Core 3.0 Náhled 6 až 8 <xref:System.Text.Json.JsonException> serializátor by vyvolat, když došlo k nepodporované odvozené kolekce typu.</span><span class="sxs-lookup"><span data-stu-id="4ee05-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="4ee05-103">Počínaje .NET Core 3.0 Náhled 9 serializátor vyvolá <xref:System.NotSupportedException> místo.</span><span class="sxs-lookup"><span data-stu-id="4ee05-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4ee05-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="4ee05-104">Change description</span></span>

<span data-ttu-id="4ee05-105">V .NET Core 3.0 Náhled 6 až Náhled <xref:System.Text.Json.JsonException> 8 serializátor by vyvolat, když došlo k nepodporované odvozené kolekce typu.</span><span class="sxs-lookup"><span data-stu-id="4ee05-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="4ee05-106">Nepodporovaný *typ odvozené kolekce* je libovolný typ kolekce, který nelze přiřadit jednomu z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="4ee05-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="4ee05-107">Řetězec IDictionary,t\<></span><span class="sxs-lookup"><span data-stu-id="4ee05-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="4ee05-108">Počínaje .NET Core 3.0 Náhled 9 serializátor vyvolá <xref:System.NotSupportedException> Při výskytu nepodporovaný typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="4ee05-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="4ee05-109">Nový typ výjimky lépe odráží, proč operace deserializace selhává.</span><span class="sxs-lookup"><span data-stu-id="4ee05-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4ee05-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="4ee05-110">Version introduced</span></span>

<span data-ttu-id="4ee05-111">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="4ee05-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4ee05-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4ee05-112">Recommended action</span></span>

<span data-ttu-id="4ee05-113">Pokud jste chytání <xref:System.Text.Json.JsonException> při deserializaci, možná budete <xref:System.NotSupportedException>chtít, aby zvážila také chytání .</span><span class="sxs-lookup"><span data-stu-id="4ee05-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="4ee05-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4ee05-114">Category</span></span>

<span data-ttu-id="4ee05-115">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="4ee05-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ee05-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4ee05-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
