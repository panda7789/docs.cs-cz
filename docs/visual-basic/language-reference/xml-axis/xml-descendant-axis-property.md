---
title: Vlastnost osy nástupce XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400250"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="7450c-102">Vlastnost osy nástupce XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7450c-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="7450c-103">Poskytuje přístup k následníkům následujících objektů: <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.</span><span class="sxs-lookup"><span data-stu-id="7450c-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="7450c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7450c-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="7450c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7450c-105">Parts</span></span>

<span data-ttu-id="7450c-106">`object`Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="7450c-106">`object` Required.</span></span> <span data-ttu-id="7450c-107"><xref:System.Xml.Linq.XElement>Objekt, <xref:System.Xml.Linq.XDocument> objekt, kolekce <xref:System.Xml.Linq.XElement> objektů nebo kolekce <xref:System.Xml.Linq.XDocument> objektů.</span><span class="sxs-lookup"><span data-stu-id="7450c-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="7450c-108">`...<`Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="7450c-108">`...<` Required.</span></span> <span data-ttu-id="7450c-109">Označuje začátek vlastnosti následníka.</span><span class="sxs-lookup"><span data-stu-id="7450c-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="7450c-110">`descendant`Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="7450c-110">`descendant` Required.</span></span> <span data-ttu-id="7450c-111">Název potomkních uzlů, které mají být přístupné, z formuláře [ `prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="7450c-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="7450c-112">Část</span><span class="sxs-lookup"><span data-stu-id="7450c-112">Part</span></span>|<span data-ttu-id="7450c-113">Description</span><span class="sxs-lookup"><span data-stu-id="7450c-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="7450c-114">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7450c-114">Optional.</span></span> <span data-ttu-id="7450c-115">Předpona oboru názvů XML pro podřízený uzel</span><span class="sxs-lookup"><span data-stu-id="7450c-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="7450c-116">Musí se jednat o globální obor názvů XML, který je definován pomocí `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7450c-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="7450c-117">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7450c-117">Required.</span></span> <span data-ttu-id="7450c-118">Místní název odvozeného uzlu.</span><span class="sxs-lookup"><span data-stu-id="7450c-118">Local name of the descendant node.</span></span> <span data-ttu-id="7450c-119">Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7450c-119">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="7450c-120">`>`Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="7450c-120">`>` Required.</span></span> <span data-ttu-id="7450c-121">Označuje konec vlastnosti odvozené osy.</span><span class="sxs-lookup"><span data-stu-id="7450c-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="7450c-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7450c-122">Return Value</span></span>

<span data-ttu-id="7450c-123">Kolekce objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="7450c-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="7450c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7450c-124">Remarks</span></span>

<span data-ttu-id="7450c-125">Vlastnost osy následníka XML můžete použít pro přístup k potomkovým uzlům podle názvu <xref:System.Xml.Linq.XElement> z <xref:System.Xml.Linq.XDocument> objektu nebo nebo z kolekce <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objektů nebo.</span><span class="sxs-lookup"><span data-stu-id="7450c-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="7450c-126">Použijte vlastnost XML `Value` pro přístup k hodnotě prvního podřízeného uzlu ve vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="7450c-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="7450c-127">Další informace najdete v tématu [vlastnost hodnoty XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="7450c-127">For more information, see [XML Value Property](xml-value-property.md).</span></span>

<span data-ttu-id="7450c-128">Kompilátor Visual Basic převádí vlastnosti následníka na volání <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7450c-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="7450c-129">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="7450c-129">XML Namespaces</span></span>

<span data-ttu-id="7450c-130">Název v Vlastnosti osy následníka může použít pouze obory názvů XML deklarované globálně s `Imports` příkazem.</span><span class="sxs-lookup"><span data-stu-id="7450c-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="7450c-131">Nemůže používat obory názvů XML deklarované místně v rámci literálů elementů XML.</span><span class="sxs-lookup"><span data-stu-id="7450c-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="7450c-132">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7450c-132">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="7450c-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="7450c-133">Example</span></span>

<span data-ttu-id="7450c-134">Následující příklad ukazuje, jak přistupovat k hodnotě prvního odvozeného uzlu s názvem `name` a hodnoty všech potomkních uzlů s názvem `phone` z `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="7450c-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="7450c-135">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="7450c-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="7450c-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="7450c-136">Example</span></span>

<span data-ttu-id="7450c-137">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="7450c-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="7450c-138">Poté pomocí předpony oboru názvů vytvoří literál XML a přistupuje k hodnotě prvního podřízeného uzlu s kvalifikovaným názvem `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="7450c-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="7450c-139">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="7450c-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="7450c-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="7450c-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="7450c-141">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="7450c-141">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="7450c-142">Literály XML</span><span class="sxs-lookup"><span data-stu-id="7450c-142">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="7450c-143">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7450c-143">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="7450c-144">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="7450c-144">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
