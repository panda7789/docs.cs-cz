---
title: Jak zachytit chyby analýzy (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141484"
---
# <a name="how-to-catch-parsing-errors-c"></a>Jak zachytit chyby analýzy (C#)
Toto téma ukazuje, jak zjistit špatně vytvořené nebo neplatné XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]implementována <xref:System.Xml.XmlReader>pomocí . Pokud je předán chybně vytvořený [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nebo <xref:System.Xml.XmlReader> neplatný xml , základní třída vyvolá výjimku. Různé metody, které analyzují <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>XML, například , nezachycují výjimku; výjimku pak může vaše aplikace zachytit.  
  
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
  
 Informace o výjimkách, které můžete <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>očekávat <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , a metody <xref:System.Xml.XmlReader> vyvolat, naleznete v dokumentaci.  
  