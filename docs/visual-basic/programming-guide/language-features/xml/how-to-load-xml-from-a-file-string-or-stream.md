---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo proudu'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392285"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="4fcd4-102">Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fcd4-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="4fcd4-103">Můžete vytvořit [literály XML](../../../language-reference/xml-literals/index.md) a naplnit je obsahem z externího zdroje, jako je například soubor, řetězec nebo datový proud pomocí několika metod.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-103">You can create [XML Literals](../../../language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="4fcd4-104">Tyto metody jsou uvedeny v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="4fcd4-105">Načtení XML ze souboru</span><span class="sxs-lookup"><span data-stu-id="4fcd4-105">To load XML from a file</span></span>

<span data-ttu-id="4fcd4-106">K naplnění literálu XML jako <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objektu nebo ze souboru použijte `Load` metodu.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="4fcd4-107">Tato metoda může jako vstup přijmout cestu k souboru, textový Stream nebo datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="4fcd4-108">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metody k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="4fcd4-109">Načtení XML z řetězce</span><span class="sxs-lookup"><span data-stu-id="4fcd4-109">To load XML from a string</span></span>

<span data-ttu-id="4fcd4-110">K naplnění literálu XML, jako je například <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objekt nebo z řetězce, lze použít `Parse` metodu.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="4fcd4-111">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metody k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="4fcd4-112">Načtení XML z datového proudu</span><span class="sxs-lookup"><span data-stu-id="4fcd4-112">To load XML from a stream</span></span>

<span data-ttu-id="4fcd4-113">Chcete-li naplnit literál XML jako <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objekt nebo z datového proudu, můžete použít `Load` metodu nebo <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4fcd4-114">Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="4fcd4-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="4fcd4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fcd4-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4fcd4-116">Literály XML</span><span class="sxs-lookup"><span data-stu-id="4fcd4-116">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="4fcd4-117">XML</span><span class="sxs-lookup"><span data-stu-id="4fcd4-117">XML</span></span>](index.md)
- [<span data-ttu-id="4fcd4-118">Zacházení s XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4fcd4-118">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
