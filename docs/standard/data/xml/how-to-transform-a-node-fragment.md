---
title: 'Postupy: transformace Fragment uzlu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b85bcbf537f5306b0b4c30630523eaf511dd3d9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="91171-102">Postupy: transformace Fragment uzlu</span><span class="sxs-lookup"><span data-stu-id="91171-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="91171-103">Při transformaci data obsažená v <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> objektu transformace XSLT vztahují k dokumentu jako celku.</span><span class="sxs-lookup"><span data-stu-id="91171-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="91171-104">Jinými slovy Pokud předáte v uzlu než kořenový uzel dokumentu, toto nezabrání proces transformace přístup na všechny uzly v načíst dokumentu.</span><span class="sxs-lookup"><span data-stu-id="91171-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="91171-105">K transformaci fragment uzlu, musíte vytvořit samostatný objekt obsahující pouze fragment uzlu a předat tento objekt, který chcete <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="91171-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="91171-106">Procedury</span><span class="sxs-lookup"><span data-stu-id="91171-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="91171-107">K transformaci fragment uzlu</span><span class="sxs-lookup"><span data-stu-id="91171-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="91171-108">Vytvořte objekt, který obsahuje zdrojový dokument.</span><span class="sxs-lookup"><span data-stu-id="91171-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="91171-109">Vyhledejte fragment uzlu, který si přejete transformace.</span><span class="sxs-lookup"><span data-stu-id="91171-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="91171-110">Vytvořte samostatný objekt s právě fragment uzlu.</span><span class="sxs-lookup"><span data-stu-id="91171-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="91171-111">Předat uzlu fragment k <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="91171-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91171-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="91171-112">Example</span></span>  
 <span data-ttu-id="91171-113">Následující příklad transformuje fragment uzlu a výsledky do konzoly.</span><span class="sxs-lookup"><span data-stu-id="91171-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="91171-114">Vstup</span><span class="sxs-lookup"><span data-stu-id="91171-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="91171-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="91171-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="91171-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="91171-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="91171-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="91171-117">Output</span></span>  
 <span data-ttu-id="91171-118">Název adresáře je Man spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="91171-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91171-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="91171-119">See Also</span></span>  
 [<span data-ttu-id="91171-120">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="91171-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
