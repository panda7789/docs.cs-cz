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
# <a name="reading-an-xml-document-into-the-dom"></a>Čtení dokumentu XML do modelu DOM
Informace o XML je načíst do paměti z různých formátech. Může být číst z řetězce, datový proud, adresa URL, čtečky textu nebo třídy odvozené od <xref:System.Xml.XmlReader>.  
  
 <xref:System.Xml.XmlDocument.Load%2A> Metoda přináší dokumentu do paměti a přetížil metody, které jsou k dispozici pro trvat data z každé z různých formátech. K dispozici je také <xref:System.Xml.XmlDocument.LoadXml%2A> metoda, která čte XML z řetězce.  
  
 Různé <xref:System.Xml.XmlDocument.Load%2A> metody ovlivnit uzlů, které jsou vytvořeny při načítání modelu pro objekt dokumentu XML (DOM). V následující tabulce jsou uvedeny rozdíly mezi některé <xref:System.Xml.XmlDocument.Load%2A> metody a témata, která je vyřešit.  
  
|Předmět|Téma|  
|-------------|-----------|  
|Vytvoření mezer uzlů|Objekt použitý k načtení modelu DOM má vliv na mezer a uzly významné prázdné znaky, které jsou generované v modelu DOM. Další informace najdete v tématu [mezer a významné zpracování mezer při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Načtení XML od konkrétním uzlu nebo načítání celého dokumentu XML|Pomocí <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> metoda data je možné načíst z konkrétní uzlu do modelu DOM. Další informace najdete v tématu [načítání dat z čtečku](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Ověření XML, protože je načtena|Data XML načíst do modelu DOM může být ověřen, jako je načten. Toho dosahuje pomocí ověřování <xref:System.Xml.XmlReader>. Další informace o ověření XML, jako je načtena, najdete v části [ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Následující příklad ukazuje XML načítá s <xref:System.Xml.XmlDocument.LoadXml%2A> metoda a data následně uložená do textového souboru s názvem `data.xml`.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
