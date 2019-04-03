---
title: Literál XML elementu (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 7bd47d2461ba86dfbd1d5ff5993382914116f9ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842249"
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="30e7e-102">Literál XML elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30e7e-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="30e7e-103">Literál, který představuje <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30e7e-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="30e7e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="30e7e-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="30e7e-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30e7e-106">Required.</span></span> <span data-ttu-id="30e7e-107">Otevře se počáteční značky elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="30e7e-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30e7e-108">Required.</span></span> <span data-ttu-id="30e7e-109">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-109">Name of the element.</span></span> <span data-ttu-id="30e7e-110">Formát je jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="30e7e-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="30e7e-111">Prostý text pro název elementu, formuláře `[ePrefix:]eName`, kde:</span><span class="sxs-lookup"><span data-stu-id="30e7e-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="30e7e-112">Část</span><span class="sxs-lookup"><span data-stu-id="30e7e-112">Part</span></span>|<span data-ttu-id="30e7e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="30e7e-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="30e7e-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-114">Optional.</span></span> <span data-ttu-id="30e7e-115">Předpona oboru názvů XML pro prvek.</span><span class="sxs-lookup"><span data-stu-id="30e7e-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="30e7e-116">Musí být globální obor názvů XML, který je definován s `Imports` prohlášení v souboru nebo na úrovni projektu, nebo místní obor názvů XML, který je definován v tomto elementu nebo nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="30e7e-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="30e7e-117">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30e7e-117">Required.</span></span> <span data-ttu-id="30e7e-118">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-118">Name of the element.</span></span> <span data-ttu-id="30e7e-119">Formát je jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="30e7e-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="30e7e-120">-Prostý text.</span><span class="sxs-lookup"><span data-stu-id="30e7e-120">-   Literal text.</span></span> <span data-ttu-id="30e7e-121">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="30e7e-122">– Vložený výraz ve tvaru `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="30e7e-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="30e7e-123">Typ `eNameExp` musí být `String` nebo typ, který je implicitně převést na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="30e7e-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="30e7e-124">Vložený výraz ve tvaru `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="30e7e-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="30e7e-125">Typ `nameExp` musí být `String` nebo implicitně převést na typ <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="30e7e-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="30e7e-126">Vložený výraz není povolen v ukončovací značky elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="30e7e-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-127">Optional.</span></span> <span data-ttu-id="30e7e-128">Seznam atributů deklarované v literálu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="30e7e-129">Každý `attribute` má jednu z následujících syntaxí:</span><span class="sxs-lookup"><span data-stu-id="30e7e-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="30e7e-130">Atribut přiřazení formuláře `[aPrefix:]aName=aValue`, kde:</span><span class="sxs-lookup"><span data-stu-id="30e7e-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="30e7e-131">Část</span><span class="sxs-lookup"><span data-stu-id="30e7e-131">Part</span></span>|<span data-ttu-id="30e7e-132">Popis</span><span class="sxs-lookup"><span data-stu-id="30e7e-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="30e7e-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-133">Optional.</span></span> <span data-ttu-id="30e7e-134">Předpona oboru názvů XML pro atribut.</span><span class="sxs-lookup"><span data-stu-id="30e7e-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="30e7e-135">Musí být globální obor názvů XML, který je definován s `Imports` příkazu nebo místní obor názvů XML, který je definován v tomto elementu nebo nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="30e7e-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="30e7e-136">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30e7e-136">Required.</span></span> <span data-ttu-id="30e7e-137">Název atributu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-137">Name of the attribute.</span></span> <span data-ttu-id="30e7e-138">Formát je jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="30e7e-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="30e7e-139">-Prostý text.</span><span class="sxs-lookup"><span data-stu-id="30e7e-139">-   Literal text.</span></span> <span data-ttu-id="30e7e-140">Zobrazit [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="30e7e-141">– Vložený výraz ve tvaru `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="30e7e-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="30e7e-142">Typ `aNameExp` musí být `String` nebo typ, který je implicitně převést na <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="30e7e-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="30e7e-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-143">Optional.</span></span> <span data-ttu-id="30e7e-144">Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-144">Value of the attribute.</span></span> <span data-ttu-id="30e7e-145">Formát je jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="30e7e-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="30e7e-146">– Literál textu v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="30e7e-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="30e7e-147">– Vložený výraz ve tvaru `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="30e7e-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="30e7e-148">Jakýkoli typ je povolen.</span><span class="sxs-lookup"><span data-stu-id="30e7e-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="30e7e-149">Vložený výraz ve tvaru `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="30e7e-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="30e7e-150">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-150">Optional.</span></span> <span data-ttu-id="30e7e-151">Určuje, zda elementu je prázdný element, bez obsahu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="30e7e-152">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30e7e-152">Required.</span></span> <span data-ttu-id="30e7e-153">Ukončí značky elementu počáteční nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="30e7e-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="30e7e-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-154">Optional.</span></span> <span data-ttu-id="30e7e-155">Obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="30e7e-156">Každý `content` může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="30e7e-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="30e7e-157">Prostý text.</span><span class="sxs-lookup"><span data-stu-id="30e7e-157">Literal text.</span></span> <span data-ttu-id="30e7e-158">Všechny prázdné znaky v `elementContents` stane, když je text literálu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="30e7e-159">Vložený výraz ve tvaru `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="30e7e-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="30e7e-160">Literál XML elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="30e7e-161">Literál komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="30e7e-161">XML comment literal.</span></span> <span data-ttu-id="30e7e-162">Zobrazit [literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="30e7e-163">XML literál instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="30e7e-163">XML processing instruction literal.</span></span> <span data-ttu-id="30e7e-164">Zobrazit [literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="30e7e-165">Literál XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="30e7e-165">XML CDATA literal.</span></span> <span data-ttu-id="30e7e-166">Zobrazit [literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="30e7e-167">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="30e7e-167">Optional.</span></span> <span data-ttu-id="30e7e-168">Představuje uzavírací značka pro element.</span><span class="sxs-lookup"><span data-stu-id="30e7e-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="30e7e-169">Volitelný `name` parametr není povolený. Pokud bude výsledek vložený výraz.</span><span class="sxs-lookup"><span data-stu-id="30e7e-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30e7e-170">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="30e7e-170">Return Value</span></span>  
 <span data-ttu-id="30e7e-171"><xref:System.Xml.Linq.XElement> Objektu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30e7e-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30e7e-172">Remarks</span></span>  
 <span data-ttu-id="30e7e-173">Syntaxe literál – element XML slouží k vytvoření <xref:System.Xml.Linq.XElement> objektů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30e7e-174">Literál XML může zahrnovat více řádků bez použití znaků pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="30e7e-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="30e7e-175">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30e7e-175">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="30e7e-176">Vložené výrazy formuláře `<%= exp %>` vám umožní přidat dynamické informace do literálů XML element.</span><span class="sxs-lookup"><span data-stu-id="30e7e-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="30e7e-177">Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="30e7e-178">Kompilátor jazyka Visual Basic převede literál XML elementu na volání <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktor a je-li vyžadován, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="30e7e-178">The Visual Basic compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="30e7e-179">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="30e7e-179">XML Namespaces</span></span>  
 <span data-ttu-id="30e7e-180">Předpony oboru názvů XML jsou užitečné, když máte k vytváření literálů XML s prvky z stejný obor názvů v mnoha případech v kódu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="30e7e-181">Můžete použít globální předpony oboru názvů XML, které definujete pomocí `Imports` příkazu nebo místní předpony, které definujete pomocí `xmlns:xmlPrefix="xmlNamespace"` syntaxe atributu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="30e7e-182">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="30e7e-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="30e7e-183">V souladu s pravidla oboru oborů názvů XML má místní předpony přednost před globální předpony.</span><span class="sxs-lookup"><span data-stu-id="30e7e-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="30e7e-184">Ale pokud literál XML definuje obor názvů XML, tento obor názvů není k dispozici na výrazy, které se zobrazují v vložený výraz.</span><span class="sxs-lookup"><span data-stu-id="30e7e-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="30e7e-185">Vložený výraz můžete přistupovat pouze globální obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="30e7e-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="30e7e-186">Kompilátor jazyka Visual Basic převede každý globální obor názvů XML, který používá literál XML do jedné definice místní obor názvů v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-186">The Visual Basic compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="30e7e-187">Globálními názvovými prostory XML, které se nepoužívají se nezobrazují v generovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30e7e-188">Příklad</span><span class="sxs-lookup"><span data-stu-id="30e7e-188">Example</span></span>  
 <span data-ttu-id="30e7e-189">Následující příklad ukazuje, jak vytvořit jednoduchý prvek XML, který má dvě vnořené prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="30e7e-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]  
  
 <span data-ttu-id="30e7e-190">V příkladu se zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="30e7e-190">The example displays the following text.</span></span> <span data-ttu-id="30e7e-191">Všimněte si, že je literál zachovává strukturu prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="30e7e-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="30e7e-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="30e7e-192">Example</span></span>  
 <span data-ttu-id="30e7e-193">Následující příklad ukazuje, jak používat vložené výrazy pro název elementu a vytvořit atributy.</span><span class="sxs-lookup"><span data-stu-id="30e7e-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]  
  
 <span data-ttu-id="30e7e-194">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="30e7e-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="30e7e-195">Příklad</span><span class="sxs-lookup"><span data-stu-id="30e7e-195">Example</span></span>  
 <span data-ttu-id="30e7e-196">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="30e7e-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="30e7e-197">Potom k vytvoření literálu XML používá předponu oboru názvů a zobrazí poslední formulář elementu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 <span data-ttu-id="30e7e-198">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="30e7e-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="30e7e-199">Všimněte si, že kompilátor převést předponu globálního oboru názvů XML na definici předpony oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="30e7e-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="30e7e-200">\<Ns:middle > předefinuje předponu oboru názvů XML pro prvek \<ns:inner1 > element.</span><span class="sxs-lookup"><span data-stu-id="30e7e-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="30e7e-201">Ale \<ns:inner2 > element používá obor názvů definovaný smyčkou `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="30e7e-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e7e-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30e7e-202">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="30e7e-203">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="30e7e-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="30e7e-204">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="30e7e-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="30e7e-205">Literál XML CDATA</span><span class="sxs-lookup"><span data-stu-id="30e7e-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [<span data-ttu-id="30e7e-206">Literály XML</span><span class="sxs-lookup"><span data-stu-id="30e7e-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="30e7e-207">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30e7e-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="30e7e-208">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="30e7e-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="30e7e-209">Příkaz Imports (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="30e7e-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
