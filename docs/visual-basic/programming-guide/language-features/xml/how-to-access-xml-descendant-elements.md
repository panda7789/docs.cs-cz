---
title: 'Postupy: Přístup k Následnickým elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: bfbf849bd296f639f03580346e4a9c52ce000abd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832213"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="2272b-102">Postupy: Přístup k Následnickým elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2272b-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="2272b-103">Tento příklad ukazuje, jak používat vlastnost Následnické osy pro přístup k všech elementů XML, které jsou obsaženy v rámci elementu XML, které mají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="2272b-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="2272b-104">Konkrétně se použije `Value` vlastnost k získání hodnoty prvního prvku v kolekci, která `name` vrátí vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="2272b-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="2272b-105">`name` Vlastnost Následnické osy získá všechny prvky s názvem `name` , které jsou součástí `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="2272b-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="2272b-106">Tento příklad také používá `phone` vlastnost Následnické osy pro přístup k všech potomků s názvem `phone` , které jsou součástí `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="2272b-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2272b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="2272b-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2272b-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2272b-108">Compiling the Code</span></span>  
 <span data-ttu-id="2272b-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2272b-109">This example requires:</span></span>  
  
-   <span data-ttu-id="2272b-110">Odkaz na <xref:System.Xml.Linq> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2272b-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2272b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2272b-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2272b-112">Vlastnost osy nástupce XML</span><span class="sxs-lookup"><span data-stu-id="2272b-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="2272b-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="2272b-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="2272b-114">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2272b-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="2272b-115">XML</span><span class="sxs-lookup"><span data-stu-id="2272b-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
