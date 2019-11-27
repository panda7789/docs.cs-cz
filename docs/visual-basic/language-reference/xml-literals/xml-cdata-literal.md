---
title: Literál XML CDATA
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349437"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="1926e-102">Literál XML CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1926e-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="1926e-103">Literál představující objekt <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="1926e-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1926e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1926e-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="1926e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1926e-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="1926e-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1926e-106">Required.</span></span> <span data-ttu-id="1926e-107">Označuje začátek oddílu CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="1926e-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="1926e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1926e-108">Required.</span></span> <span data-ttu-id="1926e-109">Textový obsah, který se má zobrazit v oddílu CDATA XML</span><span class="sxs-lookup"><span data-stu-id="1926e-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="1926e-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1926e-110">Required.</span></span> <span data-ttu-id="1926e-111">Označuje konec oddílu.</span><span class="sxs-lookup"><span data-stu-id="1926e-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1926e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1926e-112">Return Value</span></span>  
 <span data-ttu-id="1926e-113">Objekt <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="1926e-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1926e-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1926e-114">Remarks</span></span>  
 <span data-ttu-id="1926e-115">Oddíly XML CDATA obsahují nezpracovaný text, který by měl být zahrnut, ale ne analyzován, s XML, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="1926e-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="1926e-116">Oddíl CDATA XML může obsahovat libovolný text.</span><span class="sxs-lookup"><span data-stu-id="1926e-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="1926e-117">To zahrnuje vyhrazené znaky XML.</span><span class="sxs-lookup"><span data-stu-id="1926e-117">This includes reserved XML characters.</span></span> <span data-ttu-id="1926e-118">Oddíl CDATA XML končí sekvencí "]] >".</span><span class="sxs-lookup"><span data-stu-id="1926e-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="1926e-119">To zahrnuje následující body:</span><span class="sxs-lookup"><span data-stu-id="1926e-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="1926e-120">V literálu CDATA XML nelze použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="1926e-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="1926e-121">Oddíly XML CDATA nemohou být vnořené, protože `content` nesmí obsahovat hodnotu "]] >".</span><span class="sxs-lookup"><span data-stu-id="1926e-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="1926e-122">Můžete přiřadit literál CDATA XML proměnné nebo jej zahrnout do literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="1926e-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1926e-123">Literál XML může zahrnovat více řádků, ale nepoužívá znaky pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="1926e-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="1926e-124">To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="1926e-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="1926e-125">Kompilátor Visual Basic převádí literál XML CDATA na volání konstruktoru <xref:System.Xml.Linq.XCData.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="1926e-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1926e-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="1926e-126">Example</span></span>  
 <span data-ttu-id="1926e-127">Následující příklad vytvoří oddíl CDATA, který obsahuje text "může obsahovat literál \<> značky XML.</span><span class="sxs-lookup"><span data-stu-id="1926e-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="1926e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1926e-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="1926e-129">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="1926e-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="1926e-130">Literály XML</span><span class="sxs-lookup"><span data-stu-id="1926e-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="1926e-131">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1926e-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
