---
title: 'Postupy: Čtení dat objektů ze souboru XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: f6233fc7ce74cbd39237bab07cfd2ed22b9c2240
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907345"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Postupy: Čtení dat objektů ze souboru XML (Visual Basic)
V tomto příkladu čte data objektu, který se předtím zapsala do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Název souboru "c:\temp\SerializationOverview.xml" nahraďte názvem souboru, který obsahuje serializovaná data. Další informace o serializaci dat najdete v tématu [jak: Zápis dat objektů do souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Třída musí mít veřejný konstruktor bez parametrů.  
  
 Pouze veřejné vlastnosti a pole se deserializovat.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Serializovaná třída nemá veřejný konstruktor bez parametrů.  
  
- Data v souboru nepředstavuje data ze třídy k deserializaci.  
  
- Soubor neexistuje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy zkontrolujte vstupy a nikdy deserializovat data z nedůvěryhodného zdroje. Objekt znovu vytvořit běží na místním počítači s oprávněními kód, který ji deserializovat. Před použitím dat ve své aplikaci ověřte všechny vstupy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- [Postupy: Zápis dat objektů do souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [Serializace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
