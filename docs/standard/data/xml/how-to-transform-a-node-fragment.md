---
title: 'Postupy: Transformace fragmentu uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 56e9ef6031a5736acfa066ed6c068f954bd5af8d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710814"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="e0576-102">Postupy: Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="e0576-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="e0576-103">Při transformaci dat obsažených v objektu <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> se transformace XSLT vztahují na dokument jako celek.</span><span class="sxs-lookup"><span data-stu-id="e0576-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="e0576-104">Jinými slovy, Pokud předáte v jiném než kořenovém uzlu dokumentu, nezabrání to procesu transformace v přístupu ke všem uzlům v načteném dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e0576-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="e0576-105">Chcete-li transformovat fragment uzlu, je nutné vytvořit samostatný objekt obsahující pouze fragment uzlu a předat tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="e0576-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e0576-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="e0576-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="e0576-107">Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="e0576-107">To transform a node fragment</span></span>  
  
1. <span data-ttu-id="e0576-108">Vytvořte objekt obsahující zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="e0576-108">Create an object containing the source document.</span></span>  
  
2. <span data-ttu-id="e0576-109">Najděte fragment uzlu, který chcete transformovat.</span><span class="sxs-lookup"><span data-stu-id="e0576-109">Locate the node fragment you wish to transform.</span></span>  
  
3. <span data-ttu-id="e0576-110">Vytvořte samostatný objekt se pouze fragmentem uzlu.</span><span class="sxs-lookup"><span data-stu-id="e0576-110">Create separate object with just the node fragment.</span></span>  
  
4. <span data-ttu-id="e0576-111">Předejte fragment uzlu do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e0576-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0576-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0576-112">Example</span></span>  
 <span data-ttu-id="e0576-113">Následující příklad transformuje fragment uzlu a výstupy výsledků do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e0576-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="e0576-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="e0576-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="e0576-115">Books. XML</span><span class="sxs-lookup"><span data-stu-id="e0576-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="e0576-116">Single. xsl</span><span class="sxs-lookup"><span data-stu-id="e0576-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="e0576-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="e0576-117">Output</span></span>  
 <span data-ttu-id="e0576-118">Titul knihy je důvěryhodný člověk.</span><span class="sxs-lookup"><span data-stu-id="e0576-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0576-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0576-119">See also</span></span>

- [<span data-ttu-id="e0576-120">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="e0576-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
