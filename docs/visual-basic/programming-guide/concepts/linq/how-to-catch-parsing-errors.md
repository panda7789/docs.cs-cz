---
title: "Postupy: zachycení analýza chyb (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82b7c51aa8d0f9f64094211c56875e6595607c00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="916f7-102">Postupy: zachycení analýza chyb (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="916f7-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="916f7-103">Toto téma ukazuje, jak zjišťovat XML chybně formátovaný nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="916f7-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="916f7-104">je implementovaná pomocí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="916f7-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="916f7-105">Pokud je chybně vytvořený nebo je neplatný XML předaný [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], základní <xref:System.Xml.XmlReader> třída vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="916f7-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="916f7-106">Různé metody, které analyzovat soubor XML, jako například <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, není zachycení výjimky; výjimku pak může být zachycena vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="916f7-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="916f7-107">Všimněte si, že nelze získat analyzovat chyby, pokud používáte literálů XML.</span><span class="sxs-lookup"><span data-stu-id="916f7-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="916f7-108">Visual Basic – kompilátor zachytí chyby XML chybně formátovaný nebo je neplatný.</span><span class="sxs-lookup"><span data-stu-id="916f7-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="916f7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="916f7-109">Example</span></span>  
 <span data-ttu-id="916f7-110">Následující kód se pokusí analyzovat neplatný kód XML:</span><span class="sxs-lookup"><span data-stu-id="916f7-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="916f7-111">Když spustíte tento kód, vyvolá následující výjimky:</span><span class="sxs-lookup"><span data-stu-id="916f7-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="916f7-112">Informace o výjimky, které můžete očekávat, že <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, a <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> metody pro výjimku, najdete v článku <xref:System.Xml.XmlReader> dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="916f7-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916f7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="916f7-113">See Also</span></span>  
 [<span data-ttu-id="916f7-114">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="916f7-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
