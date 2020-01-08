---
title: 'Postupy: Zápis dat objektů do souboru XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 989920709428f0e9cb4ddb8aeacfc71a2df220d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345981"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Postupy: zápis dat objektů do souboru XML (Visual Basic)
Tento příklad zapíše objekt z třídy do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.  
  
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
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Třída musí mít veřejný konstruktor bez parametrů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Serializovaná třída nemá veřejný konstruktor bez parametrů.  
  
- Soubor existuje a je určen jen pro čtení (<xref:System.IO.IOException>).  
  
- Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
- Disk je plný (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, musí tato aplikace `Create` přístup ke složce. Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, což je méně oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jednomu souboru místo `Create` přístupu pro složku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Postupy: čtení dat objektů ze souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
