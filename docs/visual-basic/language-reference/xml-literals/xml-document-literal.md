---
title: Literál dokumentu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400199"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="ddd1d-102">Literál dokumentu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddd1d-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="ddd1d-103">Literál představující <xref:System.Xml.Linq.XDocument> objekt.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddd1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddd1d-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ddd1d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ddd1d-105">Parts</span></span>  
  
|<span data-ttu-id="ddd1d-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="ddd1d-106">Term</span></span>|<span data-ttu-id="ddd1d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ddd1d-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="ddd1d-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-108">Optional.</span></span> <span data-ttu-id="ddd1d-109">Textový literál, který deklaruje, který kódování dokumentu používá.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="ddd1d-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-110">Optional.</span></span> <span data-ttu-id="ddd1d-111">Textový literál</span><span class="sxs-lookup"><span data-stu-id="ddd1d-111">Literal text.</span></span> <span data-ttu-id="ddd1d-112">Musí být "Ano" nebo "ne".</span><span class="sxs-lookup"><span data-stu-id="ddd1d-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="ddd1d-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-113">Optional.</span></span> <span data-ttu-id="ddd1d-114">Seznam instrukcí pro zpracování XML a komentářů XML</span><span class="sxs-lookup"><span data-stu-id="ddd1d-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="ddd1d-115">Má následující formát:</span><span class="sxs-lookup"><span data-stu-id="ddd1d-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="ddd1d-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="ddd1d-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="ddd1d-117">Každá `piComment` z těchto možností může být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="ddd1d-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="ddd1d-118">-   [Literál instrukcí pro zpracování XML](xml-processing-instruction-literal.md)</span><span class="sxs-lookup"><span data-stu-id="ddd1d-118">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="ddd1d-119">-   [Literál komentáře XML](xml-comment-literal.md)</span><span class="sxs-lookup"><span data-stu-id="ddd1d-119">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="ddd1d-120">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-120">Required.</span></span> <span data-ttu-id="ddd1d-121">Kořenový element dokumentu</span><span class="sxs-lookup"><span data-stu-id="ddd1d-121">Root element of the document.</span></span> <span data-ttu-id="ddd1d-122">Formát je jeden z následujících:</span><span class="sxs-lookup"><span data-stu-id="ddd1d-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="ddd1d-123">[Literál elementu XML](xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="ddd1d-123">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="ddd1d-124">Vložený `<%=` výraz formuláře `elementExp` `%>`</span><span class="sxs-lookup"><span data-stu-id="ddd1d-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="ddd1d-125">`elementExp`Vrátí jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="ddd1d-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="ddd1d-126">Objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="ddd1d-127">Kolekce, která obsahuje jeden <xref:System.Xml.Linq.XElement> objekt a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objektů a <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="ddd1d-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="ddd1d-128">Další informace najdete v tématu [vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ddd1d-128">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="ddd1d-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ddd1d-129">Return Value</span></span>  
 <span data-ttu-id="ddd1d-130">Objekt <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddd1d-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddd1d-131">Remarks</span></span>  
 <span data-ttu-id="ddd1d-132">Literál dokumentu XML je identifikován deklarací XML na začátku literálu.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="ddd1d-133">I když každý literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet instrukcí pro zpracování XML a komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="ddd1d-134">Literál dokumentu XML nemůže být použit v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddd1d-135">Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="ddd1d-136">To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="ddd1d-137">Kompilátor Visual Basic převádí literál dokumentu XML na volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorů a.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd1d-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddd1d-138">Example</span></span>  
 <span data-ttu-id="ddd1d-139">Následující příklad vytvoří dokument XML, který má deklaraci XML, instrukci zpracování, komentář a prvek, který obsahuje jiný element.</span><span class="sxs-lookup"><span data-stu-id="ddd1d-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="ddd1d-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddd1d-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="ddd1d-141">Literál instrukcí pro zpracování XML</span><span class="sxs-lookup"><span data-stu-id="ddd1d-141">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="ddd1d-142">Literál komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ddd1d-142">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="ddd1d-143">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="ddd1d-143">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="ddd1d-144">Literály XML</span><span class="sxs-lookup"><span data-stu-id="ddd1d-144">XML Literals</span></span>](index.md)
- [<span data-ttu-id="ddd1d-145">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddd1d-145">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ddd1d-146">Vložené výrazy v XML</span><span class="sxs-lookup"><span data-stu-id="ddd1d-146">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
