---
title: 'Postupy: Transformace fragmentu uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabf7983a1887fb318bfb8d111b3911f4d90c545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345167"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="dfeb5-102">Postupy: Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="dfeb5-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="dfeb5-103">Při transformaci dat obsažených v <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> objektu transformace XSLT se vztahují k dokumentu jako celek.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="dfeb5-104">Jinými slovy Pokud předáte v uzlu, než je kořenový uzel dokumentu, toto nezabraňuje proces transformace přístup na všechny uzly v načtený dokument.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="dfeb5-105">Transformace fragmentu uzlu, musíte vytvořit samostatný objekt obsahující pouze fragmentu uzlu a předejte tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="dfeb5-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="dfeb5-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="dfeb5-107">Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="dfeb5-107">To transform a node fragment</span></span>  
  
1. <span data-ttu-id="dfeb5-108">Vytvořte objekt, který obsahuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-108">Create an object containing the source document.</span></span>  
  
2. <span data-ttu-id="dfeb5-109">Vyhledání fragmentu uzlu, který chcete transformovat.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-109">Locate the node fragment you wish to transform.</span></span>  
  
3. <span data-ttu-id="dfeb5-110">Vytvořte samostatný objekt s právě fragmentu uzlu.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-110">Create separate object with just the node fragment.</span></span>  
  
4. <span data-ttu-id="dfeb5-111">Předejte fragmentu uzlu na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfeb5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfeb5-112">Example</span></span>  
 <span data-ttu-id="dfeb5-113">V následujícím příkladu transformace fragmentu uzlu a vypíše výsledky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="dfeb5-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="dfeb5-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="dfeb5-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="dfeb5-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="dfeb5-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="dfeb5-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="dfeb5-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="dfeb5-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="dfeb5-117">Output</span></span>  
 <span data-ttu-id="dfeb5-118">Název knihy se požadavek spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="dfeb5-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfeb5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfeb5-119">See also</span></span>

- [<span data-ttu-id="dfeb5-120">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="dfeb5-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
