---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615734"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="21331-101">Funkce XmlWriter vyvolá neplatné náhradní páry.</span><span class="sxs-lookup"><span data-stu-id="21331-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="21331-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="21331-102">Details</span></span>

<span data-ttu-id="21331-103">Pro aplikace, které cílí na .NET Framework 4.5.2 nebo předchozí verze, zapisuje neplatnou náhradní dvojici pomocí zpracování záložního použití výjimek, vždy výjimku vyvolá.</span><span class="sxs-lookup"><span data-stu-id="21331-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="21331-104">Pro aplikace cílené na .NET Framework 4,6 vyvolá pokus o zápis neplatného náhradního páru <xref:System.ArgumentException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="21331-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="21331-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="21331-105">Suggestion</span></span>

<span data-ttu-id="21331-106">V případě potřeby se toto přerušení dá vyhnout tím, že cílí na .NET Framework 4.5.2 nebo starší.</span><span class="sxs-lookup"><span data-stu-id="21331-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="21331-107">Alternativně je možné před zápisem do platného kódu XML předem zpracovat neplatné náhradní páry.</span><span class="sxs-lookup"><span data-stu-id="21331-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="21331-108">Name</span><span class="sxs-lookup"><span data-stu-id="21331-108">Name</span></span>    | <span data-ttu-id="21331-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="21331-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="21331-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="21331-110">Scope</span></span>   | <span data-ttu-id="21331-111">Edge</span><span class="sxs-lookup"><span data-stu-id="21331-111">Edge</span></span>        |
| <span data-ttu-id="21331-112">Verze</span><span class="sxs-lookup"><span data-stu-id="21331-112">Version</span></span> | <span data-ttu-id="21331-113">4.6</span><span class="sxs-lookup"><span data-stu-id="21331-113">4.6</span></span>         |
| <span data-ttu-id="21331-114">Typ</span><span class="sxs-lookup"><span data-stu-id="21331-114">Type</span></span>    | <span data-ttu-id="21331-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="21331-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="21331-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="21331-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
