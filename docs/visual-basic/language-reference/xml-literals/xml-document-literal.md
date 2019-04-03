---
title: Literál dokumentu XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814624"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="a8f2b-102">Literál dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8f2b-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="a8f2b-103">Literál představující <xref:System.Xml.Linq.XDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8f2b-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="a8f2b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a8f2b-105">Parts</span></span>  
  
|<span data-ttu-id="a8f2b-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a8f2b-106">Term</span></span>|<span data-ttu-id="a8f2b-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a8f2b-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="a8f2b-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-108">Optional.</span></span> <span data-ttu-id="a8f2b-109">Deklarace kódování, které používá dokumentu prostý text.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="a8f2b-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-110">Optional.</span></span> <span data-ttu-id="a8f2b-111">Prostý text.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-111">Literal text.</span></span> <span data-ttu-id="a8f2b-112">Musí být "Ano" nebo "Ne".</span><span class="sxs-lookup"><span data-stu-id="a8f2b-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="a8f2b-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-113">Optional.</span></span> <span data-ttu-id="a8f2b-114">Seznam pokyny pro zpracování XML a komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="a8f2b-115">Má následující formát:</span><span class="sxs-lookup"><span data-stu-id="a8f2b-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="a8f2b-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="a8f2b-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="a8f2b-117">Každý `piComment` může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="a8f2b-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="a8f2b-118">-   [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a8f2b-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="a8f2b-119">-   [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a8f2b-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="a8f2b-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-120">Required.</span></span> <span data-ttu-id="a8f2b-121">Kořenový element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-121">Root element of the document.</span></span> <span data-ttu-id="a8f2b-122">Formát je jeden z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="a8f2b-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="a8f2b-123">[Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a8f2b-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="a8f2b-124">Vložený výraz ve tvaru `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="a8f2b-125">`elementExp` Vrátí jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="a8f2b-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="a8f2b-126"><xref:System.Xml.Linq.XElement> Objektu.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="a8f2b-127">Kolekce, která obsahuje jeden <xref:System.Xml.Linq.XElement> objektu a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="a8f2b-128">Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a8f2b-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="a8f2b-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8f2b-129">Return Value</span></span>  
 <span data-ttu-id="a8f2b-130"><xref:System.Xml.Linq.XDocument> Objektu.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8f2b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8f2b-131">Remarks</span></span>  
 <span data-ttu-id="a8f2b-132">Literál dokumentu XML je identifikován deklarace XML na začátek literálu.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="a8f2b-133">I když každá literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet pokyny pro zpracování XML a komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="a8f2b-134">Literál dokumentu XML se nemůže objevit v elementu jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8f2b-135">Literál XML může zahrnovat více řádků bez použití znaků pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="a8f2b-136">To umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="a8f2b-137">Kompilátor jazyka Visual Basic převede literál dokumentu XML na volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> a <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktory.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8f2b-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8f2b-138">Example</span></span>  
 <span data-ttu-id="a8f2b-139">Následující příklad vytvoří dokument XML, který má deklarace XML, instrukce pro zpracování, komentáře a element, který obsahuje jiný prvek.</span><span class="sxs-lookup"><span data-stu-id="a8f2b-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f2b-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8f2b-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="a8f2b-141">Literál instrukcí pro zpracování XML</span><span class="sxs-lookup"><span data-stu-id="a8f2b-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [<span data-ttu-id="a8f2b-142">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a8f2b-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [<span data-ttu-id="a8f2b-143">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="a8f2b-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="a8f2b-144">Literály XML</span><span class="sxs-lookup"><span data-stu-id="a8f2b-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="a8f2b-145">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8f2b-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="a8f2b-146">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="a8f2b-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
