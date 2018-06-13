---
title: 'Postupy: Přístup k následnickým elementům XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 6d41844b540631df96740ce56818c125cf85e928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648483"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="319ee-102">Postupy: Přístup k následnickým elementům XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="319ee-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="319ee-103">Tento příklad ukazuje, jak používat vlastnost osy nástupce pro přístup k všech elementů XML, které jsou obsažené v elementu XML, které mají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="319ee-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="319ee-104">Konkrétně používá `Value` vlastnost, která má získat hodnotu první prvek v kolekci, která `name` vrátí vlastnost Následnické osy.</span><span class="sxs-lookup"><span data-stu-id="319ee-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="319ee-105">`name` Vlastnost osy nástupce získá všechny elementy s názvem `name` , jsou součástí `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="319ee-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="319ee-106">Tento příklad také používá `phone` vlastnost osy nástupce přístup všech potomků s názvem `phone` , jsou součástí `contacts` objektu.</span><span class="sxs-lookup"><span data-stu-id="319ee-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="319ee-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="319ee-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="319ee-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="319ee-108">Compiling the Code</span></span>  
 <span data-ttu-id="319ee-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="319ee-109">This example requires:</span></span>  
  
-   <span data-ttu-id="319ee-110">Odkaz na <xref:System.Xml.Linq> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="319ee-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319ee-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="319ee-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="319ee-112">Vlastnost osy nástupce XML</span><span class="sxs-lookup"><span data-stu-id="319ee-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="319ee-113">Vlastnost hodnoty XML</span><span class="sxs-lookup"><span data-stu-id="319ee-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="319ee-114">Přístup XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="319ee-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="319ee-115">XML</span><span class="sxs-lookup"><span data-stu-id="319ee-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
