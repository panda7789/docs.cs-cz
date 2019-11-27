---
title: Prázdné znaky v literálech XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335998"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="782fb-102">Prázdné znaky v literálech XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="782fb-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="782fb-103">Kompilátor Visual Basic při vytváření objektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] v podnikové síti obsahuje pouze významné znaky mezer z literálu XML.</span><span class="sxs-lookup"><span data-stu-id="782fb-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="782fb-104">Nevýznamné prázdné znaky nejsou začleněny.</span><span class="sxs-lookup"><span data-stu-id="782fb-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="782fb-105">Významné a nevýznamné prázdné znaky</span><span class="sxs-lookup"><span data-stu-id="782fb-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="782fb-106">Prázdné znaky v literálech XML jsou významné pouze v třech oblastech:</span><span class="sxs-lookup"><span data-stu-id="782fb-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="782fb-107">Pokud jsou v hodnotě atributu.</span><span class="sxs-lookup"><span data-stu-id="782fb-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="782fb-108">Pokud jsou součástí textového obsahu elementu a text obsahuje také jiné znaky.</span><span class="sxs-lookup"><span data-stu-id="782fb-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="782fb-109">Když jsou ve vloženém výrazu pro textový obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="782fb-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="782fb-110">V opačném případě kompilátor zpracovává prázdné znaky jako nevýznamný a nezahrnuje potom do objektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pro literál.</span><span class="sxs-lookup"><span data-stu-id="782fb-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="782fb-111">Chcete-li zahrnout do literálu XML nevýznamné prázdné znaky, použijte vložený výraz, který obsahuje řetězcový literál s prázdným znakem.</span><span class="sxs-lookup"><span data-stu-id="782fb-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="782fb-112">Pokud se atribut `xml:space` nachází v literálu elementu XML, kompilátor Visual Basic obsahuje atribut v objektu <xref:System.Xml.Linq.XElement>, ale přidání tohoto atributu nemění způsob, jakým kompilátor zpracovává prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="782fb-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="782fb-113">Příklady</span><span class="sxs-lookup"><span data-stu-id="782fb-113">Examples</span></span>  
 <span data-ttu-id="782fb-114">Následující příklad obsahuje dva elementy XML, vnější a vnitřní.</span><span class="sxs-lookup"><span data-stu-id="782fb-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="782fb-115">Oba elementy obsahují prázdné znaky v textovém obsahu.</span><span class="sxs-lookup"><span data-stu-id="782fb-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="782fb-116">Prázdné znaky vnějšího prvku jsou nevýznamné, protože obsahují pouze prázdné znaky a XML element.</span><span class="sxs-lookup"><span data-stu-id="782fb-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="782fb-117">Prázdné znaky v vnitřním prvku jsou významné, protože obsahují prázdné znaky a text.</span><span class="sxs-lookup"><span data-stu-id="782fb-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="782fb-118">Při spuštění tento kód zobrazí následující text.</span><span class="sxs-lookup"><span data-stu-id="782fb-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="782fb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="782fb-119">See also</span></span>

- [<span data-ttu-id="782fb-120">Vytváření XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="782fb-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
