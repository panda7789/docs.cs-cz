---
title: Jak zachytit chyby při analýze (C#)
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 1a05037892061dec85e7837472e8ec13e076724b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141484"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="d0132-102">Jak zachytit chyby při analýze (C#)</span><span class="sxs-lookup"><span data-stu-id="d0132-102">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="d0132-103">V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="d0132-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d0132-104">se implementuje pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d0132-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d0132-105">Pokud je do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]předán chybně vytvořený nebo neplatný kód XML, podkladová třída <xref:System.Xml.XmlReader> vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="d0132-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="d0132-106">Různé metody, které analyzují kód XML, jako je například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nezachycují výjimku. výjimku lze následně zachytit ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d0132-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0132-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0132-107">Example</span></span>  
 <span data-ttu-id="d0132-108">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="d0132-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="d0132-109">Při spuštění tohoto kódu vyvolá následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="d0132-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="d0132-110">Informace o výjimkách, které lze očekávat <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody, naleznete v dokumentaci <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d0132-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  