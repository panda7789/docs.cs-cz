---
title: 'Postupy: Analýza řetězce (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0fd7c7adcfbd7e2136d1a652017d470634016b9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
