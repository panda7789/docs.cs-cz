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
# <a name="reading-an-xml-document-into-the-dom"></a>Načtení dokumentu XML do modelu DOM
Informace XML jsou čteny do paměti z různých formátů. Lze ho číst z řetězce, datového proudu, adresy URL, čtečky textu nebo třídy odvozené z <xref:System.Xml.XmlReader>.  
  
 Metoda <xref:System.Xml.XmlDocument.Load%2A> přiřadí dokument do paměti a má přetížené metody, které jsou k dispozici pro převzetí dat z různých formátů. Existuje také metoda <xref:System.Xml.XmlDocument.LoadXml%2A>, která čte XML z řetězce.  
  
 Různé metody <xref:System.Xml.XmlDocument.Load%2A> ovlivňují, které uzly budou vytvořeny při načtení XML model DOM (Document Object Model) (DOM). V následující tabulce jsou uvedeny rozdíly mezi některými <xref:System.Xml.XmlDocument.Load%2A> metodami a tématy, která je řeší.  
  
|Závislosti|Téma|  
|-------------|-----------|  
|Vytváření mezerových uzlů|Objekt použitý k načtení modelu DOM má vliv na prázdné místo a významné uzly prázdné místo vygenerované v modelu DOM. Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Načítání XML od určitého uzlu nebo načítání celého dokumentu XML|Použití dat metody <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> lze načíst z konkrétního uzlu do modelu DOM. Další informace najdete v tématu [načtení dat z čtecího zařízení](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Ověřování XML při načtení|Data XML načtená do modelu DOM lze ověřit tak, jak jsou načtena. To se provádí pomocí ověřování <xref:System.Xml.XmlReader>. Další informace o ověřování XML při jeho načtení naleznete v tématu [ověření dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 Následující příklad ukazuje XML načtený pomocí metody <xref:System.Xml.XmlDocument.LoadXml%2A> a data následně uložená do textového souboru s názvem `data.xml`.  
  
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
