---
title: "Literál XML CDATA (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 906fd2494dd952c08088b9b7e38dba4505780481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="47860-102">Literál XML CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47860-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="47860-103">Literál představující <xref:System.Xml.Linq.XCData> objektu.</span><span class="sxs-lookup"><span data-stu-id="47860-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47860-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47860-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="47860-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="47860-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="47860-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="47860-106">Required.</span></span> <span data-ttu-id="47860-107">Označuje začátek části XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="47860-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="47860-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="47860-108">Required.</span></span> <span data-ttu-id="47860-109">Obsah textu se objeví v části XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="47860-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="47860-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="47860-110">Required.</span></span> <span data-ttu-id="47860-111">Označuje konec oddílu.</span><span class="sxs-lookup"><span data-stu-id="47860-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47860-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47860-112">Return Value</span></span>  
 <span data-ttu-id="47860-113"><xref:System.Xml.Linq.XCData> Objektu.</span><span class="sxs-lookup"><span data-stu-id="47860-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47860-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47860-114">Remarks</span></span>  
 <span data-ttu-id="47860-115">XML CDATA částech nezpracovaný text, který by měl být zahrnuty, ale nebyly analyzovány s XML, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="47860-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="47860-116">XML CDATA oddílu může obsahovat jakýkoli text.</span><span class="sxs-lookup"><span data-stu-id="47860-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="47860-117">To zahrnuje vyhrazené znaky jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="47860-117">This includes reserved XML characters.</span></span> <span data-ttu-id="47860-118">Části XML CDATA končí sekvenci "]] >".</span><span class="sxs-lookup"><span data-stu-id="47860-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="47860-119">To znamená následující body:</span><span class="sxs-lookup"><span data-stu-id="47860-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="47860-120">Výraz vložené v literál XML CDATA nelze použít, protože oddělovače embedded výraz platný obsah XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="47860-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="47860-121">XML CDATA oddíly nelze vnořit, protože `content` nemůže obsahovat hodnotu "]] >".</span><span class="sxs-lookup"><span data-stu-id="47860-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="47860-122">Můžete přiřadit literál XML CDATA proměnné nebo její zahrnutí do literál XML elementu.</span><span class="sxs-lookup"><span data-stu-id="47860-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47860-123">Literál XML může mít rozsah více řádků, ale nepoužívá znaky pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="47860-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="47860-124">To umožňuje kopírovat obsah z dokumentu XML a vložte ji přímo do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="47860-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="47860-125">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede literál XML CDATA volání <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="47860-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47860-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="47860-126">Example</span></span>  
 <span data-ttu-id="47860-127">Následující příklad vytvoří oddílu CDATA, který obsahuje text "může obsahovat literálu \<XML > značky".</span><span class="sxs-lookup"><span data-stu-id="47860-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="47860-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="47860-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="47860-129">Literál XML elementu</span><span class="sxs-lookup"><span data-stu-id="47860-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="47860-130">XML – literály</span><span class="sxs-lookup"><span data-stu-id="47860-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="47860-131">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47860-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
