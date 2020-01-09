---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: a63e0175f6660967eb4aa678c6731d353e44e2d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711074"
---
# <a name="converting-net-framework-types-to-strings"></a>Převádění typů rozhraní .NET Framework na řetězce
Pokud chcete převést .NET Framework typ na řetězec, použijte metodu **ToString** . Metoda **ToString** vrátí řetězcovou reprezentaci typu předaného. V následující tabulce jsou uvedeny typy .NET Framework, které vracejí řetězec ve formátu, který se mapuje na specifikace schématu XML (XSD).  
  
|Typ rozhraní .NET Framework|Vrácený typ řetězce|  
|-------------------------|--------------------------|  
|Boolean|"pravda", "NEPRAVDA"|  
|Single. PositiveInfinity|"INF"|  
|Single. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|"INF"|  
|Double. NegativeInfinity|"-INF"|  
|Datum a čas|Formát je RRRR-MM-ddTHH: mm: sszzzzzz a jeho podmnožiny.|  
|Časový rozsah|Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` má délku 2 roky, 10 měsíců, 15 dní, 10hours, 30 minut a 20 sekund.|  
  
## <a name="see-also"></a>Viz také:

- [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Převádění řetězců na datové typy rozhraní .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
