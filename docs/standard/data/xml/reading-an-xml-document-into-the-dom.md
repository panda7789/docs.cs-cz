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
ms.openlocfilehash: 9031f5df0d0f48dc2844cdfd0654ee4ab876cc22
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44045999"
---
# <a name="reading-an-xml-document-into-the-dom"></a>Čtení dokumentu XML do modelu DOM
Informace o XML je načíst do paměti v různých formátech. Může být číst z řetězce, datového proudu, adresa URL, čtečky textu nebo třídu odvozenou z <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Metoda přináší dokumentu do paměti a přetížil metody dostupné pro vzít data ze všech různých formátech. K dispozici je také <xref:System.Xml.XmlDocument.LoadXml%2A> metodu, která čte z řetězce XML.  
  
 Různé <xref:System.Xml.XmlDocument.Load%2A> metody vliv na uzly, na kterých jsou vytvořeny při načtení XML Document Object Model (DOM). V následující tabulce jsou uvedeny rozdíly mezi některé <xref:System.Xml.XmlDocument.Load%2A> metody a témata, která je řešit.  
  
|Předmět|Téma|  
|-------------|-----------|  
|Vytvoření prázdné znaky uzly|Objekt použitý k načtení modelu DOM má vliv na mezer a významných mezer uzly vygenerované v modelu DOM. Další informace najdete v tématu [mezer a významných mezer zpracování při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Načítá se XML od konkrétní uzel nebo načítání celého dokumentu XML|Použití <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> metoda data je možné načíst z určitého uzlu do modelu DOM. Další informace najdete v tématu [načtení dat z čtečky](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Ověřuje se XML jako jeho načtení|Načtení do modelu DOM data XML můžete ověřit, protože je načtena. To lze provést pomocí ověřování <xref:System.Xml.XmlReader>. Další informace o ověřování XML, protože je načtena, naleznete v tématu [ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Následující příklad ukazuje načítání s XML <xref:System.Xml.XmlDocument.LoadXml%2A> metoda a dat, následně uloženy do textového souboru s názvem `data.xml`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
