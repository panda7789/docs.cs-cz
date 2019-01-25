---
title: 'Postupy: Zápis dat objektů do souboru XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: a7784566cba7b9cf85914a410b78240856879ba8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715826"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Postupy: Zápis dat objektů do souboru XML (Visual Basic)
Tento příklad zapíše objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.  
  
## <a name="example"></a>Příklad  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Třída musí mít veřejný konstruktor bez parametrů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Serializovaná třída nemá veřejný konstruktor bez parametrů.  
  
-   Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).  
  
-   Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
-   Disk je plný (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace potřebuje vytvořit soubor, pak tato aplikace potřebuje `Create` přístup ke složce. Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, a menší oprávnění. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` přístup do jednoho souboru, spíše než `Create` přístup ke složce.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO.StreamWriter>
- [Postupy: Čtení dat objektů ze souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
