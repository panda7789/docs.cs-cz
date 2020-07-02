---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620059"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="244ae-101">SoapFormatter nemůže deserializovat zatřiďovací tabulku a podobné objekty kolekce.</span><span class="sxs-lookup"><span data-stu-id="244ae-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="244ae-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="244ae-102">Details</span></span>

<span data-ttu-id="244ae-103"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName>Nezaručuje, že objekty serializované v rámci jedné .NET Framework verze budou úspěšně deserializovány pod jinou verzí.</span><span class="sxs-lookup"><span data-stu-id="244ae-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="244ae-104">Konkrétně některé seřazené kolekce (jako <xref:System.Collections.Hashtable?displayProperty=fullName> ) přidaly členy mezi 4,0 a 4,5, aby objekty těchto typů nebylo možné deserializovat pomocí .NET Framework 4,0, pokud byly serializovány pomocí .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="244ae-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="244ae-105">Všimněte si, že jsou-li Serializovaná data serializována i deserializována se stejnou .NET Framework verzí, nebude provedena žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="244ae-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="244ae-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="244ae-106">Suggestion</span></span>

<span data-ttu-id="244ae-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName>serializace by měla být nahrazena <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serializací nebo může <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> být odolná proti .NET Framework změnám.</span><span class="sxs-lookup"><span data-stu-id="244ae-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="244ae-108">Name</span><span class="sxs-lookup"><span data-stu-id="244ae-108">Name</span></span>    | <span data-ttu-id="244ae-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="244ae-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="244ae-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="244ae-110">Scope</span></span>   |<span data-ttu-id="244ae-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="244ae-111">Minor</span></span>|
|<span data-ttu-id="244ae-112">Verze</span><span class="sxs-lookup"><span data-stu-id="244ae-112">Version</span></span>|<span data-ttu-id="244ae-113">4.5</span><span class="sxs-lookup"><span data-stu-id="244ae-113">4.5</span></span>|
|<span data-ttu-id="244ae-114">Typ</span><span class="sxs-lookup"><span data-stu-id="244ae-114">Type</span></span>|<span data-ttu-id="244ae-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="244ae-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="244ae-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="244ae-116">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
