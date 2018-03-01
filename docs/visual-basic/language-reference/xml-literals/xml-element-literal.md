---
title: "Literál XML elementu (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="4d220-102">Literál XML elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d220-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="4d220-103">Literál, který představuje <xref:System.Xml.Linq.XElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="4d220-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d220-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="4d220-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4d220-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="4d220-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d220-106">Required.</span></span> <span data-ttu-id="4d220-107">Otevře se počáteční značky elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="4d220-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d220-108">Required.</span></span> <span data-ttu-id="4d220-109">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-109">Name of the element.</span></span> <span data-ttu-id="4d220-110">Formát je jedním z těchto:</span><span class="sxs-lookup"><span data-stu-id="4d220-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="4d220-111">Literál text pro název elementu, formuláře `[ePrefix:]eName`, kde:</span><span class="sxs-lookup"><span data-stu-id="4d220-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="4d220-112">Část</span><span class="sxs-lookup"><span data-stu-id="4d220-112">Part</span></span>|<span data-ttu-id="4d220-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4d220-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="4d220-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-114">Optional.</span></span> <span data-ttu-id="4d220-115">Předpona oboru názvů XML pro element.</span><span class="sxs-lookup"><span data-stu-id="4d220-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="4d220-116">Musí být globální obor názvů XML, který je definován s `Imports` příkaz v souboru nebo na úrovni projektu nebo místní obor názvů XML, který je definován v tento element nebo nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="4d220-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="4d220-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d220-117">Required.</span></span> <span data-ttu-id="4d220-118">Název elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-118">Name of the element.</span></span> <span data-ttu-id="4d220-119">Formát je jedním z těchto:</span><span class="sxs-lookup"><span data-stu-id="4d220-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="4d220-120">– Text literál.</span><span class="sxs-lookup"><span data-stu-id="4d220-120">-   Literal text.</span></span> <span data-ttu-id="4d220-121">V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="4d220-122">-Vložených výrazu ve formátu `<%= eNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="4d220-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="4d220-123">Typ `eNameExp` musí být `String` , nebo je implicitně převést na typ <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="4d220-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="4d220-124">Vložené výrazu ve formátu `<%= nameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="4d220-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="4d220-125">Typ `nameExp` musí být `String` nebo implicitně převést na typ <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="4d220-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="4d220-126">Vložené výraz není povolen v uzavírací značka elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="4d220-127">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-127">Optional.</span></span> <span data-ttu-id="4d220-128">Seznam atributů deklarované v literál.</span><span class="sxs-lookup"><span data-stu-id="4d220-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="4d220-129">Každý `attribute` obsahuje jednu z následujících syntaxí:</span><span class="sxs-lookup"><span data-stu-id="4d220-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="4d220-130">Atribut přiřazení formuláře `[aPrefix:]aName=aValue`, kde:</span><span class="sxs-lookup"><span data-stu-id="4d220-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="4d220-131">Část</span><span class="sxs-lookup"><span data-stu-id="4d220-131">Part</span></span>|<span data-ttu-id="4d220-132">Popis</span><span class="sxs-lookup"><span data-stu-id="4d220-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="4d220-133">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-133">Optional.</span></span> <span data-ttu-id="4d220-134">Předpona oboru názvů XML pro atribut.</span><span class="sxs-lookup"><span data-stu-id="4d220-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="4d220-135">Musí být globální obor názvů XML, který je definován s `Imports` příkaz nebo místní obor názvů XML, který je definován v tento element nebo nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="4d220-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="4d220-136">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d220-136">Required.</span></span> <span data-ttu-id="4d220-137">Název atributu.</span><span class="sxs-lookup"><span data-stu-id="4d220-137">Name of the attribute.</span></span> <span data-ttu-id="4d220-138">Formát je jedním z těchto:</span><span class="sxs-lookup"><span data-stu-id="4d220-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="4d220-139">– Text literál.</span><span class="sxs-lookup"><span data-stu-id="4d220-139">-   Literal text.</span></span> <span data-ttu-id="4d220-140">V tématu [názvy deklarovaných XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="4d220-141">-Vložených výrazu ve formátu `<%= aNameExp %>`.</span><span class="sxs-lookup"><span data-stu-id="4d220-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="4d220-142">Typ `aNameExp` musí být `String` , nebo je implicitně převést na typ <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="4d220-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="4d220-143">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-143">Optional.</span></span> <span data-ttu-id="4d220-144">Hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="4d220-144">Value of the attribute.</span></span> <span data-ttu-id="4d220-145">Formát je jedním z těchto:</span><span class="sxs-lookup"><span data-stu-id="4d220-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="4d220-146">-Literálu textu v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="4d220-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="4d220-147">-Vložených výrazu ve formátu `<%= aValueExp %>`.</span><span class="sxs-lookup"><span data-stu-id="4d220-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="4d220-148">Je povolen libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="4d220-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="4d220-149">Vložené výrazu ve formátu `<%= aExp %>`.</span><span class="sxs-lookup"><span data-stu-id="4d220-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="4d220-150">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-150">Optional.</span></span> <span data-ttu-id="4d220-151">Označuje, že element je prázdný element, bez obsahu.</span><span class="sxs-lookup"><span data-stu-id="4d220-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="4d220-152">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4d220-152">Required.</span></span> <span data-ttu-id="4d220-153">Ukončí značky elementu počáteční nebo je prázdný.</span><span class="sxs-lookup"><span data-stu-id="4d220-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="4d220-154">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-154">Optional.</span></span> <span data-ttu-id="4d220-155">Obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="4d220-156">Každý `content` může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="4d220-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="4d220-157">Literál text.</span><span class="sxs-lookup"><span data-stu-id="4d220-157">Literal text.</span></span> <span data-ttu-id="4d220-158">Prázdné znaky v `elementContents` stane důležité, pokud je literál textu.</span><span class="sxs-lookup"><span data-stu-id="4d220-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="4d220-159">Vložené výrazu ve formátu `<%= contentExp %>`.</span><span class="sxs-lookup"><span data-stu-id="4d220-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="4d220-160">Literál XML elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="4d220-161">Literál komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="4d220-161">XML comment literal.</span></span> <span data-ttu-id="4d220-162">V tématu [literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="4d220-163">XML literál instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="4d220-163">XML processing instruction literal.</span></span> <span data-ttu-id="4d220-164">V tématu [literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="4d220-165">Literál XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="4d220-165">XML CDATA literal.</span></span> <span data-ttu-id="4d220-166">V tématu [literál XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="4d220-167">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4d220-167">Optional.</span></span> <span data-ttu-id="4d220-168">Představuje koncová značka elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="4d220-169">Volitelné `name` parametr není povolen, pokud je výsledkem výrazu embedded.</span><span class="sxs-lookup"><span data-stu-id="4d220-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d220-170">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4d220-170">Return Value</span></span>  
 <span data-ttu-id="4d220-171"><xref:System.Xml.Linq.XElement> Objektu.</span><span class="sxs-lookup"><span data-stu-id="4d220-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d220-172">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d220-172">Remarks</span></span>  
 <span data-ttu-id="4d220-173">Syntaxe literál XML elementu slouží k vytvoření <xref:System.Xml.Linq.XElement> objekty v kódu.</span><span class="sxs-lookup"><span data-stu-id="4d220-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d220-174">Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="4d220-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="4d220-175">Tato funkce umožňuje kopírovat obsah z dokumentu XML a vložte ji přímo do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="4d220-175">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="4d220-176">Vložené výrazy ve tvaru `<%= exp %>` vám umožní přidat dynamické informace literál XML elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="4d220-177">Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="4d220-178">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede literál XML elementu volání <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktor a, pokud je to požadováno, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="4d220-178">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="4d220-179">Obory názvů XML</span><span class="sxs-lookup"><span data-stu-id="4d220-179">XML Namespaces</span></span>  
 <span data-ttu-id="4d220-180">XML – předpony oboru názvů jsou užitečné při vytváření literálů XML s elementy ze stejného oboru názvů mnohokrát v kódu.</span><span class="sxs-lookup"><span data-stu-id="4d220-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="4d220-181">Můžete použít globální předpony oboru názvů XML, které definují pomocí `Imports` příkaz nebo místní předpony, které definují pomocí `xmlns:xmlPrefix="xmlNamespace"` atribut syntaxe.</span><span class="sxs-lookup"><span data-stu-id="4d220-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="4d220-182">Další informace najdete v tématu [příkaz Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="4d220-183">Místní předpony v souladu s oboru pravidla pro obory názvů XML, mají přednost před globální předpony.</span><span class="sxs-lookup"><span data-stu-id="4d220-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="4d220-184">Ale pokud literál XML definuje obor názvů XML, tento obor názvů není k dispozici na výrazy, které se zobrazují v embedded výrazu.</span><span class="sxs-lookup"><span data-stu-id="4d220-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="4d220-185">Vložené výraz můžete přistupovat pouze globální obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="4d220-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="4d220-186">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede každý globální obor názvů XML, který je používán literál XML do jednu definici místní obor názvů v generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4d220-186">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="4d220-187">Globální obory názvů XML, které nepoužívají se nezobrazí v generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4d220-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d220-188">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d220-188">Example</span></span>  
 <span data-ttu-id="4d220-189">Následující příklad ukazuje, jak vytvořit jednoduché element XML, který má dva vnořené prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="4d220-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 <span data-ttu-id="4d220-190">V příkladu se zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="4d220-190">The example displays the following text.</span></span> <span data-ttu-id="4d220-191">Všimněte si, že je literál zachovává strukturu prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="4d220-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="4d220-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d220-192">Example</span></span>  
 <span data-ttu-id="4d220-193">Následující příklad ukazuje, jak používat vložené výrazy k názvu elementu a vytvořte atributy.</span><span class="sxs-lookup"><span data-stu-id="4d220-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 <span data-ttu-id="4d220-194">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="4d220-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="4d220-195">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d220-195">Example</span></span>  
 <span data-ttu-id="4d220-196">Následující příklad deklaruje `ns` jako předponu oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="4d220-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="4d220-197">Poté používá předponu oboru názvů k vytvoření literál XML a zobrazí poslední formulář elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 <span data-ttu-id="4d220-198">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="4d220-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="4d220-199">Všimněte si, že kompilátor převést předponu globální obor názvů XML do definice předponu pro obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="4d220-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="4d220-200">\<Ns:middle > přináší Předpona oboru názvů XML pro element \<ns:inner1 > elementu.</span><span class="sxs-lookup"><span data-stu-id="4d220-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="4d220-201">Ale \<ns:inner2 > element používá obor názvů definované `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4d220-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d220-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d220-202">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="4d220-203">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="4d220-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="4d220-204">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="4d220-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="4d220-205">Literál XML CDATA</span><span class="sxs-lookup"><span data-stu-id="4d220-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [<span data-ttu-id="4d220-206">XML – literály</span><span class="sxs-lookup"><span data-stu-id="4d220-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="4d220-207">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d220-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="4d220-208">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="4d220-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="4d220-209">Imports – příkaz (Namespace XML)</span><span class="sxs-lookup"><span data-stu-id="4d220-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
