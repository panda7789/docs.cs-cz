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
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="d3422-102">Jak zachytit chyby analýzy (C#)</span><span class="sxs-lookup"><span data-stu-id="d3422-102">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="d3422-103">Toto téma ukazuje, jak zjistit špatně vytvořené nebo neplatné XML.</span><span class="sxs-lookup"><span data-stu-id="d3422-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d3422-104">implementována <xref:System.Xml.XmlReader>pomocí .</span><span class="sxs-lookup"><span data-stu-id="d3422-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d3422-105">Pokud je předán chybně vytvořený [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nebo <xref:System.Xml.XmlReader> neplatný xml , základní třída vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="d3422-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="d3422-106">Různé metody, které analyzují <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>XML, například , nezachycují výjimku; výjimku pak může vaše aplikace zachytit.</span><span class="sxs-lookup"><span data-stu-id="d3422-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3422-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3422-107">Example</span></span>  
 <span data-ttu-id="d3422-108">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="d3422-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="d3422-109">Při spuštění tohoto kódu vyvolá následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="d3422-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="d3422-110">Informace o výjimkách, které můžete <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>očekávat <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , a metody <xref:System.Xml.XmlReader> vyvolat, naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="d3422-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  