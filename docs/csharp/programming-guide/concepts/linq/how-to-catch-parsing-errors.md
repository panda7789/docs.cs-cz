---
title: 'Postupy: zachycení chyb (C#) při analýze'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 879a8f037e9d31051ef0d4059ee3ce2a2fca7a4d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503922"
---
# <a name="how-to-catch-parsing-errors-c"></a>Postupy: zachycení chyb (C#) při analýze
Toto téma ukazuje, jak detekovat XML chybně vytvořený nebo je neplatný.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je implementováno pomocí <xref:System.Xml.XmlReader>. Pokud je předán chybně vytvořený nebo neplatný XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], základní <xref:System.Xml.XmlReader> třída vyvolá výjimku. Různé metody, které analyzovat soubor XML, jako například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nebude zachytávat výjimky; výjimku pak může být zachycena vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Následující kód se pokusí analyzovat kód XML je neplatný:  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 Při spuštění tohoto kódu vyvolala následující výjimku:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Informace o výjimkách, které můžete očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody vyvolání, najdete v článku <xref:System.Xml.XmlReader> dokumentaci.  
  
## <a name="see-also"></a>Viz také

- [Analýza kódu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
