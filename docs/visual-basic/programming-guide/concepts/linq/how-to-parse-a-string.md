---
title: 'Postupy: Analýza řetězce'
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 31bae00eb3ebf0d8e64fc657693e8c0767c4f5d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344487"
---
# <a name="how-to-parse-a-string-visual-basic"></a>Postupy: Analýza řetězce (Visual Basic)
Toto téma ukazuje, jak vytvořit strom XML v C#.  
  
## <a name="example"></a>Příklad  
 Můžete analyzovat řetězec v Visual Basic pomocí metody `XElement.Parse`. Je však efektivnější používat literály XML, jak je znázorněno v následujícím kódu, protože literály XML netrpí stejnými pokutami výkonu při analýze XML z řetězce.  
  
 Pomocí literálů XML můžete zkopírovat a vložit XML do programu Visual Basic.  
  
> [!NOTE]
> Analýza textu nebo načítání dokumentu XML z textového souboru je méně efektivní než konstrukce funkčnosti. Pokud inicializujete strom XML z kódu, zabere méně času procesoru na použití funkční konstrukce než k analýze textu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
