---
title: 'Postupy: Přístup k následnickým elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347159"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="c69f4-102">Postupy: Přístup k následnickým elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c69f4-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="c69f4-103">Tento příklad ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="c69f4-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="c69f4-104">Konkrétně používá vlastnost `Value` k získání hodnoty prvního prvku v kolekci, kterou vrací vlastnost osy `name` následníka.</span><span class="sxs-lookup"><span data-stu-id="c69f4-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="c69f4-105">Vlastnost osy `name` následníka získá všechny prvky pojmenované `name`, které jsou obsaženy v objektu `contacts`.</span><span class="sxs-lookup"><span data-stu-id="c69f4-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="c69f4-106">Tento příklad také používá vlastnost `phone` následníka pro přístup ke všem následníkům s názvem `phone`, které jsou obsaženy v objektu `contacts`.</span><span class="sxs-lookup"><span data-stu-id="c69f4-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c69f4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c69f4-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="c69f4-108">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c69f4-108">Compile the code</span></span>  
 <span data-ttu-id="c69f4-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c69f4-109">This example requires:</span></span>  
  
- <span data-ttu-id="c69f4-110">Odkaz na obor názvů <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="c69f4-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69f4-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c69f4-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c69f4-112">Vlastnost osy nástupce XML</span><span class="sxs-lookup"><span data-stu-id="c69f4-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="c69f4-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="c69f4-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="c69f4-114">Přístup k XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c69f4-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="c69f4-115">XML</span><span class="sxs-lookup"><span data-stu-id="c69f4-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
