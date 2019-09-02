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
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="e10c2-102">Postupy: Chyby analýzy zachycení (C#)</span><span class="sxs-lookup"><span data-stu-id="e10c2-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="e10c2-103">V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="e10c2-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e10c2-104">je implementován pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="e10c2-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e10c2-105">Pokud je předaný [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chybně vytvořen nebo je neplatný kód XML <xref:System.Xml.XmlReader> , bude podkladová třída generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="e10c2-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="e10c2-106">Různé metody, které analyzují kód XML, <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>například, nezachycují výjimku; výjimku lze následně zachytit v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e10c2-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e10c2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e10c2-107">Example</span></span>  
 <span data-ttu-id="e10c2-108">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="e10c2-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="e10c2-109">Při spuštění tohoto kódu vyvolá následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="e10c2-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="e10c2-110">Informace o výjimkách <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, které lze očekávat, že <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a mohou být vyvolávat, naleznete <xref:System.Xml.XmlReader> v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="e10c2-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  