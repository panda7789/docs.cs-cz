---
title: Imports – Příkaz (obor názvů XML)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: ba7475416d8a4e2eb3c892d457c03eeb695045eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604559"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="e5bf2-102">Imports – Příkaz (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="e5bf2-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="e5bf2-103">Importuje předpon oboru názvů XML pro použití v literály XML a vlastnosti osy XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5bf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5bf2-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="e5bf2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e5bf2-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="e5bf2-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-106">Optional.</span></span> <span data-ttu-id="e5bf2-107">Řetězec, ve které XML elementů a atributů může odkazovat na `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="e5bf2-108">Pokud žádné `xmlNamespacePrefix` je uvedený importované obor názvů XML je výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="e5bf2-109">Musí být platný identifikátor XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="e5bf2-110">Další informace najdete v tématu [názvy z deklarovaný XML elementů a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e5bf2-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="e5bf2-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-111">Required.</span></span> <span data-ttu-id="e5bf2-112">Řetězec identifikující importovaných obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5bf2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5bf2-113">Remarks</span></span>  
 <span data-ttu-id="e5bf2-114">Můžete použít `Imports` příkaz k definování globální obory názvů XML, který můžete použít s literály XML a vlastnosti osy XML nebo jako parametry předat `GetXmlNamespace` operátor.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="e5bf2-115">(Informace o používání `Imports` příkaz pro import alias, který je možné, kdy se používá název typu ve vašem kódu najdete v části [příkaz Imports (Namespace .NET a typ)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Syntaxe deklarace oboru názvů XML s použitím `Imports` příkaz je shodná se syntaxí používá v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="e5bf2-116">Proto můžete zkopírovat deklaraci oboru názvů ze souboru XML a použít ho `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="e5bf2-117">XML – předpony oboru názvů jsou užitečné, pokud chcete vytvořit opakovaně elementů XML, které jsou ze stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="e5bf2-118">Předpona oboru názvů XML deklarovat s `Imports` příkaz je globální v tom smyslu, že je k dispozici všechny kód v souboru.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="e5bf2-119">Můžete ho použít při vytváření element literály XML a při přístup k vlastnosti osy XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="e5bf2-120">Další informace najdete v tématu [literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [vlastnosti osy XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e5bf2-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span></span>  
  
 <span data-ttu-id="e5bf2-121">Pokud definujete globální obor názvů XML bez předpony oboru názvů (například `Imports <xmlns="http://SomeNameSpace>"`), tento obor názvů se považuje za výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="e5bf2-122">U elementu XML – literály nebo vlastnosti osy atributu XML, které explicitně nezadávejte obor názvů se používá výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="e5bf2-123">Výchozí obor názvů se také používá, pokud je zadaný obor názvů prázdného oboru názvů (tedy `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="e5bf2-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="e5bf2-124">Výchozí obor názvů XML nevztahuje atributům XML v literálech XML a vlastnosti osy atributu XML, které nemají obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="e5bf2-125">XML obory názvů, které jsou definovány v XML literálu, které se nazývají *místní obory názvů XML*, mají přednost před obory názvů XML, které jsou definovány `Imports` příkaz jako globální.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="e5bf2-126">Obory názvů XML, které jsou definovány `Imports` příkaz mají přednost před obory názvů XML importu projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="e5bf2-127">Pokud literál XML definuje obor názvů XML, že místní obor názvů se nevztahuje na vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="e5bf2-128">Globální obory názvů XML použijte stejná nastavení oboru a definice pravidla jako obory názvů v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="e5bf2-129">V důsledku toho můžete použít `Imports` příkaz k definování globální obor názvů XML kdekoli můžete importovat obor názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="e5bf2-130">To zahrnuje soubory kódu a importovaných oborů názvů úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="e5bf2-131">Informace o úrovni projektu importovaných oborů názvů najdete v tématu [stránka odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e5bf2-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="e5bf2-132">Každý zdrojový soubor může obsahovat libovolný počet `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="e5bf2-133">Tyto postupujte možnost deklarace, jako `Option Strict` příkaz a musí předcházet programovací element deklarace, jako například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5bf2-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5bf2-134">Example</span></span>  
 <span data-ttu-id="e5bf2-135">Následující příklad importuje výchozí obor názvů XML a označeny předponu oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="e5bf2-136">Pak vytvoří literálů XML, které používají oba obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 <span data-ttu-id="e5bf2-137">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e5bf2-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="e5bf2-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5bf2-138">Example</span></span>  
 <span data-ttu-id="e5bf2-139">Následující příklad importuje Předpona oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="e5bf2-140">Pak vytvoří literálu kód XML, který používá Předpona oboru názvů a zobrazí poslední formulář elementu.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 <span data-ttu-id="e5bf2-141">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e5bf2-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="e5bf2-142">Všimněte si, že kompilátor převést Předpona oboru názvů XML z globální předpony na definici místní předponu.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5bf2-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5bf2-143">Example</span></span>  
 <span data-ttu-id="e5bf2-144">Následující příklad importuje Předpona oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="e5bf2-145">Poté použije Předpona oboru názvů k vytvoření literál XML a přístup k první podřízený uzel s kvalifikovaný název `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="e5bf2-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 <span data-ttu-id="e5bf2-146">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="e5bf2-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="e5bf2-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5bf2-147">See Also</span></span>  
 [<span data-ttu-id="e5bf2-148">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="e5bf2-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="e5bf2-149">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="e5bf2-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="e5bf2-150">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="e5bf2-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="e5bf2-151">Operátor GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="e5bf2-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
