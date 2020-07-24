---
title: Jak zachytit chyby při analýze (C#)
description: Tento LINQ to XML příklad v jazyce C# detekuje chybně vytvořený nebo neplatný kód XML. LINQ to XML používá XmlReader, který vyvolá výjimku pro chybně vytvořený nebo neplatný kód XML.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105409"
---
# <a name="how-to-catch-parsing-errors-c"></a>Jak zachytit chyby při analýze (C#)
V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je implementován pomocí <xref:System.Xml.XmlReader> . Pokud je předaný chybně vytvořen nebo je neplatný kód XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , bude podkladová <xref:System.Xml.XmlReader> Třída generovat výjimku. Různé metody, které analyzují kód XML, například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nezachycují výjimku; výjimku lze následně zachytit v aplikaci.  
  
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
  
 Informace o výjimkách, které lze očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> metody,, a mohou <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> být vyvolávat, naleznete v <xref:System.Xml.XmlReader> dokumentaci.  
  