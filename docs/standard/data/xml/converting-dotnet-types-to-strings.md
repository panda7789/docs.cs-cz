---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98ebc9248b0585295adf12e04dece0fef654c2e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953982"
---
# <a name="converting-net-framework-types-to-strings"></a>Převádění typů rozhraní .NET Framework na řetězce
Pokud chcete převést na řetězec, typ rozhraní .NET Framework, použijte **ToString** metody. **ToString** metoda vrátí řetězcovou reprezentaci objektu předaný typ. Následující tabulka uvádí typy rozhraní .NET Framework, které vrací řetězec ve formátu, který se mapuje na specifikace schématu XML (XSD).  
  
|Typ rozhraní .NET Framework|Vrátí typ String|  
|-------------------------|--------------------------|  
|Boolean|"PRAVDA", "Nepravda"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Formát je rrrr-MM-ddTHH:mm:sszzzzzz a její podskupiny.|  
|Časový interval|Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` je po dobu 2 let, 10 měsíců, 15 dnů, 10hours 30 minut a 20 sekund.|  
  
## <a name="see-also"></a>Viz také:

- [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Převádění řetězců na datové typy rozhraní .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
