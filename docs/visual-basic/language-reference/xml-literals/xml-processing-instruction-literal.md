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
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958484"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="efb2d-102">Literál instrukcí pro zpracování XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efb2d-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="efb2d-103">Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objekt.</span><span class="sxs-lookup"><span data-stu-id="efb2d-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efb2d-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="efb2d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="efb2d-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="efb2d-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="efb2d-106">Required.</span></span> <span data-ttu-id="efb2d-107">Označuje začátek literálu instrukcí pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="efb2d-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="efb2d-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="efb2d-108">Required.</span></span> <span data-ttu-id="efb2d-109">Název, který určuje, která aplikace cílí na zpracování instrukcí.</span><span class="sxs-lookup"><span data-stu-id="efb2d-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="efb2d-110">Nelze začínat řetězcem "XML" nebo "XML".</span><span class="sxs-lookup"><span data-stu-id="efb2d-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="efb2d-111">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="efb2d-111">Optional.</span></span> <span data-ttu-id="efb2d-112">Řetězec určující, jak aplikace, na `piName` kterou cílí, by měla zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="efb2d-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="efb2d-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="efb2d-113">Required.</span></span> <span data-ttu-id="efb2d-114">Označuje konec instrukce pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="efb2d-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efb2d-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="efb2d-115">Return Value</span></span>  
 <span data-ttu-id="efb2d-116"><xref:System.Xml.Linq.XProcessingInstruction> Objekt.</span><span class="sxs-lookup"><span data-stu-id="efb2d-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efb2d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efb2d-117">Remarks</span></span>  
 <span data-ttu-id="efb2d-118">Literály instrukcí pro zpracování XML označují, jak by měly aplikace zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="efb2d-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="efb2d-119">Když aplikace načte dokument XML, aplikace může ověřit instrukce pro zpracování XML a určit, jak se má dokument zpracovat.</span><span class="sxs-lookup"><span data-stu-id="efb2d-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="efb2d-120">Aplikace interpretuje význam `piName` a `piData`.</span><span class="sxs-lookup"><span data-stu-id="efb2d-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="efb2d-121">Literál dokumentu XML používá syntaxi, která je podobná jako instrukce pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="efb2d-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="efb2d-122">Další informace naleznete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="efb2d-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efb2d-123">`piName` Element nemůže začínat řetězcem "XML" nebo "XML", protože specifikace XML 1,0 si tyto identifikátory vyhrazuje.</span><span class="sxs-lookup"><span data-stu-id="efb2d-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="efb2d-124">Literál instrukcí pro zpracování XML můžete přiřadit proměnné nebo ji zahrnout do literálu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="efb2d-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efb2d-125">Literál XML může zahrnovat více řádků bez nutnosti znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="efb2d-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="efb2d-126">To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="efb2d-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="efb2d-127">Kompilátor Visual Basic převádí literál instrukcí pro zpracování XML na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="efb2d-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efb2d-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="efb2d-128">Example</span></span>  
 <span data-ttu-id="efb2d-129">Následující příklad vytvoří instrukci pro zpracování identifikující šablonu stylů dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="efb2d-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="efb2d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efb2d-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="efb2d-131">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="efb2d-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="efb2d-132">Literály XML</span><span class="sxs-lookup"><span data-stu-id="efb2d-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="efb2d-133">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efb2d-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
