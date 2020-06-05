---
title: 'Postupy: Přístup k podřízeným elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392815"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="73de1-102">Postupy: Přístup k podřízeným elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73de1-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="73de1-103">Tento příklad ukazuje, jak použít vlastnost podřízené osy pro přístup ke všem podřízeným elementům XML, které mají zadaný název v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="73de1-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="73de1-104">Konkrétně používá <xref:System.Xml.Linq.XElement.Value%2A> vlastnost k získání hodnoty prvního prvku v kolekci, kterou `name` vrací vlastnost podřízené osy.</span><span class="sxs-lookup"><span data-stu-id="73de1-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="73de1-105">`name`Vlastnost podřízené osy získá všechny podřízené elementy s názvem `phone` v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="73de1-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="73de1-106">Tento příklad také používá `phone` vlastnost podřízené osy pro přístup ke všem podřízeným prvkům s názvem `phone` , které jsou obsaženy v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="73de1-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73de1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="73de1-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="73de1-108">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="73de1-108">Compile the code</span></span>  
 <span data-ttu-id="73de1-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="73de1-109">This example requires:</span></span>  
  
- <span data-ttu-id="73de1-110">Odkaz na <xref:System.Xml.Linq> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="73de1-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73de1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="73de1-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="73de1-112">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="73de1-112">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="73de1-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="73de1-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="73de1-114">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73de1-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="73de1-115">XML</span><span class="sxs-lookup"><span data-stu-id="73de1-115">XML</span></span>](index.md)
