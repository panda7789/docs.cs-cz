---
title: 'Postupy: Přístup k podřízeným elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: af5ea809cb0777b16230f20e133764dd5f1f86d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332344"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="e8b1a-102">Postupy: Přístup k podřízeným elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8b1a-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="e8b1a-103">Tento příklad ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="e8b1a-104">Konkrétně používá vlastnost <xref:System.Xml.Linq.XElement.Value%2A> k získání hodnoty prvního prvku v kolekci, kterou vrací vlastnost `name` podřízená osa.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="e8b1a-105">Vlastnost `name` podřízená osa získá všechny podřízené elementy s názvem `phone` v objektu `contact`.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="e8b1a-106">Tento příklad také používá vlastnost `phone` podřízená osa pro přístup ke všem podřízeným prvkům s názvem `phone`, které jsou obsaženy v objektu `contact`.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b1a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8b1a-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8b1a-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e8b1a-108">Compiling the Code</span></span>  
 <span data-ttu-id="e8b1a-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e8b1a-109">This example requires:</span></span>  
  
- <span data-ttu-id="e8b1a-110">Odkaz na obor názvů <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b1a-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8b1a-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e8b1a-112">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="e8b1a-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="e8b1a-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="e8b1a-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="e8b1a-114">Přístup k XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8b1a-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="e8b1a-115">XML</span><span class="sxs-lookup"><span data-stu-id="e8b1a-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
