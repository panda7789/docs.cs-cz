---
title: Načtení dokumentu XML do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 02338d72f51d3a7507c0dfa030383399b9e213f6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282399"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="675a4-102">Načtení dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="675a4-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="675a4-103">Informace XML jsou čteny do paměti z různých formátů.</span><span class="sxs-lookup"><span data-stu-id="675a4-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="675a4-104">Lze ho číst z řetězce, datového proudu, adresy URL, čtečky textu nebo třídy odvozené z <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="675a4-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="675a4-105">Metoda přiřadí <xref:System.Xml.XmlDocument.Load%2A> dokument do paměti a má přetížené metody, které jsou k dispozici pro převzetí dat z každého z různých formátů.</span><span class="sxs-lookup"><span data-stu-id="675a4-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="675a4-106">Existuje také <xref:System.Xml.XmlDocument.LoadXml%2A> metoda, která čte XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="675a4-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="675a4-107">Různé <xref:System.Xml.XmlDocument.Load%2A> metody ovlivňují, které uzly jsou vytvořeny při načtení XML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="675a4-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="675a4-108">V následující tabulce jsou uvedeny rozdíly mezi následujícími <xref:System.Xml.XmlDocument.Load%2A> metodami a tématy, která je řeší.</span><span class="sxs-lookup"><span data-stu-id="675a4-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="675a4-109">Subjekt</span><span class="sxs-lookup"><span data-stu-id="675a4-109">Subject</span></span>|<span data-ttu-id="675a4-110">Téma</span><span class="sxs-lookup"><span data-stu-id="675a4-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="675a4-111">Vytváření mezerových uzlů</span><span class="sxs-lookup"><span data-stu-id="675a4-111">Creation of white space nodes</span></span>|<span data-ttu-id="675a4-112">Objekt použitý k načtení modelu DOM má vliv na prázdné místo a významné uzly prázdné místo vygenerované v modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="675a4-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="675a4-113">Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="675a4-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="675a4-114">Načítání XML od určitého uzlu nebo načítání celého dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="675a4-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="675a4-115">Použití <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> dat metody lze načíst z konkrétního uzlu do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="675a4-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="675a4-116">Další informace najdete v tématu [načtení dat z čtecího zařízení](load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="675a4-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="675a4-117">Ověřování XML při načtení</span><span class="sxs-lookup"><span data-stu-id="675a4-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="675a4-118">Data XML načtená do modelu DOM lze ověřit tak, jak jsou načtena.</span><span class="sxs-lookup"><span data-stu-id="675a4-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="675a4-119">To se provádí pomocí ověřování <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="675a4-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="675a4-120">Další informace o ověřování XML při jeho načtení naleznete v tématu [ověření dokumentu XML v modelu DOM](validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="675a4-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="675a4-121">Následující příklad ukazuje XML načtený pomocí <xref:System.Xml.XmlDocument.LoadXml%2A> metody a data následně uložená do textového souboru s názvem `data.xml` .</span><span class="sxs-lookup"><span data-stu-id="675a4-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="675a4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="675a4-122">See also</span></span>

- [<span data-ttu-id="675a4-123">model DOM (Document Object Model) dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="675a4-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
