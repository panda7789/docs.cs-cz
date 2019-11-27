---
title: 'Postupy: zachycení chyb při analýze'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353347"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="b6e15-102">Postupy: zachycení chyb při analýze (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6e15-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="b6e15-103">V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="b6e15-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b6e15-104">se implementuje pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b6e15-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="b6e15-105">Pokud je do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]předán chybně vytvořený nebo neplatný kód XML, podkladová třída <xref:System.Xml.XmlReader> vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="b6e15-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="b6e15-106">Různé metody, které analyzují kód XML, jako je například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, nezachycují výjimku. výjimku lze následně zachytit ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b6e15-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="b6e15-107">Všimněte si, že pokud používáte literály XML, nemůžete získat chyby analýzy.</span><span class="sxs-lookup"><span data-stu-id="b6e15-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="b6e15-108">Kompilátor Visual Basic zachytí chyby nesprávně vytvořeného nebo neplatného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="b6e15-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e15-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6e15-109">Example</span></span>  
 <span data-ttu-id="b6e15-110">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="b6e15-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="b6e15-111">Při spuštění tohoto kódu vyvolá následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="b6e15-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="b6e15-112">Informace o výjimkách, které lze očekávat <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody, naleznete v dokumentaci <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="b6e15-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e15-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6e15-113">See also</span></span>

- [<span data-ttu-id="b6e15-114">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6e15-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
