---
title: Literál XML CDATA (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8dfc091409e060e20970b0b6d6bc19b4fc2aeea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="b1105-102">Literál XML CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1105-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="b1105-103">Literál představující <xref:System.Xml.Linq.XCData> objektu.</span><span class="sxs-lookup"><span data-stu-id="b1105-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1105-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1105-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="b1105-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b1105-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="b1105-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b1105-106">Required.</span></span> <span data-ttu-id="b1105-107">Označuje začátek části XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="b1105-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="b1105-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b1105-108">Required.</span></span> <span data-ttu-id="b1105-109">Obsah textu se objeví v části XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="b1105-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="b1105-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b1105-110">Required.</span></span> <span data-ttu-id="b1105-111">Označuje konec oddílu.</span><span class="sxs-lookup"><span data-stu-id="b1105-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1105-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1105-112">Return Value</span></span>  
 <span data-ttu-id="b1105-113"><xref:System.Xml.Linq.XCData> Objektu.</span><span class="sxs-lookup"><span data-stu-id="b1105-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1105-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1105-114">Remarks</span></span>  
 <span data-ttu-id="b1105-115">XML CDATA částech nezpracovaný text, který by měl být zahrnuty, ale nebyly analyzovány s XML, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="b1105-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="b1105-116">XML CDATA oddílu může obsahovat jakýkoli text.</span><span class="sxs-lookup"><span data-stu-id="b1105-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="b1105-117">To zahrnuje vyhrazené znaky jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="b1105-117">This includes reserved XML characters.</span></span> <span data-ttu-id="b1105-118">Části XML CDATA končí sekvenci "]] >".</span><span class="sxs-lookup"><span data-stu-id="b1105-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="b1105-119">To znamená následující body:</span><span class="sxs-lookup"><span data-stu-id="b1105-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="b1105-120">Výraz vložené v literál XML CDATA nelze použít, protože oddělovače embedded výraz platný obsah XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="b1105-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="b1105-121">XML CDATA oddíly nelze vnořit, protože `content` nemůže obsahovat hodnotu "]] >".</span><span class="sxs-lookup"><span data-stu-id="b1105-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="b1105-122">Můžete přiřadit literál XML CDATA proměnné nebo její zahrnutí do literál XML elementu.</span><span class="sxs-lookup"><span data-stu-id="b1105-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1105-123">Literál XML může mít rozsah více řádků, ale nepoužívá znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="b1105-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="b1105-124">To umožňuje kopírovat obsah z dokumentu XML a vložte jej přímo do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b1105-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="b1105-125">Visual Basic – kompilátor převede literál XML CDATA volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b1105-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1105-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1105-126">Example</span></span>  
 <span data-ttu-id="b1105-127">Následující příklad vytvoří oddílu CDATA, který obsahuje text "může obsahovat literálu \<XML > značky".</span><span class="sxs-lookup"><span data-stu-id="b1105-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b1105-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1105-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="b1105-129">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="b1105-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="b1105-130">Literály XML</span><span class="sxs-lookup"><span data-stu-id="b1105-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="b1105-131">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1105-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
