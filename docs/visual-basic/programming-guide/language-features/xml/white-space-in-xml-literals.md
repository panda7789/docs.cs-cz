---
title: Prázdné znaky v literálech XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649747"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="7acc8-102">Prázdné znaky v literálech XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7acc8-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="7acc8-103">Visual Basic – kompilátor zahrnuje pouze znaky významné prázdné znaky z literál XML při vytváření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="7acc8-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="7acc8-104">Nejsou zahrnuty zanedbatelný prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="7acc8-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="7acc8-105">Významné a zanedbatelný prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="7acc8-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="7acc8-106">Prázdné znaky v literálech XML jsou důležitá pouze tří oblastí:</span><span class="sxs-lookup"><span data-stu-id="7acc8-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="7acc8-107">Pokud se hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="7acc8-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="7acc8-108">Když jsou součástí textového obsahu elementu a text také obsahuje jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="7acc8-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="7acc8-109">Když jsou v embedded výrazu pro textového obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="7acc8-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="7acc8-110">Jinak kompilátor zpracovává prázdné znaky jako zanedbatelný a pak nezahrnuje v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt pro literál.</span><span class="sxs-lookup"><span data-stu-id="7acc8-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="7acc8-111">Literál XML zahrnout zanedbatelný prázdné znaky, použijte embedded výraz, který obsahuje řetězcový literál s bílými oblasti.</span><span class="sxs-lookup"><span data-stu-id="7acc8-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7acc8-112">Pokud `xml:space` atributu se zobrazí v elementu XML literálu, Visual Basic – kompilátor obsahuje atribut v <xref:System.Xml.Linq.XElement> objektu, ale přidání tento atribut nezmění jak kompilátor zpracovává mezer.</span><span class="sxs-lookup"><span data-stu-id="7acc8-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7acc8-113">Příklady</span><span class="sxs-lookup"><span data-stu-id="7acc8-113">Examples</span></span>  
 <span data-ttu-id="7acc8-114">Následující příklad obsahuje dva elementy XML vnitřní a vnější.</span><span class="sxs-lookup"><span data-stu-id="7acc8-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="7acc8-115">Oba elementy obsahovat prázdné znaky v jejich textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="7acc8-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="7acc8-116">Prázdné znaky v prvku vnější je zanedbatelný, protože obsahuje jenom prázdné znaky a XML element.</span><span class="sxs-lookup"><span data-stu-id="7acc8-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="7acc8-117">Prázdné znaky v informacích o vnitřní element je důležité, protože obsahuje prázdné znaky a text.</span><span class="sxs-lookup"><span data-stu-id="7acc8-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="7acc8-118">Při spuštění, tento kód zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="7acc8-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7acc8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7acc8-119">See Also</span></span>  
 [<span data-ttu-id="7acc8-120">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7acc8-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
