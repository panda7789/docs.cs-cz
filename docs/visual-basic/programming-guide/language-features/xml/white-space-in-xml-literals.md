---
title: "Prázdné znaky v literálech XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8587abb98fe33ab2c5a0cef6cea76049a00909e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="a4626-102">Prázdné znaky v literálech XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4626-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="a4626-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru zahrnuje pouze znaky významné prázdné znaky z literál XML při vytváření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="a4626-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="a4626-104">Nejsou zahrnuty zanedbatelný prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="a4626-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="a4626-105">Významné a zanedbatelný prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="a4626-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="a4626-106">Prázdné znaky v literálech XML jsou důležitá pouze tří oblastí:</span><span class="sxs-lookup"><span data-stu-id="a4626-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="a4626-107">Pokud se hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="a4626-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="a4626-108">Když jsou součástí textového obsahu elementu a text také obsahuje jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="a4626-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="a4626-109">Když jsou v embedded výrazu pro textového obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="a4626-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="a4626-110">Jinak kompilátor zpracovává prázdné znaky jako zanedbatelný a pak nezahrnuje v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt pro literál.</span><span class="sxs-lookup"><span data-stu-id="a4626-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="a4626-111">Literál XML zahrnout zanedbatelný prázdné znaky, použijte embedded výraz, který obsahuje řetězcový literál s bílými oblasti.</span><span class="sxs-lookup"><span data-stu-id="a4626-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4626-112">Pokud `xml:space` atributu se zobrazí v elementu XML literálu, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru obsahuje atribut v <xref:System.Xml.Linq.XElement> objektu, ale přidání tento atribut nezmění jak kompilátor zpracovává mezer.</span><span class="sxs-lookup"><span data-stu-id="a4626-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a4626-113">Příklady</span><span class="sxs-lookup"><span data-stu-id="a4626-113">Examples</span></span>  
 <span data-ttu-id="a4626-114">Následující příklad obsahuje dva elementy XML vnitřní a vnější.</span><span class="sxs-lookup"><span data-stu-id="a4626-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="a4626-115">Oba elementy obsahovat prázdné znaky v jejich textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="a4626-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="a4626-116">Prázdné znaky v prvku vnější je zanedbatelný, protože obsahuje jenom prázdné znaky a XML element.</span><span class="sxs-lookup"><span data-stu-id="a4626-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="a4626-117">Prázdné znaky v informacích o vnitřní element je důležité, protože obsahuje prázdné znaky a text.</span><span class="sxs-lookup"><span data-stu-id="a4626-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="a4626-118">Při spuštění, tento kód zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="a4626-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4626-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4626-119">See Also</span></span>  
 [<span data-ttu-id="a4626-120">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4626-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
