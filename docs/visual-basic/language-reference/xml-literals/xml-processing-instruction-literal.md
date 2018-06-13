---
title: Literál instrukcí pro zpracování XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: e6d4c200822f58c7dbe5bf423282740d4aa86ac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604130"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="bb4d6-102">Literál instrukcí pro zpracování XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb4d6-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="bb4d6-103">Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objektu.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb4d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb4d6-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="bb4d6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bb4d6-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="bb4d6-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-106">Required.</span></span> <span data-ttu-id="bb4d6-107">Označuje začátek XML literál instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="bb4d6-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-108">Required.</span></span> <span data-ttu-id="bb4d6-109">Název označující, která aplikace cíle instrukcí pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="bb4d6-110">Nemůže začínat řetězcem "xml" nebo "XML".</span><span class="sxs-lookup"><span data-stu-id="bb4d6-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="bb4d6-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-111">Optional.</span></span> <span data-ttu-id="bb4d6-112">Řetězec určující, jak aplikaci cílem `piName` by měl zpracovat v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="bb4d6-113">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-113">Required.</span></span> <span data-ttu-id="bb4d6-114">Označuje konec pokyny pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb4d6-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb4d6-115">Return Value</span></span>  
 <span data-ttu-id="bb4d6-116"><xref:System.Xml.Linq.XProcessingInstruction> Objektu.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb4d6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb4d6-117">Remarks</span></span>  
 <span data-ttu-id="bb4d6-118">XML – literály instrukce zpracování označuje, jak by měla aplikace zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="bb4d6-119">Pokud aplikace načte dokument XML, aplikace můžete zkontrolovat pokyny pro zpracování XML určit, jak zpracovat dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="bb4d6-120">Aplikace interpretuje význam `piName` a `piData`.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="bb4d6-121">Literál dokumentu XML používá syntaxi, která je podobná pokyny pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="bb4d6-122">Další informace najdete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="bb4d6-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb4d6-123">`piName` Element nemůže začínat číslem řetězce "xml" nebo "XML", protože specifikace XML 1.0 si vyhrazuje tyto identifikátory.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="bb4d6-124">Můžete přiřadit XML literál instrukcí pro zpracování proměnné nebo její zahrnutí do literál dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb4d6-125">Literál XML může zahrnovat více řádků bez nutnosti znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="bb4d6-126">To umožňuje kopírovat obsah z dokumentu XML a vložte jej přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="bb4d6-127">Visual Basic – kompilátor převede XML literál instrukcí pro zpracování volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb4d6-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb4d6-128">Example</span></span>  
 <span data-ttu-id="bb4d6-129">Následující příklad vytvoří instrukce pro zpracování identifikace šablonu stylů pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bb4d6-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb4d6-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="bb4d6-131">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="bb4d6-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="bb4d6-132">Literály XML</span><span class="sxs-lookup"><span data-stu-id="bb4d6-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="bb4d6-133">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb4d6-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
