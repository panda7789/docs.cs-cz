---
title: Literál instrukcí pro zpracování XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 9bd1781e01bc4cbf1ce5da8c454ab2f5a679aead
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400173"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="9e6d6-102">Literál instrukcí pro zpracování XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e6d6-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="9e6d6-103">Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objekt.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e6d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e6d6-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="9e6d6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9e6d6-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="9e6d6-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-106">Required.</span></span> <span data-ttu-id="9e6d6-107">Označuje začátek literálu instrukcí pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="9e6d6-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-108">Required.</span></span> <span data-ttu-id="9e6d6-109">Název, který určuje, která aplikace cílí na zpracování instrukcí.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="9e6d6-110">Nelze začínat řetězcem "XML" nebo "XML".</span><span class="sxs-lookup"><span data-stu-id="9e6d6-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="9e6d6-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-111">Optional.</span></span> <span data-ttu-id="9e6d6-112">Řetězec určující, jak aplikace, na kterou cílí, `piName` by měla zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="9e6d6-113">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-113">Required.</span></span> <span data-ttu-id="9e6d6-114">Označuje konec instrukce pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e6d6-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e6d6-115">Return Value</span></span>  
 <span data-ttu-id="9e6d6-116">Objekt <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e6d6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e6d6-117">Remarks</span></span>  
 <span data-ttu-id="9e6d6-118">Literály instrukcí pro zpracování XML označují, jak by měly aplikace zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="9e6d6-119">Když aplikace načte dokument XML, aplikace může ověřit instrukce pro zpracování XML a určit, jak se má dokument zpracovat.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="9e6d6-120">Aplikace interpretuje význam `piName` a `piData` .</span><span class="sxs-lookup"><span data-stu-id="9e6d6-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="9e6d6-121">Literál dokumentu XML používá syntaxi, která je podobná jako instrukce pro zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="9e6d6-122">Další informace naleznete v tématu [literál dokumentu XML](xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9e6d6-122">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e6d6-123">`piName`Element nemůže začínat řetězcem "XML" nebo "XML", protože specifikace xml 1,0 si tyto identifikátory vyhrazuje.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="9e6d6-124">Literál instrukcí pro zpracování XML můžete přiřadit proměnné nebo ji zahrnout do literálu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e6d6-125">Literál XML může zahrnovat více řádků bez nutnosti znaků pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="9e6d6-126">To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="9e6d6-127">Kompilátor Visual Basic převádí literál instrukcí pro zpracování XML na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e6d6-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e6d6-128">Example</span></span>  
 <span data-ttu-id="9e6d6-129">Následující příklad vytvoří instrukci pro zpracování identifikující šablonu stylů dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="9e6d6-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="9e6d6-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e6d6-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="9e6d6-131">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="9e6d6-131">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="9e6d6-132">Literály XML</span><span class="sxs-lookup"><span data-stu-id="9e6d6-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="9e6d6-133">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e6d6-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
