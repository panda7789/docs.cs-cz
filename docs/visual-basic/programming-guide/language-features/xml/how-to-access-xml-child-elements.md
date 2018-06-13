---
title: 'Postupy: Přístup k podřízeným elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 4ec7743a30b8101d813ac414a8f5164aeb6c593d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649201"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="f0fb8-102">Postupy: Přístup k podřízeným elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0fb8-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="f0fb8-103">Tento příklad ukazuje způsob použití podřízená osa – vlastnost přístup všech podřízených elementů XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="f0fb8-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="f0fb8-104">Konkrétně používá <xref:System.Xml.Linq.XElement.Value%2A> vlastnost, která má získat hodnotu první prvek v kolekci, která `name` vrátí vlastnost podřízené osy.</span><span class="sxs-lookup"><span data-stu-id="f0fb8-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="f0fb8-105">`name` Vlastnost osy podřízeného získá všech podřízených elementů s názvem `phone` v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="f0fb8-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="f0fb8-106">Tento příklad také používá `phone` vlastnost osy podřízeného přístup všech podřízených elementů s názvem `phone` , jsou součástí `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="f0fb8-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0fb8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0fb8-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0fb8-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f0fb8-108">Compiling the Code</span></span>  
 <span data-ttu-id="f0fb8-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f0fb8-109">This example requires:</span></span>  
  
-   <span data-ttu-id="f0fb8-110">Odkaz na <xref:System.Xml.Linq> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f0fb8-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fb8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0fb8-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f0fb8-112">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="f0fb8-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="f0fb8-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="f0fb8-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="f0fb8-114">Přístup XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0fb8-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="f0fb8-115">XML</span><span class="sxs-lookup"><span data-stu-id="f0fb8-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
