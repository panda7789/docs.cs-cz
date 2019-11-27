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
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347031"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="fa8bc-102">Literál XML elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa8bc-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="fa8bc-103">Literál, který představuje objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa8bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa8bc-104">Syntax</span></span>

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a><span data-ttu-id="fa8bc-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="fa8bc-105">Parts</span></span>

- `<`

  <span data-ttu-id="fa8bc-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-106">Required.</span></span> <span data-ttu-id="fa8bc-107">Otevře značku počátečního elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-107">Opens the starting element tag.</span></span>

- `name`

  <span data-ttu-id="fa8bc-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-108">Required.</span></span> <span data-ttu-id="fa8bc-109">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-109">Name of the element.</span></span> <span data-ttu-id="fa8bc-110">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-110">The format is one of the following:</span></span>

  - <span data-ttu-id="fa8bc-111">Textový literál pro název prvku `[ePrefix:]eName`formuláře, kde:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>

    |<span data-ttu-id="fa8bc-112">Částí</span><span class="sxs-lookup"><span data-stu-id="fa8bc-112">Part</span></span>|<span data-ttu-id="fa8bc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fa8bc-113">Description</span></span>|
    |---|---|
    |`ePrefix`|<span data-ttu-id="fa8bc-114">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-114">Optional.</span></span> <span data-ttu-id="fa8bc-115">Předpona oboru názvů XML pro element.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="fa8bc-116">Musí být globální obor názvů XML, který je definován pomocí příkazu `Imports` v souboru nebo na úrovni projektu, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`eName`|<span data-ttu-id="fa8bc-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-117">Required.</span></span> <span data-ttu-id="fa8bc-118">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-118">Name of the element.</span></span> <span data-ttu-id="fa8bc-119">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="fa8bc-120">-Literal text.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-120">- Literal text.</span></span> <span data-ttu-id="fa8bc-121">Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="fa8bc-122">– Vložený výraz formuláře `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-122">- Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="fa8bc-123">Typ `eNameExp` musí být `String` nebo typ, který lze implicitně převést na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|

  - <span data-ttu-id="fa8bc-124">Vložený výraz formuláře `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="fa8bc-125">Typ `nameExp` musí být `String` nebo typ implicitně převoditelné na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="fa8bc-126">Vložený výraz není povolený v uzavírací značce elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-126">An embedded expression is not allowed in a closing tag of an element.</span></span>

- `attributeList`

  <span data-ttu-id="fa8bc-127">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-127">Optional.</span></span> <span data-ttu-id="fa8bc-128">Seznam atributů deklarovaných v literálu</span><span class="sxs-lookup"><span data-stu-id="fa8bc-128">List of attributes declared in the literal.</span></span>

  `attribute [ attribute ... ]`

  <span data-ttu-id="fa8bc-129">Každý `attribute` má jednu z následujících syntaxí:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-129">Each `attribute` has one of the following syntaxes:</span></span>

  - <span data-ttu-id="fa8bc-130">Přiřazení atributu `[aPrefix:]aName=aValue`formuláře, kde:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>

    |<span data-ttu-id="fa8bc-131">Částí</span><span class="sxs-lookup"><span data-stu-id="fa8bc-131">Part</span></span>|<span data-ttu-id="fa8bc-132">Popis</span><span class="sxs-lookup"><span data-stu-id="fa8bc-132">Description</span></span>|
    |---|---|
    |`aPrefix`|<span data-ttu-id="fa8bc-133">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-133">Optional.</span></span> <span data-ttu-id="fa8bc-134">Předpona oboru názvů XML pro atribut</span><span class="sxs-lookup"><span data-stu-id="fa8bc-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="fa8bc-135">Musí být globální obor názvů XML, který je definován pomocí příkazu `Imports`, nebo místní obor názvů XML, který je definován v tomto elementu nebo v nadřazeném elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|
    |`aName`|<span data-ttu-id="fa8bc-136">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-136">Required.</span></span> <span data-ttu-id="fa8bc-137">Název atributu</span><span class="sxs-lookup"><span data-stu-id="fa8bc-137">Name of the attribute.</span></span> <span data-ttu-id="fa8bc-138">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="fa8bc-139">-Literal text.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-139">- Literal text.</span></span> <span data-ttu-id="fa8bc-140">Viz [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="fa8bc-141">– Vložený výraz formuláře `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-141">- Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="fa8bc-142">Typ `aNameExp` musí být `String` nebo typ, který lze implicitně převést na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|
    |`aValue`|<span data-ttu-id="fa8bc-143">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-143">Optional.</span></span> <span data-ttu-id="fa8bc-144">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="fa8bc-144">Value of the attribute.</span></span> <span data-ttu-id="fa8bc-145">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="fa8bc-146">-Literal text uzavřený v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-146">- Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="fa8bc-147">– Vložený výraz formuláře `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-147">- Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="fa8bc-148">Je povolen libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-148">Any type is allowed.</span></span>|

  - <span data-ttu-id="fa8bc-149">Vložený výraz formuláře `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-149">Embedded expression of the form `<%= aExp %>`.</span></span>

- `/>`

  <span data-ttu-id="fa8bc-150">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-150">Optional.</span></span> <span data-ttu-id="fa8bc-151">Označuje, že element je prázdný prvek bez obsahu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-151">Indicates that the element is an empty element, without content.</span></span>

- `>`

  <span data-ttu-id="fa8bc-152">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-152">Required.</span></span> <span data-ttu-id="fa8bc-153">Ukončí značku začátku nebo prázdného prvku.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-153">Ends the beginning or empty element tag.</span></span>

- `elementContents`

  <span data-ttu-id="fa8bc-154">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-154">Optional.</span></span> <span data-ttu-id="fa8bc-155">Obsah elementu</span><span class="sxs-lookup"><span data-stu-id="fa8bc-155">Content of the element.</span></span>

  `content [ content ... ]`

  <span data-ttu-id="fa8bc-156">Každá `content` může být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-156">Each `content` can be one of the following:</span></span>

  - <span data-ttu-id="fa8bc-157">Textový literál</span><span class="sxs-lookup"><span data-stu-id="fa8bc-157">Literal text.</span></span> <span data-ttu-id="fa8bc-158">Všechny prázdné znaky v `elementContents` budou významné, pokud je nějaký textový literál.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>

  - <span data-ttu-id="fa8bc-159">Vložený výraz formuláře `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-159">Embedded expression of the form `<%= contentExp %>`.</span></span>

  - <span data-ttu-id="fa8bc-160">Literál elementu XML.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-160">XML element literal.</span></span>

  - <span data-ttu-id="fa8bc-161">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="fa8bc-161">XML comment literal.</span></span> <span data-ttu-id="fa8bc-162">Viz [literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>

  - <span data-ttu-id="fa8bc-163">Literál instrukcí pro zpracování XML</span><span class="sxs-lookup"><span data-stu-id="fa8bc-163">XML processing instruction literal.</span></span> <span data-ttu-id="fa8bc-164">Viz [literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>

  - <span data-ttu-id="fa8bc-165">Literál XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-165">XML CDATA literal.</span></span> <span data-ttu-id="fa8bc-166">Viz [literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>

- `</[name]>`

  <span data-ttu-id="fa8bc-167">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-167">Optional.</span></span> <span data-ttu-id="fa8bc-168">Představuje uzavírací značku elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="fa8bc-169">Nepovinný parametr `name` není povolený, pokud se jedná o výsledek vloženého výrazu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>

## <a name="return-value"></a><span data-ttu-id="fa8bc-170">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa8bc-170">Return Value</span></span>

<span data-ttu-id="fa8bc-171">Objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-171">An <xref:System.Xml.Linq.XElement> object.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa8bc-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa8bc-172">Remarks</span></span>

<span data-ttu-id="fa8bc-173">Můžete použít syntaxi literálu elementu XML k vytvoření <xref:System.Xml.Linq.XElement> objektů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>

> [!NOTE]
> <span data-ttu-id="fa8bc-174">Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="fa8bc-175">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>

<span data-ttu-id="fa8bc-176">Vložené výrazy formuláře `<%= exp %>` umožňují přidat dynamické informace do literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="fa8bc-177">Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>

<span data-ttu-id="fa8bc-178">Kompilátor Visual Basic převádí literál elementu XML na volání konstruktoru <xref:System.Xml.Linq.XElement.%23ctor%2A> a v případě potřeby konstruktor <xref:System.Xml.Linq.XAttribute.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="fa8bc-179">XML – obory názvů</span><span class="sxs-lookup"><span data-stu-id="fa8bc-179">XML Namespaces</span></span>

<span data-ttu-id="fa8bc-180">Předpony oboru názvů XML jsou užitečné v případě, že je nutné vytvořit literály XML s prvky ze stejného oboru názvů, kolikrát je kód.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="fa8bc-181">Můžete použít globální předpony oboru názvů XML, které definujete pomocí příkazu `Imports`, nebo místní předpony, které definujete pomocí `xmlns:xmlPrefix="xmlNamespace"` syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="fa8bc-182">Další informace naleznete v tématu [příkaz Imports (obor názvů XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="fa8bc-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

<span data-ttu-id="fa8bc-183">V souladu s pravidly oboru názvů XML mají místní předpony přednost před globálními předponami.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="fa8bc-184">Pokud však literál XML definuje obor názvů XML, tento obor názvů není k dispozici pro výrazy, které se zobrazí ve vloženém výrazu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="fa8bc-185">Vložený výraz má přístup pouze k globálnímu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-185">The embedded expression can access only the global XML namespace.</span></span>

<span data-ttu-id="fa8bc-186">Kompilátor Visual Basic převádí všechny globální obory názvů XML, které jsou používány literály XML, do jedné definice místního oboru názvů v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="fa8bc-187">Globální obory názvů XML, které se nepoužívají, se ve vygenerovaném kódu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>

## <a name="example"></a><span data-ttu-id="fa8bc-188">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa8bc-188">Example</span></span>

<span data-ttu-id="fa8bc-189">Následující příklad ukazuje, jak vytvořit jednoduchý element XML, který má dva vnořené prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

<span data-ttu-id="fa8bc-190">V příkladu se zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-190">The example displays the following text.</span></span> <span data-ttu-id="fa8bc-191">Všimněte si, že literál zachovává strukturu prázdných prvků.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-191">Notice that the literal preserves the structure of the empty elements.</span></span>

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a><span data-ttu-id="fa8bc-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa8bc-192">Example</span></span>

<span data-ttu-id="fa8bc-193">Následující příklad ukazuje, jak použít vložené výrazy k pojmenování elementu a vytváření atributů.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

<span data-ttu-id="fa8bc-194">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-194">This code displays the following text:</span></span>

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a><span data-ttu-id="fa8bc-195">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa8bc-195">Example</span></span>

<span data-ttu-id="fa8bc-196">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="fa8bc-197">Potom používá předponu oboru názvů k vytvoření literálu XML a zobrazí konečný formulář elementu.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="fa8bc-198">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-198">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="fa8bc-199">Všimněte si, že kompilátor převedl předponu globálního oboru názvů XML do definice předpony pro obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="fa8bc-200">Element \<NS: Middle > předefinuje předponu oboru názvů XML pro element \<NS: inner1 >.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="fa8bc-201">Nicméně element \<NS: inner2 > používá obor názvů definovaný příkazem `Imports`.</span><span class="sxs-lookup"><span data-stu-id="fa8bc-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa8bc-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa8bc-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="fa8bc-203">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="fa8bc-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="fa8bc-204">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="fa8bc-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="fa8bc-205">Literál XML CDATA</span><span class="sxs-lookup"><span data-stu-id="fa8bc-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="fa8bc-206">Literály XML</span><span class="sxs-lookup"><span data-stu-id="fa8bc-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="fa8bc-207">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa8bc-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="fa8bc-208">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="fa8bc-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="fa8bc-209">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="fa8bc-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
