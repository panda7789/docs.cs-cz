---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595676"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="fc460-101">Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.</span><span class="sxs-lookup"><span data-stu-id="fc460-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="fc460-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType>již neprezentuje úvodní `#` znak a již <xref:System.UriBuilder.Query?displayProperty=nameWithType> předřadí úvodní `?` znak, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="fc460-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fc460-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="fc460-103">Change description</span></span>

<span data-ttu-id="fc460-104"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> V .NET Framework vlastnosti <xref:System.UriBuilder.Query?displayProperty=nameWithType> a vždy předřadí znak `#` nebo `?` (v uvedeném pořadí) na hodnotu, která je ukládána.</span><span class="sxs-lookup"><span data-stu-id="fc460-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="fc460-105">Toto chování může mít za následek `#` více `?` nebo znaků v uložené hodnotě, pokud řetězec již obsahuje jeden z těchto úvodních znaků.</span><span class="sxs-lookup"><span data-stu-id="fc460-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="fc460-106">Například hodnota <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> může být `##main`.</span><span class="sxs-lookup"><span data-stu-id="fc460-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="fc460-107">Počínaje rozhraním .NET Core 1,0 tyto vlastnosti již neprezentují `#` znaky `?` ani pro uloženou hodnotu, je-li již na začátku řetězce přítomen některý z nich.</span><span class="sxs-lookup"><span data-stu-id="fc460-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fc460-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="fc460-108">Version introduced</span></span>

<span data-ttu-id="fc460-109">1.0</span><span class="sxs-lookup"><span data-stu-id="fc460-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc460-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="fc460-110">Recommended action</span></span>

<span data-ttu-id="fc460-111">Při nastavování hodnot vlastností už nemusíte explicitně odebírat žádné z těchto počátečních znaků.</span><span class="sxs-lookup"><span data-stu-id="fc460-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="fc460-112">To je užitečné hlavně v případě, že přidáváte hodnoty, protože už nemusíte odebírat úvodní `#` nebo `?` pokaždé, když se připojujete.</span><span class="sxs-lookup"><span data-stu-id="fc460-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="fc460-113">Například následující fragment kódu ukazuje rozdíl chování mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fc460-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="fc460-114">Ve .NET Framework je `????one=1&two=2&three=3&four=4`výstup.</span><span class="sxs-lookup"><span data-stu-id="fc460-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="fc460-115">Ve výstupu .NET Core je `?one=1&two=2&three=3&four=4`výstup.</span><span class="sxs-lookup"><span data-stu-id="fc460-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="fc460-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="fc460-116">Category</span></span>

<span data-ttu-id="fc460-117">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="fc460-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc460-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fc460-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
