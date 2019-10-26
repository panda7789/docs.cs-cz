---
title: Odkaz na dynamické vlastnosti LINQ to XML
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: ca3684716f9b562d0e6a006c26730a1d1a28f8b1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920928"
---
# <a name="linq-to-xml-dynamic-properties"></a><span data-ttu-id="4d934-102">Dynamické vlastnosti LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="4d934-102">LINQ to XML dynamic properties</span></span>

<span data-ttu-id="4d934-103">V této části najdete referenční informace o dynamických vlastnostech v LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="4d934-103">This section provides reference information about the dynamic properties in LINQ to XML.</span></span> <span data-ttu-id="4d934-104">Konkrétně tyto vlastnosti jsou zpřístupněny <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> třídy, které jsou v oboru názvů <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="4d934-104">Specifically, these properties are exposed by the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, which are in the <xref:System.Xml.Linq> namespace.</span></span>

<span data-ttu-id="4d934-105">Jak je vysvětleno v tématu [Přehled datové vazby WPF s LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), každá z dynamických vlastností je ekvivalentní standardní veřejné vlastnosti nebo metody ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="4d934-105">As explained in the topic [Overview of WPF data binding with LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), each of the dynamic properties is equivalent to a standard public property or method in the same class.</span></span> <span data-ttu-id="4d934-106">Tyto standardní členy by se měly používat pro většinu účelů; dynamické vlastnosti jsou určené speciálně pro LINQ to XML scénáře datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="4d934-106">These standard members should be used for most purposes; dynamic properties are provided specifically for LINQ to XML data binding scenarios.</span></span> <span data-ttu-id="4d934-107">Další informace o standardních členech těchto tříd naleznete v tématu <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> referenční témata.</span><span class="sxs-lookup"><span data-stu-id="4d934-107">For more information about the standard members of these classes, see the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> reference topics.</span></span>

<span data-ttu-id="4d934-108">V souvislosti s jejich vyřešenými hodnotami jsou dynamické vlastnosti v této části rozdělené do dvou kategorií:</span><span class="sxs-lookup"><span data-stu-id="4d934-108">With respect to their resolved values, the dynamic properties in this section fall into two categories:</span></span>

- <span data-ttu-id="4d934-109">Jednoduché, například vlastnosti `Value` v třídách <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement>, které se překládají na jedinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d934-109">Simple ones, such as the `Value` properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes, that resolve to a single value.</span></span>

- <span data-ttu-id="4d934-110">Indexované hodnoty, jako jsou vlastnosti [prvků](elements-xelement-dynamic-property.md) a [následníků](descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement>, které se překládají na typ indexeru.</span><span class="sxs-lookup"><span data-stu-id="4d934-110">Indexed values, such as the [Elements](elements-xelement-dynamic-property.md) and [Descendants](descendants-xelement-dynamic-property.md) properties of <xref:System.Xml.Linq.XElement>, that resolve into an indexer type.</span></span> <span data-ttu-id="4d934-111">Aby byly typy indexerů přeloženy na požadovanou hodnotu nebo kolekci, je nutné předat rozšířený parametr názvu.</span><span class="sxs-lookup"><span data-stu-id="4d934-111">For indexer types to be resolved to the desired value or collection, an expanded name parameter must be passed to them.</span></span>

<span data-ttu-id="4d934-112">Všechny dynamické vlastnosti, které vracejí indexovanou hodnotu typu <xref:System.Collections.Generic.IEnumerable%601> použít odložené provádění.</span><span class="sxs-lookup"><span data-stu-id="4d934-112">All the dynamic properties that return an indexed value of type <xref:System.Collections.Generic.IEnumerable%601> use deferred execution.</span></span> <span data-ttu-id="4d934-113">Další informace o odloženém spuštění najdete v tématu [Úvod do dotazů LINQC#()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).</span><span class="sxs-lookup"><span data-stu-id="4d934-113">For more information about deferred execution, see [Introduction to LINQ queries (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).</span></span>

## <a name="reference"></a><span data-ttu-id="4d934-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="4d934-114">Reference</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="4d934-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d934-115">See also</span></span>

- [<span data-ttu-id="4d934-116">Datová vazba WPF s LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="4d934-116">WPF data binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="4d934-117">Datová vazba WPF s LINQ to XML – přehled</span><span class="sxs-lookup"><span data-stu-id="4d934-117">WPF data binding with LINQ to XML overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="4d934-118">Úvod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="4d934-118">Introduction to LINQ queries (C#)</span></span>](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
