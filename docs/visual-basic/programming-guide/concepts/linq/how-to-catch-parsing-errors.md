---
title: 'Postupy: Chyby analýzy zachycení (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: a0c0749e8bc6d3fb1a71595778bfc5effaaf8533
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352939"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Postupy: Chyby analýzy zachycení (Visual Basic)
V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se implementuje pomocí <xref:System.Xml.XmlReader>. Pokud je do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] předán chybně vytvořený nebo neplatný kód XML, podkladová třída <xref:System.Xml.XmlReader> vyvolá výjimku. Různé metody, které analyzují kód XML, například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nezachycují výjimku; výjimku lze následně zachytit ve vaší aplikaci.  
  
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
  
 Informace o výjimkách, které můžete očekávat metodou <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, najdete v dokumentaci k @no__t 4.  
  
## <a name="see-also"></a>Viz také:

- [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
