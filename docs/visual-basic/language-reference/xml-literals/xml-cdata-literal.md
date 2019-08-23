---
title: Literál XML CDATA (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 248f3cf31f686de3af2ea06012aa4a6d4f3f29fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942921"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="7c3c8-102">Literál XML CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c3c8-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="7c3c8-103">Literál představující <xref:System.Xml.Linq.XCData> objekt.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c3c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c3c8-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="7c3c8-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7c3c8-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="7c3c8-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-106">Required.</span></span> <span data-ttu-id="7c3c8-107">Označuje začátek oddílu CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="7c3c8-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-108">Required.</span></span> <span data-ttu-id="7c3c8-109">Textový obsah, který se má zobrazit v oddílu CDATA XML</span><span class="sxs-lookup"><span data-stu-id="7c3c8-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="7c3c8-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-110">Required.</span></span> <span data-ttu-id="7c3c8-111">Označuje konec oddílu.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c3c8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7c3c8-112">Return Value</span></span>  
 <span data-ttu-id="7c3c8-113"><xref:System.Xml.Linq.XCData> Objekt.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c3c8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c3c8-114">Remarks</span></span>  
 <span data-ttu-id="7c3c8-115">Oddíly XML CDATA obsahují nezpracovaný text, který by měl být zahrnut, ale ne analyzován, s XML, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="7c3c8-116">Oddíl CDATA XML může obsahovat libovolný text.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="7c3c8-117">To zahrnuje vyhrazené znaky XML.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-117">This includes reserved XML characters.</span></span> <span data-ttu-id="7c3c8-118">Oddíl CDATA XML končí sekvencí "]] >".</span><span class="sxs-lookup"><span data-stu-id="7c3c8-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="7c3c8-119">To zahrnuje následující body:</span><span class="sxs-lookup"><span data-stu-id="7c3c8-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="7c3c8-120">V literálu CDATA XML nelze použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="7c3c8-121">Oddíly XML CDATA nemůžou být vnořené, `content` protože nesmí obsahovat hodnotu "]] >".</span><span class="sxs-lookup"><span data-stu-id="7c3c8-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="7c3c8-122">Můžete přiřadit literál CDATA XML proměnné nebo jej zahrnout do literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c3c8-123">Literál XML může zahrnovat více řádků, ale nepoužívá znaky pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="7c3c8-124">To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="7c3c8-125">Kompilátor Visual Basic převádí literál XML CDATA na volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7c3c8-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c3c8-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c3c8-126">Example</span></span>  
 <span data-ttu-id="7c3c8-127">Následující příklad vytvoří oddíl CDATA, který obsahuje text "může obsahovat literál \<XML > značek".</span><span class="sxs-lookup"><span data-stu-id="7c3c8-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="7c3c8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c3c8-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="7c3c8-129">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="7c3c8-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="7c3c8-130">Literály XML</span><span class="sxs-lookup"><span data-stu-id="7c3c8-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="7c3c8-131">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c3c8-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
