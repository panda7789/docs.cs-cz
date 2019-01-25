---
title: 'Postupy: Přístup k podřízeným elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 92ecea2c2e6e117add37b30498f5fb34adfeac6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626651"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="70360-102">Postupy: Přístup k podřízeným elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70360-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="70360-103">Tento příklad ukazuje, jak používat podřízený – vlastnost osy pro přístup k všechny podřízené prvky XML, které mají zadaný název v elementu jazyka XML.</span><span class="sxs-lookup"><span data-stu-id="70360-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="70360-104">Konkrétně se použije <xref:System.Xml.Linq.XElement.Value%2A> vlastnost k získání hodnoty prvního prvku v kolekci, která `name` vrátí vlastnost podřízené osy.</span><span class="sxs-lookup"><span data-stu-id="70360-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="70360-105">`name` – Vlastnost podřízené osy získá všechny podřízené prvky s názvem `phone` v `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="70360-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="70360-106">Tento příklad také používá `phone` – vlastnost podřízené osy pro přístup k všechny podřízené prvky s názvem `phone` , které jsou součástí `contact` objektu.</span><span class="sxs-lookup"><span data-stu-id="70360-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70360-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="70360-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70360-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="70360-108">Compiling the Code</span></span>  
 <span data-ttu-id="70360-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="70360-109">This example requires:</span></span>  
  
-   <span data-ttu-id="70360-110">Odkaz na <xref:System.Xml.Linq> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="70360-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70360-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70360-111">See also</span></span>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="70360-112">Vlastnost osy podřízeného XML</span><span class="sxs-lookup"><span data-stu-id="70360-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="70360-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="70360-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="70360-114">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70360-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="70360-115">XML</span><span class="sxs-lookup"><span data-stu-id="70360-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
