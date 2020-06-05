---
title: 'Postupy: Zachycení chyb při analýze'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: c0b46d7df270dd6f081a0c736b6978088cfbd9c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375145"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="37261-102">Postupy: zachycení chyb při analýze (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37261-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="37261-103">V tomto tématu se dozvíte, jak zjistit chybně vytvořený nebo neplatný kód XML.</span><span class="sxs-lookup"><span data-stu-id="37261-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="37261-104">je implementován pomocí <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="37261-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="37261-105">Pokud je předaný chybně vytvořen nebo je neplatný kód XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , bude podkladová <xref:System.Xml.XmlReader> Třída generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="37261-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="37261-106">Různé metody, které analyzují kód XML, například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> , nezachycují výjimku; výjimku lze následně zachytit v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37261-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="37261-107">Všimněte si, že pokud používáte literály XML, nemůžete získat chyby analýzy.</span><span class="sxs-lookup"><span data-stu-id="37261-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="37261-108">Kompilátor Visual Basic zachytí chyby nesprávně vytvořeného nebo neplatného kódu XML.</span><span class="sxs-lookup"><span data-stu-id="37261-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37261-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="37261-109">Example</span></span>  
 <span data-ttu-id="37261-110">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="37261-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="37261-111">Při spuštění tohoto kódu vyvolá následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="37261-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="37261-112">Informace o výjimkách, které lze očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> metody,, a mohou <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> být vyvolávat, naleznete v <xref:System.Xml.XmlReader> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="37261-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37261-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="37261-113">See also</span></span>

- [<span data-ttu-id="37261-114">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37261-114">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
