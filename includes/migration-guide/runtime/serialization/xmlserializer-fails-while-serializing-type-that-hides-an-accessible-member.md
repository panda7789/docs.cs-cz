---
ms.openlocfilehash: eafbdd2d42977381fb4d77748a3c9a2595ff2936
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620056"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="03340-101">XmlSerializer se nezdařil při serializaci typu, který skrývá přístupný člen s nedostupným.</span><span class="sxs-lookup"><span data-stu-id="03340-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="03340-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="03340-102">Details</span></span>

<span data-ttu-id="03340-103">Při serializaci odvozeného typu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> může selhat, pokud typ obsahuje nedostupné pole nebo vlastnost, která skrývá (pomocí klíčového slova New) pole nebo vlastnost se stejným názvem, který byl dříve přístupný (například veřejný) na základním typu.</span><span class="sxs-lookup"><span data-stu-id="03340-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="03340-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="03340-104">Suggestion</span></span>

<span data-ttu-id="03340-105">Tento problém lze vyřešit tak, že vytvoříte nový, skryjete člena, který je přístupný pro <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (například tím, že ho označíte jako veřejný). Případně se následující nastavení konfigurace vrátí na 4,0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> chování, což vyřeší problém:</span><span class="sxs-lookup"><span data-stu-id="03340-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="03340-106">Name</span><span class="sxs-lookup"><span data-stu-id="03340-106">Name</span></span>    | <span data-ttu-id="03340-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="03340-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="03340-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="03340-108">Scope</span></span>   |<span data-ttu-id="03340-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="03340-109">Minor</span></span>|
|<span data-ttu-id="03340-110">Verze</span><span class="sxs-lookup"><span data-stu-id="03340-110">Version</span></span>|<span data-ttu-id="03340-111">4.5</span><span class="sxs-lookup"><span data-stu-id="03340-111">4.5</span></span>|
|<span data-ttu-id="03340-112">Typ</span><span class="sxs-lookup"><span data-stu-id="03340-112">Type</span></span>|<span data-ttu-id="03340-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="03340-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03340-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="03340-114">Affected APIs</span></span>

-<xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType></li></ul>|
