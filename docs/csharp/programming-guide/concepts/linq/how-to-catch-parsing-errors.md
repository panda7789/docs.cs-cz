---
title: 'Postupy: zachycení chyb (C#) při analýze'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 037e490fa7b0600b906ec310201e5d33c2f55baa
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198470"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="47fdf-102">Postupy: zachycení chyb (C#) při analýze</span><span class="sxs-lookup"><span data-stu-id="47fdf-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="47fdf-103">Toto téma ukazuje, jak detekovat XML chybně vytvořený nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="47fdf-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="47fdf-104"> je implementováno pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="47fdf-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="47fdf-105">Pokud je předán chybně vytvořený nebo neplatný XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], základní <xref:System.Xml.XmlReader> třída vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="47fdf-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="47fdf-106">Různé metody, které analyzovat soubor XML, jako například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nebude zachytávat výjimky; výjimku pak může být zachycena vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="47fdf-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47fdf-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="47fdf-107">Example</span></span>  
 <span data-ttu-id="47fdf-108">Následující kód se pokusí analyzovat kód XML je neplatný:</span><span class="sxs-lookup"><span data-stu-id="47fdf-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="47fdf-109">Při spuštění tohoto kódu vyvolala následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="47fdf-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="47fdf-110">Informace o výjimkách, které můžete očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody vyvolání, najdete v článku <xref:System.Xml.XmlReader> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="47fdf-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fdf-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="47fdf-111">See Also</span></span>  
 [<span data-ttu-id="47fdf-112">Analýza kódu XML (C#)</span><span class="sxs-lookup"><span data-stu-id="47fdf-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
