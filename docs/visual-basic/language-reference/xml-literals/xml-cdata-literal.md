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
ms.openlocfilehash: b9cc830d27625f192d8f5e059bd3783d05d8ba3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400225"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="4e374-102">Literál XML CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e374-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="4e374-103">Literál představující <xref:System.Xml.Linq.XCData> objekt.</span><span class="sxs-lookup"><span data-stu-id="4e374-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e374-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e374-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="4e374-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4e374-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="4e374-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4e374-106">Required.</span></span> <span data-ttu-id="4e374-107">Označuje začátek oddílu CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="4e374-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="4e374-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4e374-108">Required.</span></span> <span data-ttu-id="4e374-109">Textový obsah, který se má zobrazit v oddílu CDATA XML</span><span class="sxs-lookup"><span data-stu-id="4e374-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="4e374-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="4e374-110">Required.</span></span> <span data-ttu-id="4e374-111">Označuje konec oddílu.</span><span class="sxs-lookup"><span data-stu-id="4e374-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e374-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4e374-112">Return Value</span></span>  
 <span data-ttu-id="4e374-113">Objekt <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="4e374-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e374-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e374-114">Remarks</span></span>  
 <span data-ttu-id="4e374-115">Oddíly XML CDATA obsahují nezpracovaný text, který by měl být zahrnut, ale ne analyzován, s XML, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="4e374-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="4e374-116">Oddíl CDATA XML může obsahovat libovolný text.</span><span class="sxs-lookup"><span data-stu-id="4e374-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="4e374-117">To zahrnuje vyhrazené znaky XML.</span><span class="sxs-lookup"><span data-stu-id="4e374-117">This includes reserved XML characters.</span></span> <span data-ttu-id="4e374-118">Oddíl CDATA XML končí sekvencí "]] >".</span><span class="sxs-lookup"><span data-stu-id="4e374-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="4e374-119">To zahrnuje následující body:</span><span class="sxs-lookup"><span data-stu-id="4e374-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="4e374-120">V literálu CDATA XML nelze použít vložený výraz, protože oddělovače vložených výrazů jsou platným obsahem CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="4e374-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="4e374-121">Oddíly XML CDATA nemůžou být vnořené, protože `content` nesmí obsahovat hodnotu "]] >".</span><span class="sxs-lookup"><span data-stu-id="4e374-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="4e374-122">Můžete přiřadit literál CDATA XML proměnné nebo jej zahrnout do literálu elementu XML.</span><span class="sxs-lookup"><span data-stu-id="4e374-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e374-123">Literál XML může zahrnovat více řádků, ale nepoužívá znaky pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="4e374-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="4e374-124">To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.</span><span class="sxs-lookup"><span data-stu-id="4e374-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="4e374-125">Kompilátor Visual Basic převádí literál XML CDATA na volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4e374-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e374-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e374-126">Example</span></span>  
 <span data-ttu-id="4e374-127">Následující příklad vytvoří oddíl CDATA obsahující text "může obsahovat literální \<XML> značky".</span><span class="sxs-lookup"><span data-stu-id="4e374-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="4e374-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e374-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="4e374-129">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="4e374-129">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="4e374-130">Literály XML</span><span class="sxs-lookup"><span data-stu-id="4e374-130">XML Literals</span></span>](index.md)
- [<span data-ttu-id="4e374-131">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e374-131">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
