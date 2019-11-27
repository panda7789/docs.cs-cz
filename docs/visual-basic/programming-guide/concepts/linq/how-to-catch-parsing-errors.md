---
title: 'Postupy: zachycení chyb při analýze'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353347"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Postupy: zachycení chyb při analýze (Visual Basic)
V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se implementuje pomocí <xref:System.Xml.XmlReader>. Pokud je do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]předán chybně vytvořený nebo neplatný kód XML, podkladová třída <xref:System.Xml.XmlReader> vyvolá výjimku. Různé metody, které analyzují kód XML, jako je například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nezachycují výjimku. výjimku lze následně zachytit ve vaší aplikaci.  
  
 Všimněte si, že pokud používáte literály XML, nemůžete získat chyby analýzy. Kompilátor Visual Basic zachytí chyby nesprávně vytvořeného nebo neplatného kódu XML.  
  
## <a name="example"></a>Příklad  
 Následující kód se pokusí analyzovat neplatný kód XML:  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 Při spuštění tohoto kódu vyvolá následující výjimku:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Informace o výjimkách, které lze očekávat <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody, naleznete v dokumentaci <xref:System.Xml.XmlReader>.  
  
## <a name="see-also"></a>Viz také:

- [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
