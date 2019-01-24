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
ms.openlocfilehash: 71769c023ba77d40099ba0ba29ef363091e96831
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521553"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="7a098-102">Literál XML CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a098-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="7a098-103">Literál představující <xref:System.Xml.Linq.XCData> objektu.</span><span class="sxs-lookup"><span data-stu-id="7a098-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a098-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a098-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="7a098-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7a098-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="7a098-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7a098-106">Required.</span></span> <span data-ttu-id="7a098-107">Označuje začátek oddílu CDATA kódu XML.</span><span class="sxs-lookup"><span data-stu-id="7a098-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="7a098-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7a098-108">Required.</span></span> <span data-ttu-id="7a098-109">Textový obsah se zobrazí v oddílu CDATA kódu XML.</span><span class="sxs-lookup"><span data-stu-id="7a098-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="7a098-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7a098-110">Required.</span></span> <span data-ttu-id="7a098-111">Označuje konec oddílu.</span><span class="sxs-lookup"><span data-stu-id="7a098-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a098-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7a098-112">Return Value</span></span>  
 <span data-ttu-id="7a098-113"><xref:System.Xml.Linq.XCData> Objektu.</span><span class="sxs-lookup"><span data-stu-id="7a098-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a098-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a098-114">Remarks</span></span>  
 <span data-ttu-id="7a098-115">XML CDATA oddíly obsahují nezpracovaný text, který by měl zahrnuty, ale nebyly analyzovány pomocí XML, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="7a098-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="7a098-116">Oddíl CDATA kódu XML může obsahovat libovolný text.</span><span class="sxs-lookup"><span data-stu-id="7a098-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="7a098-117">To zahrnuje vyhrazené znaky jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="7a098-117">This includes reserved XML characters.</span></span> <span data-ttu-id="7a098-118">Sekce XML CDATA končí sekvence "]] >".</span><span class="sxs-lookup"><span data-stu-id="7a098-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="7a098-119">Z toho vyplývá následující body:</span><span class="sxs-lookup"><span data-stu-id="7a098-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="7a098-120">V XML CDATA, který je literál nejde použít vložený výraz, protože vložený výraz oddělovače jsou platný obsah XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="7a098-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="7a098-121">XML CDATA oddíly nelze vnořit, protože `content` nemůže obsahovat hodnotu "]] >".</span><span class="sxs-lookup"><span data-stu-id="7a098-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="7a098-122">Můžete přiřadit literál XML CDATA proměnné nebo zahrnout do literálů XML element.</span><span class="sxs-lookup"><span data-stu-id="7a098-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a098-123">Literál XML může zahrnovat více řádků, ale nepoužívá znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="7a098-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="7a098-124">To umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a098-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="7a098-125">Kompilátor jazyka Visual Basic převede literál XML CDATA na volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7a098-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a098-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a098-126">Example</span></span>  
 <span data-ttu-id="7a098-127">Následující příklad vytvoří oddíl CDATA, který obsahuje text "může obsahovat literál \<XML > značky".</span><span class="sxs-lookup"><span data-stu-id="7a098-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7a098-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a098-128">See also</span></span>
- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="7a098-129">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="7a098-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="7a098-130">Literály XML</span><span class="sxs-lookup"><span data-stu-id="7a098-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="7a098-131">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a098-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
