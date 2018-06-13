---
title: 'Postupy: transformace Fragment uzlu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd35e469a16dc2fdb3a7f4afd89d04f67185cd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568560"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="2d855-102">Postupy: transformace Fragment uzlu</span><span class="sxs-lookup"><span data-stu-id="2d855-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="2d855-103">Při transformaci data obsažená v <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> objektu transformace XSLT vztahují k dokumentu jako celku.</span><span class="sxs-lookup"><span data-stu-id="2d855-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="2d855-104">Jinými slovy Pokud předáte v uzlu než kořenový uzel dokumentu, toto nezabrání proces transformace přístup na všechny uzly v načíst dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2d855-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="2d855-105">K transformaci fragment uzlu, musíte vytvořit samostatný objekt obsahující pouze fragment uzlu a předat tento objekt, který chcete <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2d855-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2d855-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="2d855-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="2d855-107">K transformaci fragment uzlu</span><span class="sxs-lookup"><span data-stu-id="2d855-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="2d855-108">Vytvořte objekt, který obsahuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="2d855-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="2d855-109">Vyhledejte fragment uzlu, který si přejete transformace.</span><span class="sxs-lookup"><span data-stu-id="2d855-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="2d855-110">Vytvořte samostatný objekt s právě fragment uzlu.</span><span class="sxs-lookup"><span data-stu-id="2d855-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="2d855-111">Předat uzlu fragment k <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2d855-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d855-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d855-112">Example</span></span>  
 <span data-ttu-id="2d855-113">Následující příklad transformuje fragment uzlu a výsledky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="2d855-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="2d855-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="2d855-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="2d855-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="2d855-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="2d855-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="2d855-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="2d855-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="2d855-117">Output</span></span>  
 <span data-ttu-id="2d855-118">Název adresáře je Man spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="2d855-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d855-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d855-119">See Also</span></span>  
 [<span data-ttu-id="2d855-120">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="2d855-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
