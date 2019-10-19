---
title: Příkaz Imports – obor názvů XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 0fca0caecfd69580510a539317856209108e5a32
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581770"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="bc937-102">Imports – Příkaz (obor názvů XML)</span><span class="sxs-lookup"><span data-stu-id="bc937-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="bc937-103">Importuje předpony oboru názvů XML pro použití v literálech XML a vlastnostech osy XML.</span><span class="sxs-lookup"><span data-stu-id="bc937-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc937-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc937-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="bc937-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bc937-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="bc937-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bc937-106">Optional.</span></span> <span data-ttu-id="bc937-107">Řetězec, podle kterého mohou prvky a atributy XML odkazovat na `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="bc937-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="bc937-108">Pokud není zadán žádný `xmlNamespacePrefix`, je importovaný obor názvů XML výchozím oborem názvů XML.</span><span class="sxs-lookup"><span data-stu-id="bc937-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="bc937-109">Musí být platný identifikátor XML.</span><span class="sxs-lookup"><span data-stu-id="bc937-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="bc937-110">Další informace najdete v tématu [Názvy deklarovaných elementů XML a atributů](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="bc937-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="bc937-111">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bc937-111">Required.</span></span> <span data-ttu-id="bc937-112">Řetězec identifikující obor názvů XML, který se má importovat</span><span class="sxs-lookup"><span data-stu-id="bc937-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc937-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc937-113">Remarks</span></span>

<span data-ttu-id="bc937-114">Pomocí příkazu `Imports` můžete definovat globální obory názvů XML, které lze použít s literály XML a vlastnostmi osy XML, nebo jako parametry předané do operátoru `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="bc937-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="bc937-115">(Informace o použití příkazu `Imports` pro import aliasu, který lze použít, kde se používají názvy typů ve vašem kódu, naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Syntaxe pro deklaraci oboru názvů XML pomocí příkazu `Imports` je shodná se syntaxí použitou v jazyce XML.</span><span class="sxs-lookup"><span data-stu-id="bc937-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="bc937-116">Proto můžete zkopírovat deklaraci oboru názvů ze souboru XML a použít ho v příkazu `Imports`.</span><span class="sxs-lookup"><span data-stu-id="bc937-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="bc937-117">Předpony oboru názvů XML jsou užitečné, pokud chcete opakovaně vytvářet elementy XML, které se nacházejí ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bc937-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="bc937-118">Předpona oboru názvů XML deklarovaná pomocí příkazu `Imports` je globální v tom smyslu, že je k dispozici pro veškerý kód v souboru.</span><span class="sxs-lookup"><span data-stu-id="bc937-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="bc937-119">Můžete ji použít při vytváření literálů elementů XML a při přístupu k vlastnostem osy XML.</span><span class="sxs-lookup"><span data-stu-id="bc937-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="bc937-120">Další informace naleznete v tématu vlastnosti [literálu elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) a [osy XML](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc937-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

<span data-ttu-id="bc937-121">Definujete-li globální obor názvů XML bez předpony oboru názvů (například `Imports <xmlns="http://SomeNameSpace>"`), tento obor názvů je považován za výchozí obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="bc937-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="bc937-122">Výchozí obor názvů XML se používá pro všechny literály elementu XML nebo vlastnosti osy atributu XML, které explicitně neurčují obor názvů.</span><span class="sxs-lookup"><span data-stu-id="bc937-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="bc937-123">Výchozí obor názvů se používá také v případě, že zadaný obor názvů je prázdným oborem názvů (tj. `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="bc937-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="bc937-124">Výchozí obor názvů XML se nevztahuje na atributy XML v literálech XML nebo na Vlastnosti osy atributu XML, které nemají obor názvů.</span><span class="sxs-lookup"><span data-stu-id="bc937-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="bc937-125">Obory názvů XML, které jsou definovány v literálu XML, které se nazývají *místní obory názvů XML*, mají přednost před obory názvů XML, které jsou definovány příkazem `Imports` jako globální.</span><span class="sxs-lookup"><span data-stu-id="bc937-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="bc937-126">Obory názvů XML, které jsou definovány příkazem `Imports`, mají přednost před obory názvů XML importovanými pro projekt Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bc937-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="bc937-127">Pokud literál XML definuje obor názvů XML, tento místní obor názvů neplatí pro vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="bc937-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="bc937-128">Globální obory názvů XML dodržují stejná pravidla pro obor a definici jako obory názvů .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc937-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="bc937-129">V důsledku toho můžete zahrnout příkaz `Imports` pro definování globálního oboru názvů XML kdekoli můžete importovat .NET Framework obor názvů.</span><span class="sxs-lookup"><span data-stu-id="bc937-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="bc937-130">To zahrnuje jak soubory kódu, tak importované obory názvů na úrovni projektu.</span><span class="sxs-lookup"><span data-stu-id="bc937-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="bc937-131">Informace o importovaných oborech názvů na úrovni projektu naleznete na [stránce odkazy, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bc937-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="bc937-132">Každý zdrojový soubor může obsahovat libovolný počet příkazů `Imports`.</span><span class="sxs-lookup"><span data-stu-id="bc937-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="bc937-133">Musí následovat po deklaracích možností, jako je například příkaz `Option Strict`, a musí předcházet deklarace programovacích prvků, jako jsou například `Module` nebo `Class` příkazy.</span><span class="sxs-lookup"><span data-stu-id="bc937-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="bc937-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc937-134">Example</span></span>

<span data-ttu-id="bc937-135">Následující příklad importuje výchozí obor názvů XML a obor názvů XML identifikovaný předponou `ns`.</span><span class="sxs-lookup"><span data-stu-id="bc937-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="bc937-136">Potom vytvoří literály XML, které používají oba obory názvů.</span><span class="sxs-lookup"><span data-stu-id="bc937-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="bc937-137">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="bc937-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="bc937-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc937-138">Example</span></span>

<span data-ttu-id="bc937-139">Následující příklad importuje předponu oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="bc937-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="bc937-140">Potom vytvoří literál XML, který používá předponu oboru názvů a zobrazí konečný formulář elementu.</span><span class="sxs-lookup"><span data-stu-id="bc937-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="bc937-141">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="bc937-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="bc937-142">Všimněte si, že kompilátor převedl předponu oboru názvů XML z globální předpony na definici místní předpony.</span><span class="sxs-lookup"><span data-stu-id="bc937-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="bc937-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc937-143">Example</span></span>

<span data-ttu-id="bc937-144">Následující příklad importuje předponu oboru názvů XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="bc937-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="bc937-145">Poté pomocí předpony oboru názvů vytvoří literál XML a přístup k prvnímu podřízenému uzlu s kvalifikovaným názvem `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="bc937-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="bc937-146">Tento kód zobrazí následující text:</span><span class="sxs-lookup"><span data-stu-id="bc937-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="bc937-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc937-147">See also</span></span>

- [<span data-ttu-id="bc937-148">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="bc937-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="bc937-149">Vlastnosti osy XML</span><span class="sxs-lookup"><span data-stu-id="bc937-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="bc937-150">Názvy deklarovaných XML elementů a atributů</span><span class="sxs-lookup"><span data-stu-id="bc937-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="bc937-151">Operátor GetXmlNamespace</span><span class="sxs-lookup"><span data-stu-id="bc937-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
