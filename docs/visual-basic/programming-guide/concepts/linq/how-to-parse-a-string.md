---
title: 'Postupy: Analýze řetězce (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 815e94b3b41c2c0cc1d18d598307ab292919bea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942594"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="37de5-102">Postupy: Analýze řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37de5-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="37de5-103">Toto téma ukazuje, jak vytvořit stromu XML v C#.</span><span class="sxs-lookup"><span data-stu-id="37de5-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37de5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="37de5-104">Example</span></span>  
 <span data-ttu-id="37de5-105">Řetězec v jazyce Visual Basic můžete analyzovat pomocí `XElement.Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="37de5-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="37de5-106">Je však efektivnější použijte literály XML, jak je znázorněno v následujícím kódu, protože není literály XML mají stejný snížení výkonu jako analýza kódu XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="37de5-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="37de5-107">Pomocí literálů XML můžete stačí zkopírovat a vložit soubor XML do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="37de5-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37de5-108">Analýza textu nebo načítání dokumentu XML z textového souboru je méně efektivní než funkční konstrukce.</span><span class="sxs-lookup"><span data-stu-id="37de5-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="37de5-109">Pokud se inicializace stromu XML z kódu, trvá méně času procesoru použít funkční konstrukce, než se analyzovat text.</span><span class="sxs-lookup"><span data-stu-id="37de5-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37de5-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37de5-110">See also</span></span>

- [<span data-ttu-id="37de5-111">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37de5-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
