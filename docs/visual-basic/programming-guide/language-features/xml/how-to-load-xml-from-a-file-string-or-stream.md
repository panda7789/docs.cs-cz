---
title: "Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 572e34b1cd4813fad35e6afaf2ec3d0d9dac470a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="e3a36-102">Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3a36-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="e3a36-103">Můžete vytvořit [XML – literály](../../../../visual-basic/language-reference/xml-literals/index.md) a naplnit je obsah z externího zdroje například souboru, řetězce nebo datový proud pomocí několika metod.</span><span class="sxs-lookup"><span data-stu-id="e3a36-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="e3a36-104">Tyto metody jsou uvedeny v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="e3a36-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="e3a36-105">K načtení XML ze souboru</span><span class="sxs-lookup"><span data-stu-id="e3a36-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="e3a36-106">K naplnění literál jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt ze souboru, použijte `Load` metoda.</span><span class="sxs-lookup"><span data-stu-id="e3a36-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="e3a36-107">Tato metoda může trvat cesta k souboru, datový proud text nebo datový proud XML jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e3a36-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="e3a36-108">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="e3a36-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="e3a36-109">K načtení XML z řetězce</span><span class="sxs-lookup"><span data-stu-id="e3a36-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="e3a36-110">K naplnění literál jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt z řetězce, můžete použít `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="e3a36-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="e3a36-111">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="e3a36-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="e3a36-112">K načtení XML z datového proudu</span><span class="sxs-lookup"><span data-stu-id="e3a36-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="e3a36-113">K naplnění literál jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu z datového proudu, můžete použít `Load` metoda nebo <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="e3a36-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e3a36-114">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="e3a36-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e3a36-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3a36-115">See Also</span></span>  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e3a36-116">XML – literály</span><span class="sxs-lookup"><span data-stu-id="e3a36-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="e3a36-117">XML</span><span class="sxs-lookup"><span data-stu-id="e3a36-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="e3a36-118">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3a36-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
