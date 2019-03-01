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
ms.openlocfilehash: 1906c9101f9a53bde13698d0ed17b7b8d0988c1d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981371"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="a81f2-102">Literál instrukcí pro zpracování XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a81f2-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="a81f2-103">Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objektu.</span><span class="sxs-lookup"><span data-stu-id="a81f2-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a81f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a81f2-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="a81f2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a81f2-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="a81f2-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a81f2-106">Required.</span></span> <span data-ttu-id="a81f2-107">Označuje začátek instrukce zpracování XML literál.</span><span class="sxs-lookup"><span data-stu-id="a81f2-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="a81f2-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a81f2-108">Required.</span></span> <span data-ttu-id="a81f2-109">Jméno označující aplikaci, pro kterou zpracování instrukcí cíle.</span><span class="sxs-lookup"><span data-stu-id="a81f2-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="a81f2-110">Nesmí začínat znakem "xml" nebo "XML".</span><span class="sxs-lookup"><span data-stu-id="a81f2-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="a81f2-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a81f2-111">Optional.</span></span> <span data-ttu-id="a81f2-112">Řetězec určující, jak aplikace cílem `piName` by měl zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a81f2-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="a81f2-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="a81f2-113">Required.</span></span> <span data-ttu-id="a81f2-114">Označuje konec instrukce ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="a81f2-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a81f2-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a81f2-115">Return Value</span></span>  
 <span data-ttu-id="a81f2-116"><xref:System.Xml.Linq.XProcessingInstruction> Objektu.</span><span class="sxs-lookup"><span data-stu-id="a81f2-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a81f2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a81f2-117">Remarks</span></span>  
 <span data-ttu-id="a81f2-118">Literály instrukce zpracování XML určit, jak aplikace by měl zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a81f2-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="a81f2-119">Když aplikace načte dokument XML, aplikace může kontrolovat pokyny pro zpracování XML k určení způsobu zpracování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a81f2-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="a81f2-120">Aplikace interpretuje význam `piName` a `piData`.</span><span class="sxs-lookup"><span data-stu-id="a81f2-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="a81f2-121">Literál dokumentu XML používá syntaxe, která je podobná instrukce zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="a81f2-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="a81f2-122">Další informace najdete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="a81f2-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a81f2-123">`piName` Elementu nemůže začínat řetězce "xml" nebo "XML", protože tyto identifikátory specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="a81f2-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="a81f2-124">Můžete přiřadit proměnné literál instrukce zpracování XML nebo zahrnout do literál dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a81f2-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a81f2-125">Literál XML může zahrnovat více řádků bez nutnosti znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="a81f2-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="a81f2-126">To umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a81f2-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="a81f2-127">Kompilátor jazyka Visual Basic převede instrukce zpracování XML literál na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a81f2-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81f2-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="a81f2-128">Example</span></span>  
 <span data-ttu-id="a81f2-129">Následující příklad vytvoří zpracování instrukcí identifikující šablony stylů pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a81f2-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="a81f2-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a81f2-130">See also</span></span>
- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="a81f2-131">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="a81f2-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="a81f2-132">Literály XML</span><span class="sxs-lookup"><span data-stu-id="a81f2-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="a81f2-133">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a81f2-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
