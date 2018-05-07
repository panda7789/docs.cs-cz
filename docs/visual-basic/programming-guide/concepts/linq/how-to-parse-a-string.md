---
title: 'Postupy: Analýza řetězce (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: da12ec98e03acceae375bbed4fc6ad4c2a71ec2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a>Postupy: Analýza řetězce (Visual Basic)
Toto téma ukazuje, jak vytvořit strom XML v jazyce C#.  
  
## <a name="example"></a>Příklad  
 Řetězec v jazyce Visual Basic můžete analyzovat pomocí `XElement.Parse` metoda. Je však efektivnější použít XML – literály, jak je znázorněno v následujícím kódu, protože XML – literály se nebude vyskytovat ze stejné penalizacím výkonu jako analýzu kódu XML z řetězce.  
  
 Pomocí XML – literály můžete právě zkopírujte a vložte kód XML do programu jazyka Visual Basic.  
  
> [!NOTE]
>  Analýza textu nebo načítání dokumentu XML z textového souboru je míň efektivní než funkční konstrukce. Pokud se inicializace strom XML z kódu, zabere to méně času procesoru použít funkční konstrukce, než se analyzovat text.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
