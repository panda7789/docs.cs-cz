---
title: 'Postupy: Přístup k následnickým elementům XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 63a094c3c2b20736f0ef6589c76d53b7cc96b29a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332317"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="80376-102">Postupy: Přístup k následnickým elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80376-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="80376-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span><span class="sxs-lookup"><span data-stu-id="80376-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="80376-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span><span class="sxs-lookup"><span data-stu-id="80376-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="80376-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span><span class="sxs-lookup"><span data-stu-id="80376-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="80376-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span><span class="sxs-lookup"><span data-stu-id="80376-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80376-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="80376-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80376-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="80376-108">Compiling the Code</span></span>  
 <span data-ttu-id="80376-109">This example requires:</span><span class="sxs-lookup"><span data-stu-id="80376-109">This example requires:</span></span>  
  
- <span data-ttu-id="80376-110">A reference to the <xref:System.Xml.Linq> namespace.</span><span class="sxs-lookup"><span data-stu-id="80376-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80376-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80376-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="80376-112">Vlastnost osy nástupce XML</span><span class="sxs-lookup"><span data-stu-id="80376-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="80376-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="80376-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="80376-114">Accessing XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80376-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="80376-115">XML</span><span class="sxs-lookup"><span data-stu-id="80376-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
