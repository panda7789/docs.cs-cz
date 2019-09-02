---
title: 'Postupy: Chyby analýzy zachycení (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 4195ff50d1b4d23cd9eb07fc27f20861d1504672
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204148"
---
# <a name="how-to-catch-parsing-errors-c"></a>Postupy: Chyby analýzy zachycení (C#)
V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je implementován pomocí <xref:System.Xml.XmlReader>. Pokud je předaný [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chybně vytvořen nebo je neplatný kód XML <xref:System.Xml.XmlReader> , bude podkladová třída generovat výjimku. Různé metody, které analyzují kód XML, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>například, nezachycují výjimku; výjimku lze následně zachytit v aplikaci.  
  
## <a name="example"></a>Příklad  
 Následující kód se pokusí analyzovat neplatný kód XML:  
  
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
  
 Při spuštění tohoto kódu vyvolá následující výjimku:  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Informace o výjimkách <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, které lze očekávat, že <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a mohou být vyvolávat, naleznete <xref:System.Xml.XmlReader> v dokumentaci.  
  