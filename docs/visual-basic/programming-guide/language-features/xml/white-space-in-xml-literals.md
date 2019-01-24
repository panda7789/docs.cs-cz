---
title: Prázdné znaky v literálech XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56466856bc70f4bde428f7087efdf4e71a50021f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689143"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="4ce52-102">Prázdné znaky v literálech XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ce52-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="4ce52-103">Kompilátor jazyka Visual Basic zahrnuje pouze znaky významných mezer literál XML při vytváření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="4ce52-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="4ce52-104">Neplatné prázdné znaky nejsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="4ce52-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="4ce52-105">Prázdné místo důležité a nevýznamné</span><span class="sxs-lookup"><span data-stu-id="4ce52-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="4ce52-106">Prázdné znaky v literálech XML jsou významné v pouze tři oblasti:</span><span class="sxs-lookup"><span data-stu-id="4ce52-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="4ce52-107">Když jsou v hodnotě atributu.</span><span class="sxs-lookup"><span data-stu-id="4ce52-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="4ce52-108">Když jsou součástí obsahu prvku textu a text také obsahuje jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="4ce52-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="4ce52-109">Když jsou v vložený výraz pro textový obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="4ce52-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="4ce52-110">V opačném případě kompilátor považuje za prázdné znaky neplatné a potom nezahrnuje v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekt pro literál.</span><span class="sxs-lookup"><span data-stu-id="4ce52-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="4ce52-111">Zahrnout nevýznamné prázdný znak literálu XML, použijte vložený výraz, který obsahuje řetězcový literál s prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="4ce52-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ce52-112">Pokud `xml:space` atributu se zobrazí v elementu XML literál, kompilátor jazyka Visual Basic obsahuje atribut v <xref:System.Xml.Linq.XElement> objektu, ale přidat tento atribut nedojde ke změně způsobu, jakým kompilátor zpracovává prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="4ce52-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4ce52-113">Příklady</span><span class="sxs-lookup"><span data-stu-id="4ce52-113">Examples</span></span>  
 <span data-ttu-id="4ce52-114">Následující příklad obsahuje dva elementy XML, vnitřní a vnější.</span><span class="sxs-lookup"><span data-stu-id="4ce52-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="4ce52-115">Oba prvky obsahovat prázdné znaky ve svém textového obsahu.</span><span class="sxs-lookup"><span data-stu-id="4ce52-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="4ce52-116">Prázdné znaky na vnější element je neplatné, protože obsahuje pouze prázdné znaky a platný element XML.</span><span class="sxs-lookup"><span data-stu-id="4ce52-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="4ce52-117">Prázdný znak ve vnitřní element je důležité, protože obsahuje prázdné znaky a text.</span><span class="sxs-lookup"><span data-stu-id="4ce52-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="4ce52-118">Při spuštění, tento kód zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="4ce52-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ce52-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ce52-119">See also</span></span>
- [<span data-ttu-id="4ce52-120">Vytvoření XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ce52-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
