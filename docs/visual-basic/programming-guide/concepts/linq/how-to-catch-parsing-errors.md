---
title: 'Postupy: Zachycení chyb při analýze'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: c0b46d7df270dd6f081a0c736b6978088cfbd9c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375145"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Postupy: zachycení chyb při analýze (Visual Basic)
V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je implementován pomocí <xref:System.Xml.XmlReader> . Pokud je předaný chybně vytvořen nebo je neplatný kód XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , bude podkladová <xref:System.Xml.XmlReader> Třída generovat výjimku. Různé metody, které analyzují kód XML, například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nezachycují výjimku; výjimku lze následně zachytit v aplikaci.  
  
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
  
 Informace o výjimkách, které lze očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> metody,, a mohou <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> být vyvolávat, naleznete v <xref:System.Xml.XmlReader> dokumentaci.  
  
## <a name="see-also"></a>Viz také

- [Analýza kódu XML (Visual Basic)](parsing-xml.md)
