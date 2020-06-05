---
title: 'Postupy: Analýza řetězce'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 0a9076fc516bb8e6bc74732ca252fabfeda43d53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398009"
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="edcfb-102">Postupy: Analýza řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edcfb-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="edcfb-103">Toto téma ukazuje, jak vytvořit strom XML v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="edcfb-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edcfb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="edcfb-104">Example</span></span>  
 <span data-ttu-id="edcfb-105">Můžete analyzovat řetězec v Visual Basic pomocí `XElement.Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="edcfb-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="edcfb-106">Je však efektivnější používat literály XML, jak je znázorněno v následujícím kódu, protože literály XML netrpí stejnými pokutami výkonu při analýze XML z řetězce.</span><span class="sxs-lookup"><span data-stu-id="edcfb-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="edcfb-107">Pomocí literálů XML můžete zkopírovat a vložit XML do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="edcfb-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edcfb-108">Analýza textu nebo načítání dokumentu XML z textového souboru je méně efektivní než konstrukce funkčnosti.</span><span class="sxs-lookup"><span data-stu-id="edcfb-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="edcfb-109">Pokud inicializujete strom XML z kódu, zabere méně času procesoru na použití funkční konstrukce než k analýze textu.</span><span class="sxs-lookup"><span data-stu-id="edcfb-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edcfb-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="edcfb-110">See also</span></span>

- [<span data-ttu-id="edcfb-111">Analýza kódu XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edcfb-111">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
