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
ms.openlocfilehash: cb9ad1d687203dff497e4cd451933a8bbbdf4bf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491230"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="0f32e-102">Literál instrukcí pro zpracování XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f32e-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="0f32e-103">Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objektu.</span><span class="sxs-lookup"><span data-stu-id="0f32e-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f32e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f32e-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="0f32e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0f32e-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="0f32e-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0f32e-106">Required.</span></span> <span data-ttu-id="0f32e-107">Označuje začátek instrukce zpracování XML literál.</span><span class="sxs-lookup"><span data-stu-id="0f32e-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="0f32e-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0f32e-108">Required.</span></span> <span data-ttu-id="0f32e-109">Jméno označující aplikaci, pro kterou zpracování instrukcí cíle.</span><span class="sxs-lookup"><span data-stu-id="0f32e-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="0f32e-110">Nesmí začínat znakem "xml" nebo "XML".</span><span class="sxs-lookup"><span data-stu-id="0f32e-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="0f32e-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0f32e-111">Optional.</span></span> <span data-ttu-id="0f32e-112">Řetězec určující, jak aplikace cílem `piName` by měl zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0f32e-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="0f32e-113">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0f32e-113">Required.</span></span> <span data-ttu-id="0f32e-114">Označuje konec instrukce ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="0f32e-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f32e-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0f32e-115">Return Value</span></span>  
 <span data-ttu-id="0f32e-116"><xref:System.Xml.Linq.XProcessingInstruction> Objektu.</span><span class="sxs-lookup"><span data-stu-id="0f32e-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f32e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f32e-117">Remarks</span></span>  
 <span data-ttu-id="0f32e-118">Literály instrukce zpracování XML určit, jak aplikace by měl zpracovat dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0f32e-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="0f32e-119">Když aplikace načte dokument XML, aplikace může kontrolovat pokyny pro zpracování XML k určení způsobu zpracování dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0f32e-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="0f32e-120">Aplikace interpretuje význam `piName` a `piData`.</span><span class="sxs-lookup"><span data-stu-id="0f32e-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="0f32e-121">Literál dokumentu XML používá syntaxe, která je podobná instrukce zpracování XML.</span><span class="sxs-lookup"><span data-stu-id="0f32e-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="0f32e-122">Další informace najdete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="0f32e-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f32e-123">`piName` Elementu nemůže začínat řetězce "xml" nebo "XML", protože tyto identifikátory specifikace XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="0f32e-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="0f32e-124">Můžete přiřadit proměnné literál instrukce zpracování XML nebo zahrnout do literál dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0f32e-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f32e-125">Literál XML může zahrnovat více řádků bez nutnosti znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="0f32e-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="0f32e-126">To umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f32e-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="0f32e-127">Kompilátor jazyka Visual Basic převede instrukce zpracování XML literál na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0f32e-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f32e-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f32e-128">Example</span></span>  
 <span data-ttu-id="0f32e-129">Následující příklad vytvoří zpracování instrukcí identifikující šablony stylů pro dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0f32e-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0f32e-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f32e-130">See also</span></span>
- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="0f32e-131">Literál dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="0f32e-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="0f32e-132">Literály XML</span><span class="sxs-lookup"><span data-stu-id="0f32e-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="0f32e-133">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f32e-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
