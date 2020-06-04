---
title: Literál XML elementu
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400186"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="a0c53-102">Literál XML elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0c53-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="a0c53-103">Literál, který představuje <xref:System.Xml.Linq.XElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="a0c53-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0c53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0c53-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="a0c53-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a0c53-105">Parts</span></span>

- `<`

  <span data-ttu-id="a0c53-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0c53-106">Required.</span></span> <span data-ttu-id="a0c53-107">Otevře značku počátečního elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="a0c53-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0c53-108">Required.</span></span> <span data-ttu-id="a0c53-109">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-109">Name of the element.</span></span> <span data-ttu-id="a0c53-110">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="a0c53-110">The format is one of the following:</span></span>

  - <span data-ttu-id="a0c53-111">Textový literál pro název prvku formuláře `[ePrefix:]eName` , kde:</span><span class="sxs-lookup"><span data-stu-id="a0c53-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="a0c53-112">Část</span><span class="sxs-lookup"><span data-stu-id="a0c53-112">Part</span></span>|<span data-ttu-id="a0c53-113">Description</span><span class="sxs-lookup"><span data-stu-id="a0c53-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="a0c53-114">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-114">Optional.</span></span> <span data-ttu-id="a0c53-115">Předpona oboru názvů XML pro element.</span><span class="sxs-lookup"><span data-stu-id="a0c53-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="a0c53-116">Musí se jednat o globální obor názvů XML, který je definován pomocí `Imports` příkazu v souboru nebo na úrovni projektu, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="a0c53-117">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0c53-117">Required.</span></span> <span data-ttu-id="a0c53-118">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-118">Name of the element.</span></span> <span data-ttu-id="a0c53-119">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="a0c53-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="a0c53-120">-Literal text.</span><span class="sxs-lookup"><span data-stu-id="a0c53-120">- Literal text.</span></span> <span data-ttu-id="a0c53-121">Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="a0c53-122">– Vložený výraz formuláře `<%= eNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="a0c53-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="a0c53-123">Typ `eNameExp` musí být `String` nebo typ, který je implicitně převoditelný na <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="a0c53-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="a0c53-124">Vložený `<%= nameExp %>` výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="a0c53-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="a0c53-125">Typ `nameExp` musí být `String` nebo typ, který lze implicitně převést na <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="a0c53-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="a0c53-126">Vložený výraz není povolený v uzavírací značce elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="a0c53-127">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-127">Optional.</span></span> <span data-ttu-id="a0c53-128">Seznam atributů deklarovaných v literálu</span><span class="sxs-lookup"><span data-stu-id="a0c53-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="a0c53-129">Každá `attribute` z nich má jednu z následujících syntaxí:</span><span class="sxs-lookup"><span data-stu-id="a0c53-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="a0c53-130">Přiřazení atributu formuláře `[aPrefix:]aName=aValue` , kde:</span><span class="sxs-lookup"><span data-stu-id="a0c53-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="a0c53-131">Část</span><span class="sxs-lookup"><span data-stu-id="a0c53-131">Part</span></span>|<span data-ttu-id="a0c53-132">Description</span><span class="sxs-lookup"><span data-stu-id="a0c53-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="a0c53-133">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-133">Optional.</span></span> <span data-ttu-id="a0c53-134">Předpona oboru názvů XML pro atribut</span><span class="sxs-lookup"><span data-stu-id="a0c53-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="a0c53-135">Musí se jednat o globální obor názvů XML, který je definován pomocí `Imports` příkazu, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="a0c53-136">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0c53-136">Required.</span></span> <span data-ttu-id="a0c53-137">Název atributu</span><span class="sxs-lookup"><span data-stu-id="a0c53-137">Name of the attribute.</span></span> <span data-ttu-id="a0c53-138">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="a0c53-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="a0c53-139">-Literal text.</span><span class="sxs-lookup"><span data-stu-id="a0c53-139">- Literal text.</span></span> <span data-ttu-id="a0c53-140">Viz [Názvy deklarovaných elementů XML a atributů](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-140">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="a0c53-141">– Vložený výraz formuláře `<%= aNameExp %>` .</span><span class="sxs-lookup"><span data-stu-id="a0c53-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="a0c53-142">Typ `aNameExp` musí být `String` nebo typ, který je implicitně převoditelný na <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="a0c53-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="a0c53-143">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-143">Optional.</span></span> <span data-ttu-id="a0c53-144">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="a0c53-144">Value of the attribute.</span></span> <span data-ttu-id="a0c53-145">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="a0c53-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="a0c53-146">-Literal text uzavřený v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="a0c53-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="a0c53-147">– Vložený výraz formuláře `<%= aValueExp %>` .</span><span class="sxs-lookup"><span data-stu-id="a0c53-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="a0c53-148">Je povolen libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="a0c53-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="a0c53-149">Vložený `<%= aExp %>` výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="a0c53-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="a0c53-150">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-150">Optional.</span></span> <span data-ttu-id="a0c53-151">Označuje, že element je prázdný prvek bez obsahu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="a0c53-152">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0c53-152">Required.</span></span> <span data-ttu-id="a0c53-153">Ukončí značku začátku nebo prázdného prvku.</span><span class="sxs-lookup"><span data-stu-id="a0c53-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="a0c53-154">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-154">Optional.</span></span> <span data-ttu-id="a0c53-155">Obsah elementu</span><span class="sxs-lookup"><span data-stu-id="a0c53-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="a0c53-156">Každá `content` z těchto možností může být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="a0c53-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="a0c53-157">Textový literál</span><span class="sxs-lookup"><span data-stu-id="a0c53-157">Literal text.</span></span> <span data-ttu-id="a0c53-158">Všechny prázdné znaky v `elementContents` je významné, pokud existuje nějaký literálový text.</span><span class="sxs-lookup"><span data-stu-id="a0c53-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="a0c53-159">Vložený `<%= contentExp %>` výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="a0c53-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="a0c53-160">Literál elementu XML.</span><span class="sxs-lookup"><span data-stu-id="a0c53-160">XML element literal.</span></span>

  - <span data-ttu-id="a0c53-161">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a0c53-161">XML comment literal.</span></span> <span data-ttu-id="a0c53-162">Viz [literál komentáře XML](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-162">See [XML Comment Literal](xml-comment-literal.md).</span></span>

  - <span data-ttu-id="a0c53-163">Literál instrukcí pro zpracování XML</span><span class="sxs-lookup"><span data-stu-id="a0c53-163">XML processing instruction literal.</span></span> <span data-ttu-id="a0c53-164">Viz [literál instrukcí pro zpracování XML](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-164">See [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="a0c53-165">Literál XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="a0c53-165">XML CDATA literal.</span></span> <span data-ttu-id="a0c53-166">Viz [literál XML CDATA](xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-166">See [XML CDATA Literal](xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="a0c53-167">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a0c53-167">Optional.</span></span> <span data-ttu-id="a0c53-168">Představuje uzavírací značku elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="a0c53-169">Volitelný `name` parametr není povolen, pokud je výsledkem vloženého výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="a0c53-170">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0c53-170">Return Value</span></span>

<span data-ttu-id="a0c53-171">Objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a0c53-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0c53-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0c53-172">Remarks</span></span>

<span data-ttu-id="a0c53-173">Můžete použít syntaxi literálu elementu XML k vytvoření <xref:System.Xml.Linq.XElement> objektů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="a0c53-174">Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="a0c53-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="a0c53-175">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="a0c53-176">Vložené výrazy formuláře `<%= exp %>` umožňují přidat dynamické informace k literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="a0c53-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="a0c53-177">Další informace najdete v tématu [vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-177">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="a0c53-178">Kompilátor Visual Basic převádí literál elementu XML na volání <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktoru a, pokud je požadován, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a0c53-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="a0c53-179">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="a0c53-179">XML Namespaces</span></span>

<span data-ttu-id="a0c53-180">Předpony oboru názvů XML jsou užitečné v případě, že je nutné vytvořit literály XML s prvky ze stejného oboru názvů, kolikrát je kód.</span><span class="sxs-lookup"><span data-stu-id="a0c53-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="a0c53-181">Můžete použít globální předpony oboru názvů XML, které definujete pomocí `Imports` příkazu, nebo místní předpony, které definujete pomocí `xmlns:xmlPrefix="xmlNamespace"` syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="a0c53-182">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a0c53-182">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="a0c53-183">V souladu s pravidly oboru názvů XML mají místní předpony přednost před globálními předponami.</span><span class="sxs-lookup"><span data-stu-id="a0c53-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="a0c53-184">Pokud však literál XML definuje obor názvů XML, tento obor názvů není k dispozici pro výrazy, které se zobrazí ve vloženém výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="a0c53-185">Vložený výraz má přístup pouze k globálnímu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="a0c53-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="a0c53-186">Kompilátor Visual Basic převádí všechny globální obory názvů XML, které jsou používány literály XML, do jedné definice místního oboru názvů v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="a0c53-187">Globální obory názvů XML, které se nepoužívají, se ve vygenerovaném kódu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="a0c53-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="a0c53-188">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c53-188">Example</span></span>

<span data-ttu-id="a0c53-189">Následující příklad ukazuje, jak vytvořit jednoduchý element XML, který má dva vnořené prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="a0c53-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="a0c53-190">V příkladu se zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="a0c53-190">The example displays the following text.</span></span> <span data-ttu-id="a0c53-191">Všimněte si, že literál zachovává strukturu prázdných prvků.</span><span class="sxs-lookup"><span data-stu-id="a0c53-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="a0c53-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c53-192">Example</span></span>

<span data-ttu-id="a0c53-193">Následující příklad ukazuje, jak použít vložené výrazy k pojmenování elementu a vytváření atributů.</span><span class="sxs-lookup"><span data-stu-id="a0c53-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="a0c53-194">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="a0c53-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="a0c53-195">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c53-195">Example</span></span>

<span data-ttu-id="a0c53-196">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="a0c53-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="a0c53-197">Potom používá předponu oboru názvů k vytvoření literálu XML a zobrazí konečný formulář elementu.</span><span class="sxs-lookup"><span data-stu-id="a0c53-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="a0c53-198">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="a0c53-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="a0c53-199">Všimněte si, že kompilátor převedl předponu globálního oboru názvů XML do definice předpony pro obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="a0c53-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="a0c53-200">\<ns:middle>Element předefinuje předponu oboru názvů XML pro \<ns:inner1> element.</span><span class="sxs-lookup"><span data-stu-id="a0c53-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="a0c53-201">\<ns:inner2>Element však používá obor názvů definovaný `Imports` příkazem.</span><span class="sxs-lookup"><span data-stu-id="a0c53-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0c53-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c53-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="a0c53-203">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="a0c53-203">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="a0c53-204">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a0c53-204">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="a0c53-205">Literál XML CDATA</span><span class="sxs-lookup"><span data-stu-id="a0c53-205">XML CDATA Literal</span></span>](xml-cdata-literal.md)
- [<span data-ttu-id="a0c53-206">Literály XML</span><span class="sxs-lookup"><span data-stu-id="a0c53-206">XML Literals</span></span>](index.md)
- [<span data-ttu-id="a0c53-207">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0c53-207">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="a0c53-208">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="a0c53-208">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="a0c53-209">Imports – Příkaz (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="a0c53-209">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
