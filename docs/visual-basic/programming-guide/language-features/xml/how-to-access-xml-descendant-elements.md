---
title: 'Postupy: Přístup k následnickým elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 03c403aa3c187b0b9d2006104eccaa1f9cd8aec5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392633"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="268e8-102">Postupy: Přístup k následnickým elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="268e8-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="268e8-103">Tento příklad ukazuje, jak použít vlastnost následníka pro přístup ke všem elementům XML, které mají zadaný název a které jsou obsaženy v elementu XML.</span><span class="sxs-lookup"><span data-stu-id="268e8-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="268e8-104">Konkrétně používá `Value` vlastnost k získání hodnoty prvního prvku v kolekci, kterou `name` vrací vlastnost osy následníka.</span><span class="sxs-lookup"><span data-stu-id="268e8-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="268e8-105">`name`Vlastnost osy následníka získá všechny prvky s názvem `name` , které jsou obsaženy v `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="268e8-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="268e8-106">Tento příklad také používá `phone` vlastnost následníka pro přístup ke všem následníkům s názvem `phone` , které jsou obsaženy v `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="268e8-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268e8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="268e8-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="268e8-108">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="268e8-108">Compile the code</span></span>  
 <span data-ttu-id="268e8-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="268e8-109">This example requires:</span></span>  
  
- <span data-ttu-id="268e8-110">Odkaz na <xref:System.Xml.Linq> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="268e8-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268e8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="268e8-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="268e8-112">Vlastnost osy nástupce XML</span><span class="sxs-lookup"><span data-stu-id="268e8-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="268e8-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="268e8-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="268e8-114">Přístup ke XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="268e8-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="268e8-115">XML</span><span class="sxs-lookup"><span data-stu-id="268e8-115">XML</span></span>](index.md)
