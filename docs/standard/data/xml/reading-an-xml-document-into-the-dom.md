---
title: Čtení dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad649e61f4f006103d38a998eece174a07889828
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569717"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="781b3-102">Čtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="781b3-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="781b3-103">Informace o XML je načíst do paměti z různých formátech.</span><span class="sxs-lookup"><span data-stu-id="781b3-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="781b3-104">Může být číst z řetězce, datový proud, adresa URL, čtečky textu nebo třídy odvozené od <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="781b3-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="781b3-105"><xref:System.Xml.XmlDocument.Load%2A> Metoda přináší dokumentu do paměti a přetížil metody, které jsou k dispozici pro trvat data z každé z různých formátech.</span><span class="sxs-lookup"><span data-stu-id="781b3-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="781b3-106">K dispozici je také <xref:System.Xml.XmlDocument.LoadXml%2A> metoda, která čte XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="781b3-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="781b3-107">Různé <xref:System.Xml.XmlDocument.Load%2A> metody ovlivnit uzlů, které jsou vytvořeny při načítání modelu pro objekt dokumentu XML (DOM).</span><span class="sxs-lookup"><span data-stu-id="781b3-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="781b3-108">V následující tabulce jsou uvedeny rozdíly mezi některé <xref:System.Xml.XmlDocument.Load%2A> metody a témata, která je vyřešit.</span><span class="sxs-lookup"><span data-stu-id="781b3-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="781b3-109">Předmět</span><span class="sxs-lookup"><span data-stu-id="781b3-109">Subject</span></span>|<span data-ttu-id="781b3-110">Téma</span><span class="sxs-lookup"><span data-stu-id="781b3-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="781b3-111">Vytvoření mezer uzlů</span><span class="sxs-lookup"><span data-stu-id="781b3-111">Creation of white space nodes</span></span>|<span data-ttu-id="781b3-112">Objekt použitý k načtení modelu DOM má vliv na mezer a uzly významné prázdné znaky, které jsou generované v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="781b3-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="781b3-113">Další informace najdete v tématu [mezer a významné zpracování mezer při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="781b3-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="781b3-114">Načtení XML od konkrétním uzlu nebo načítání celého dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="781b3-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="781b3-115">Pomocí <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> metoda data je možné načíst z konkrétní uzlu do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="781b3-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="781b3-116">Další informace najdete v tématu [načítání dat z čtečku](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="781b3-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="781b3-117">Ověření XML, protože je načtena</span><span class="sxs-lookup"><span data-stu-id="781b3-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="781b3-118">Data XML načíst do modelu DOM může být ověřen, jako je načten.</span><span class="sxs-lookup"><span data-stu-id="781b3-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="781b3-119">Toho dosahuje pomocí ověřování <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="781b3-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="781b3-120">Další informace o ověření XML, jako je načtena, najdete v části [ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="781b3-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="781b3-121">Následující příklad ukazuje XML načítá s <xref:System.Xml.XmlDocument.LoadXml%2A> metoda a data následně uložená do textového souboru s názvem `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="781b3-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="781b3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="781b3-122">See Also</span></span>  
 [<span data-ttu-id="781b3-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="781b3-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
