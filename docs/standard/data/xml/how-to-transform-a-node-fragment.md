---
title: 'Postupy: transformace fragmentu uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb258b61664e1fdbf6604afdf69074c48cf5bda4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273814"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="b5d55-102">Postupy: transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="b5d55-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="b5d55-103">Při transformaci dat obsažených v <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> objektu transformace XSLT se vztahují k dokumentu jako celek.</span><span class="sxs-lookup"><span data-stu-id="b5d55-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="b5d55-104">Jinými slovy Pokud předáte v uzlu, než je kořenový uzel dokumentu, toto nezabraňuje proces transformace přístup na všechny uzly v načtený dokument.</span><span class="sxs-lookup"><span data-stu-id="b5d55-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="b5d55-105">Transformace fragmentu uzlu, musíte vytvořit samostatný objekt obsahující pouze fragmentu uzlu a předejte tento objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b5d55-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="b5d55-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5d55-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="b5d55-107">Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="b5d55-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="b5d55-108">Vytvořte objekt, který obsahuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="b5d55-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="b5d55-109">Vyhledání fragmentu uzlu, který chcete transformovat.</span><span class="sxs-lookup"><span data-stu-id="b5d55-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="b5d55-110">Vytvořte samostatný objekt s právě fragmentu uzlu.</span><span class="sxs-lookup"><span data-stu-id="b5d55-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="b5d55-111">Předejte fragmentu uzlu na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b5d55-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5d55-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5d55-112">Example</span></span>  
 <span data-ttu-id="b5d55-113">V následujícím příkladu transformace fragmentu uzlu a vypíše výsledky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b5d55-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="b5d55-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="b5d55-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="b5d55-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="b5d55-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="b5d55-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="b5d55-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="b5d55-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="b5d55-117">Output</span></span>  
 <span data-ttu-id="b5d55-118">Název knihy se požadavek spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="b5d55-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d55-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5d55-119">See also</span></span>

- [<span data-ttu-id="b5d55-120">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b5d55-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
