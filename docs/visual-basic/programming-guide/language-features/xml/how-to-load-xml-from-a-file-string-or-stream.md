---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo Stream (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 2b9da2062068ef25c5df97ef19b1502999ea78ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832135"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="9074b-102">Postupy: Načtení XML ze souboru, řetězce nebo Stream (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9074b-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="9074b-103">Můžete vytvořit [literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) a naplníte je obsah z externího zdroje, jako je například souboru, řetězce nebo proudu pomocí několika metod.</span><span class="sxs-lookup"><span data-stu-id="9074b-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="9074b-104">Tyto metody jsou uvedeny v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="9074b-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="9074b-105">Načtení XML ze souboru</span><span class="sxs-lookup"><span data-stu-id="9074b-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="9074b-106">K naplnění literálu jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt ze souboru, použijte `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="9074b-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="9074b-107">Tato metoda může trvat cesta k souboru, textového datového proudu nebo datový proud XML jako vstup.</span><span class="sxs-lookup"><span data-stu-id="9074b-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="9074b-108">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metoda k naplnění <xref:System.Xml.Linq.XDocument> objektu s jazykem XML z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="9074b-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="9074b-109">Načtení XML z řetězce</span><span class="sxs-lookup"><span data-stu-id="9074b-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="9074b-110">K naplnění literálu jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt z řetězce, můžete použít `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="9074b-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="9074b-111">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="9074b-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="9074b-112">Načtení z datový proud XML</span><span class="sxs-lookup"><span data-stu-id="9074b-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="9074b-113">K naplnění literálu jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu z datového proudu, můžete použít `Load` – metoda nebo <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9074b-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9074b-114">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda k naplnění <xref:System.Xml.Linq.XDocument> objektu s jazykem XML z datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="9074b-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="9074b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9074b-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9074b-116">Literály XML</span><span class="sxs-lookup"><span data-stu-id="9074b-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="9074b-117">XML</span><span class="sxs-lookup"><span data-stu-id="9074b-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="9074b-118">Manipulace s kódem XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9074b-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
