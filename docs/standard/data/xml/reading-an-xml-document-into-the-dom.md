---
title: Načtení dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 2e61a9ed1a1ccaa2f9f1543efa1d33c3fcf00061
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130835"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="7bc6f-102">Načtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="7bc6f-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="7bc6f-103">Informace XML jsou čteny do paměti z různých formátů.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="7bc6f-104">Lze ho číst z řetězce, datového proudu, adresy URL, čtečky textu nebo třídy odvozené z <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="7bc6f-105">Metoda <xref:System.Xml.XmlDocument.Load%2A> přiřadí dokument do paměti a má přetížené metody, které jsou k dispozici pro převzetí dat z různých formátů.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="7bc6f-106">Existuje také metoda <xref:System.Xml.XmlDocument.LoadXml%2A>, která čte XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="7bc6f-107">Různé metody <xref:System.Xml.XmlDocument.Load%2A> ovlivňují, které uzly budou vytvořeny při načtení XML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="7bc6f-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="7bc6f-108">V následující tabulce jsou uvedeny rozdíly mezi některými <xref:System.Xml.XmlDocument.Load%2A> metodami a tématy, která je řeší.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="7bc6f-109">Závislosti</span><span class="sxs-lookup"><span data-stu-id="7bc6f-109">Subject</span></span>|<span data-ttu-id="7bc6f-110">Téma</span><span class="sxs-lookup"><span data-stu-id="7bc6f-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="7bc6f-111">Vytváření mezerových uzlů</span><span class="sxs-lookup"><span data-stu-id="7bc6f-111">Creation of white space nodes</span></span>|<span data-ttu-id="7bc6f-112">Objekt použitý k načtení modelu DOM má vliv na prázdné místo a významné uzly prázdné místo vygenerované v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="7bc6f-113">Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="7bc6f-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="7bc6f-114">Načítání XML od určitého uzlu nebo načítání celého dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="7bc6f-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="7bc6f-115">Použití dat metody <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> lze načíst z konkrétního uzlu do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="7bc6f-116">Další informace najdete v tématu [načtení dat z čtecího zařízení](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="7bc6f-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="7bc6f-117">Ověřování XML při načtení</span><span class="sxs-lookup"><span data-stu-id="7bc6f-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="7bc6f-118">Data XML načtená do modelu DOM lze ověřit tak, jak jsou načtena.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="7bc6f-119">To se provádí pomocí ověřování <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="7bc6f-120">Další informace o ověřování XML při jeho načtení naleznete v tématu [ověření dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="7bc6f-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="7bc6f-121">Následující příklad ukazuje XML načtený pomocí metody <xref:System.Xml.XmlDocument.LoadXml%2A> a data následně uložená do textového souboru s názvem `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="7bc6f-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7bc6f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bc6f-122">See also</span></span>

- [<span data-ttu-id="7bc6f-123">Model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="7bc6f-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
