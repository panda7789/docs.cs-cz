---
title: 'Postupy: Zachycení chyb (Visual Basic) při analýze'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 1a5d01d4853a9fd0cc7f0a0e5071b394ab3f218b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829374"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="72c5c-102">Postupy: Zachycení chyb (Visual Basic) při analýze</span><span class="sxs-lookup"><span data-stu-id="72c5c-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="72c5c-103">Toto téma ukazuje, jak detekovat XML chybně vytvořený nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="72c5c-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="72c5c-104">je implementováno pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="72c5c-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="72c5c-105">Pokud je předán chybně vytvořený nebo neplatný XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], základní <xref:System.Xml.XmlReader> třída vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="72c5c-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="72c5c-106">Různé metody, které analyzovat soubor XML, jako například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nebude zachytávat výjimky; výjimku pak může být zachycena vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="72c5c-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="72c5c-107">Všimněte si, že nejde získat chyby analýzy, pokud použijte literály XML.</span><span class="sxs-lookup"><span data-stu-id="72c5c-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="72c5c-108">Kompilátor jazyka Visual Basic zachytí chyby XML chybně vytvořený nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="72c5c-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c5c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="72c5c-109">Example</span></span>  
 <span data-ttu-id="72c5c-110">Následující kód se pokusí analyzovat kód XML je neplatný:</span><span class="sxs-lookup"><span data-stu-id="72c5c-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="72c5c-111">Při spuštění tohoto kódu vyvolala následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="72c5c-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="72c5c-112">Informace o výjimkách, které můžete očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody vyvolání, najdete v článku <xref:System.Xml.XmlReader> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="72c5c-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c5c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72c5c-113">See also</span></span>

- [<span data-ttu-id="72c5c-114">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72c5c-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
