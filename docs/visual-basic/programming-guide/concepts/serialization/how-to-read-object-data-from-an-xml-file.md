---
title: 'Postupy: Čtení dat objektů ze souboru XML'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: efd5fb72487c92bcccf1fc797106f93c0d2a39fc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345984"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Postupy: čtení dat objektů ze souboru XML (Visual Basic)
Tento příklad načte data objektů, která byla dříve zapsána do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Příklad  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Nahraďte název souboru "c:\temp\SerializationOverview.xml" názvem souboru, který obsahuje Serializovaná data. Další informace o serializaci dat naleznete v tématu [How to: Write Data Object to a XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Třída musí mít veřejný konstruktor bez parametrů.  
  
 Pouze veřejné vlastnosti a pole jsou deserializovány.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Serializovaná třída nemá veřejný konstruktor bez parametrů.  
  
- Data v souboru reprezentují data z třídy, která se má deserializovat.  
  
- Soubor neexistuje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy ověřte vstupy a nikdy neserializovat data z nedůvěryhodného zdroje. Nově vytvořený objekt je spuštěn v místním počítači s oprávněním kódu, který jej deserializovat. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Postupy: zápis dat objektů do souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
