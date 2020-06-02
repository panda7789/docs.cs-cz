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
# <a name="reading-an-xml-document-into-the-dom"></a>Načtení dokumentu XML do modelu DOM
Informace XML jsou čteny do paměti z různých formátů. Lze ho číst z řetězce, datového proudu, adresy URL, čtečky textu nebo třídy odvozené z <xref:System.Xml.XmlReader> .  
  
 Metoda přiřadí <xref:System.Xml.XmlDocument.Load%2A> dokument do paměti a má přetížené metody, které jsou k dispozici pro převzetí dat z každého z různých formátů. Existuje také <xref:System.Xml.XmlDocument.LoadXml%2A> metoda, která čte XML z řetězce.  
  
 Různé <xref:System.Xml.XmlDocument.Load%2A> metody ovlivňují, které uzly jsou vytvořeny při načtení XML model DOM (Document Object Model) (DOM). V následující tabulce jsou uvedeny rozdíly mezi následujícími <xref:System.Xml.XmlDocument.Load%2A> metodami a tématy, která je řeší.  
  
|Subjekt|Téma|  
|-------------|-----------|  
|Vytváření mezerových uzlů|Objekt použitý k načtení modelu DOM má vliv na prázdné místo a významné uzly prázdné místo vygenerované v modelu DOM. Další informace naleznete v tématu [mezera a významná manipulace s prázdným znakem při načítání modelu DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Načítání XML od určitého uzlu nebo načítání celého dokumentu XML|Použití <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> dat metody lze načíst z konkrétního uzlu do modelu DOM. Další informace najdete v tématu [načtení dat z čtecího zařízení](load-data-from-a-reader.md).|  
|Ověřování XML při načtení|Data XML načtená do modelu DOM lze ověřit tak, jak jsou načtena. To se provádí pomocí ověřování <xref:System.Xml.XmlReader> . Další informace o ověřování XML při jeho načtení naleznete v tématu [ověření dokumentu XML v modelu DOM](validating-an-xml-document-in-the-dom.md).|  
  
 Následující příklad ukazuje XML načtený pomocí <xref:System.Xml.XmlDocument.LoadXml%2A> metody a data následně uložená do textového souboru s názvem `data.xml` .  
  
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

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
