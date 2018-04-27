---
title: Literál dokumentu XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c84fecbb035c229cc3576bc556db6ecb6f3934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="dc17c-102">Literál dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc17c-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="dc17c-103">Literál představující <xref:System.Xml.Linq.XDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="dc17c-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc17c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc17c-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="dc17c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="dc17c-105">Parts</span></span>  
  
|<span data-ttu-id="dc17c-106">Termín</span><span class="sxs-lookup"><span data-stu-id="dc17c-106">Term</span></span>|<span data-ttu-id="dc17c-107">Definice</span><span class="sxs-lookup"><span data-stu-id="dc17c-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="dc17c-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="dc17c-108">Optional.</span></span> <span data-ttu-id="dc17c-109">Literál text deklarace, které kódování dokumentu používá.</span><span class="sxs-lookup"><span data-stu-id="dc17c-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="dc17c-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="dc17c-110">Optional.</span></span> <span data-ttu-id="dc17c-111">Literál text.</span><span class="sxs-lookup"><span data-stu-id="dc17c-111">Literal text.</span></span> <span data-ttu-id="dc17c-112">Musí být "Ano" nebo "Ne".</span><span class="sxs-lookup"><span data-stu-id="dc17c-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="dc17c-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="dc17c-113">Optional.</span></span> <span data-ttu-id="dc17c-114">Seznam příkazů pro zpracování XML a komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="dc17c-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="dc17c-115">Má následující formát:</span><span class="sxs-lookup"><span data-stu-id="dc17c-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="dc17c-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="dc17c-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="dc17c-117">Každý `piComment` může být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="dc17c-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="dc17c-118">-   [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dc17c-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="dc17c-119">-   [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dc17c-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="dc17c-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="dc17c-120">Required.</span></span> <span data-ttu-id="dc17c-121">Kořenový element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dc17c-121">Root element of the document.</span></span> <span data-ttu-id="dc17c-122">Formát je jedním z těchto:</span><span class="sxs-lookup"><span data-stu-id="dc17c-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="dc17c-123">[Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dc17c-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="dc17c-124">Vložené výrazu ve formátu `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="dc17c-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="dc17c-125">`elementExp` Vrátí jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="dc17c-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="dc17c-126"><xref:System.Xml.Linq.XElement> Objektu.</span><span class="sxs-lookup"><span data-stu-id="dc17c-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="dc17c-127">Kolekce, která obsahuje jednu <xref:System.Xml.Linq.XElement> objekt a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty.</span><span class="sxs-lookup"><span data-stu-id="dc17c-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="dc17c-128">Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dc17c-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="dc17c-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc17c-129">Return Value</span></span>  
 <span data-ttu-id="dc17c-130"><xref:System.Xml.Linq.XDocument> Objektu.</span><span class="sxs-lookup"><span data-stu-id="dc17c-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc17c-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc17c-131">Remarks</span></span>  
 <span data-ttu-id="dc17c-132">Literál dokumentu XML je identifikována deklaraci XML na začátku literál.</span><span class="sxs-lookup"><span data-stu-id="dc17c-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="dc17c-133">I když každý literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet příkazů pro zpracování XML a komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="dc17c-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="dc17c-134">Literál dokumentu XML se nemůže vyskytovat v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="dc17c-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc17c-135">Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="dc17c-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="dc17c-136">To umožňuje kopírovat obsah z dokumentu XML a vložte jej přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dc17c-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="dc17c-137">Visual Basic – kompilátor převede literál dokumentu XML volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> a <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktory.</span><span class="sxs-lookup"><span data-stu-id="dc17c-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc17c-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc17c-138">Example</span></span>  
 <span data-ttu-id="dc17c-139">Následující příklad vytvoří dokument XML, který má deklarace XML, pokyny pro zpracování, komentáře a elementu, který obsahuje jiný element.</span><span class="sxs-lookup"><span data-stu-id="dc17c-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dc17c-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc17c-140">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [<span data-ttu-id="dc17c-141">Literál instrukcí pro zpracování XML</span><span class="sxs-lookup"><span data-stu-id="dc17c-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [<span data-ttu-id="dc17c-142">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="dc17c-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="dc17c-143">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="dc17c-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="dc17c-144">Literály XML</span><span class="sxs-lookup"><span data-stu-id="dc17c-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="dc17c-145">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc17c-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="dc17c-146">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="dc17c-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
