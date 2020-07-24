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
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="e8631-104">Jak zachytit chyby při analýze (C#)</span><span class="sxs-lookup"><span data-stu-id="e8631-104">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="e8631-105">V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="e8631-105">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e8631-106">je implementován pomocí <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="e8631-106">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e8631-107">Pokud je předaný chybně vytvořen nebo je neplatný kód XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , bude podkladová <xref:System.Xml.XmlReader> Třída generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="e8631-107">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="e8631-108">Různé metody, které analyzují kód XML, například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nezachycují výjimku; výjimku lze následně zachytit v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e8631-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8631-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8631-109">Example</span></span>  
 <span data-ttu-id="e8631-110">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="e8631-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="e8631-111">Při spuštění tohoto kódu vyvolá následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="e8631-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="e8631-112">Informace o výjimkách, které lze očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> metody,, a mohou <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> být vyvolávat, naleznete v <xref:System.Xml.XmlReader> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="e8631-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  