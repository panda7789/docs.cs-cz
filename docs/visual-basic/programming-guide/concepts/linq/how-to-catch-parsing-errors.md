---
title: 'Postupy: Zachycení chyb (Visual Basic) při analýze'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 1a5d01d4853a9fd0cc7f0a0e5071b394ab3f218b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829374"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Postupy: Zachycení chyb (Visual Basic) při analýze
Toto téma ukazuje, jak detekovat XML chybně vytvořený nebo je neplatný.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je implementováno pomocí <xref:System.Xml.XmlReader>. Pokud je předán chybně vytvořený nebo neplatný XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], základní <xref:System.Xml.XmlReader> třída vyvolá výjimku. Různé metody, které analyzovat soubor XML, jako například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nebude zachytávat výjimky; výjimku pak může být zachycena vaší aplikace.  
  
 Všimněte si, že nejde získat chyby analýzy, pokud použijte literály XML. Kompilátor jazyka Visual Basic zachytí chyby XML chybně vytvořený nebo je neplatný.  
  
## <a name="example"></a>Příklad  
 Následující kód se pokusí analyzovat kód XML je neplatný:  
  
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
  
 Při spuštění tohoto kódu vyvolala následující výjimku:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Informace o výjimkách, které můžete očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody vyvolání, najdete v článku <xref:System.Xml.XmlReader> dokumentaci.  
  
## <a name="see-also"></a>Viz také:

- [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
