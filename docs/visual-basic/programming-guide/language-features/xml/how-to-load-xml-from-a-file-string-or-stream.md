---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo proudu'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330964"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="8b6ea-102">Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6ea-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="8b6ea-103">Můžete vytvořit [literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) a naplnit je obsahem z externího zdroje, jako je například soubor, řetězec nebo datový proud pomocí několika metod.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="8b6ea-104">Tyto metody jsou uvedeny v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="8b6ea-105">Načtení XML ze souboru</span><span class="sxs-lookup"><span data-stu-id="8b6ea-105">To load XML from a file</span></span>

<span data-ttu-id="8b6ea-106">Chcete-li naplnit literál XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt ze souboru, použijte metodu `Load`.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="8b6ea-107">Tato metoda může jako vstup přijmout cestu k souboru, textový Stream nebo datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="8b6ea-108">Následující příklad kódu ukazuje použití metody <xref:System.Xml.Linq.XDocument.Load%28System.String%29> k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="8b6ea-109">Načtení XML z řetězce</span><span class="sxs-lookup"><span data-stu-id="8b6ea-109">To load XML from a string</span></span>

<span data-ttu-id="8b6ea-110">Chcete-li naplnit literál XML, jako je například <xref:System.Xml.Linq.XElement> nebo objekt <xref:System.Xml.Linq.XDocument> z řetězce, lze použít metodu `Parse`.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="8b6ea-111">Následující příklad kódu ukazuje použití metody <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="8b6ea-112">Načtení XML z datového proudu</span><span class="sxs-lookup"><span data-stu-id="8b6ea-112">To load XML from a stream</span></span>

<span data-ttu-id="8b6ea-113">Chcete-li naplnit literál XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt z datového proudu, lze použít metodu `Load` nebo metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="8b6ea-114">Následující příklad kódu ukazuje použití metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="8b6ea-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="8b6ea-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b6ea-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8b6ea-116">Literály XML</span><span class="sxs-lookup"><span data-stu-id="8b6ea-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="8b6ea-117">XML</span><span class="sxs-lookup"><span data-stu-id="8b6ea-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="8b6ea-118">Manipulace s XML v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b6ea-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
