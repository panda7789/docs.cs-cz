---
title: Imports – příkaz - Namespace XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 8cce1cc918b150fdf30449f127b1e2f0a73e6f6c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973272"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="b53fc-102">Imports – Příkaz (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="b53fc-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="b53fc-103">Importuje předpon názvového prostoru XML pro použití v literály XML a vlastnosti OS XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b53fc-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="b53fc-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b53fc-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="b53fc-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b53fc-106">Optional.</span></span> <span data-ttu-id="b53fc-107">Řetězec, ve které XML elementů a atributů mohou odkazovat na `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="b53fc-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="b53fc-108">Pokud ne `xmlNamespacePrefix` je zadán, importované oboru názvů XML je výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="b53fc-109">Musí být platný identifikátor XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="b53fc-110">Další informace najdete v tématu [názvy z deklarované XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b53fc-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="b53fc-111">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b53fc-111">Required.</span></span> <span data-ttu-id="b53fc-112">Řetězec, který identifikuje importované oboru názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b53fc-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b53fc-113">Remarks</span></span>  
 <span data-ttu-id="b53fc-114">Můžete použít `Imports` příkaz k definování globálními názvovými prostory XML, který vám pomůže s literály XML a vlastnosti OS XML, nebo jako parametry předat `GetXmlNamespace` operátor.</span><span class="sxs-lookup"><span data-stu-id="b53fc-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="b53fc-115">(Další informace o použití `Imports` smlouvu pro import alias, který je možné, kde se používají názvy typů ve vašem kódu, naleznete v tématu [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Syntaxe pro deklarování obor názvů XML s použitím `Imports` příkaz je stejná jako syntaxe používané ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="b53fc-116">Proto, můžete zkopírovat deklarace oboru názvů ze souboru XML a použít ho `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b53fc-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="b53fc-117">Předpony oboru názvů XML jsou užitečné, pokud chcete vytvořit opakovaně elementů XML, které pocházejí ze stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b53fc-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="b53fc-118">Předpona oboru názvů XML deklarována s `Imports` příkaz je globální v tom smyslu, že je k dispozici pro všechen kód v souboru.</span><span class="sxs-lookup"><span data-stu-id="b53fc-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="b53fc-119">Můžete ho používat při vytváření elementu literály XML a při přístupu k vlastnosti osy XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="b53fc-120">Další informace najdete v tématu [literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="b53fc-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>  
  
 <span data-ttu-id="b53fc-121">Pokud můžete definovat globální obor názvů XML bez předpony oboru názvů (například `Imports <xmlns="http://SomeNameSpace>"`), tento obor názvů se považuje za výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="b53fc-122">Výchozí obor názvů XML se používá pro jakoukoli element literály XML a vlastnosti osy atributu XML, které není explicitně zadán obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b53fc-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="b53fc-123">Výchozí obor názvů se také používá, pokud zadaný obor názvů není prázdný obor názvů (to znamená `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="b53fc-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="b53fc-124">Výchozí obor názvů XML se nevztahuje k atributům XML v literálech XML a vlastnosti osy atributu XML, které nemají žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b53fc-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="b53fc-125">Obory názvů XML, které jsou definovány v XML literál, který se nazývá *místní obory názvů XML*, přednost před obory názvů XML, které jsou definovány `Imports` příkaz jako globální.</span><span class="sxs-lookup"><span data-stu-id="b53fc-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="b53fc-126">Obory názvů XML, které jsou definovány `Imports` příkaz přednost importovat pro projekt jazyka Visual Basic obory názvů XML.</span><span class="sxs-lookup"><span data-stu-id="b53fc-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="b53fc-127">Pokud literál XML definuje obor názvů XML, že místní obor názvů se nevztahují na vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="b53fc-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="b53fc-128">Globálními názvovými prostory XML řídit stejnými pravidly určení oboru a definice jako obory názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b53fc-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="b53fc-129">V důsledku toho může obsahovat `Imports` příkaz k definování globální obor názvů XML kdekoli můžete importovat obor názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b53fc-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="b53fc-130">To zahrnuje soubory s kódem a importovaných oborů názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="b53fc-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="b53fc-131">Informace o importovaných oborů názvů na úrovni projektu, naleznete v tématu [odkazy na stránky, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b53fc-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="b53fc-132">Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="b53fc-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="b53fc-133">Tyto musí následovat možnost deklarace, jako `Option Strict` příkaz a musí předcházet programovací element deklarace, jako například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="b53fc-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b53fc-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="b53fc-134">Example</span></span>  
 <span data-ttu-id="b53fc-135">Následující příklad importuje výchozí názvový prostor XML a obor názvů XML identifikovat s předponou `ns`.</span><span class="sxs-lookup"><span data-stu-id="b53fc-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="b53fc-136">Potom vytvoří literály XML, které používají oba obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b53fc-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]  
  
 <span data-ttu-id="b53fc-137">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="b53fc-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="b53fc-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b53fc-138">Example</span></span>  
 <span data-ttu-id="b53fc-139">Následující příklad importuje předponu oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="b53fc-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="b53fc-140">Potom vytvoří literál XML, který používá předponu oboru názvů a zobrazí poslední formulář daného elementu.</span><span class="sxs-lookup"><span data-stu-id="b53fc-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 <span data-ttu-id="b53fc-141">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="b53fc-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="b53fc-142">Všimněte si, že kompilátor převést předponu oboru názvů XML z globální předpony s definicí místní předponu.</span><span class="sxs-lookup"><span data-stu-id="b53fc-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b53fc-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="b53fc-143">Example</span></span>  
 <span data-ttu-id="b53fc-144">Následující příklad importuje předponu oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="b53fc-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="b53fc-145">Poté použije předponu oboru názvů XML vytvoření literálu a přístup k první podřízený uzel s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="b53fc-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="b53fc-146">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="b53fc-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="b53fc-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b53fc-147">See also</span></span>
- [<span data-ttu-id="b53fc-148">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="b53fc-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="b53fc-149">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="b53fc-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="b53fc-150">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="b53fc-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="b53fc-151">Operátor GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="b53fc-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
