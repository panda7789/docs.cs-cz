---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1e9b22a4bc876e9b02ec0da0439682082d2d706
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="converting-net-framework-types-to-strings"></a>Převádění typů rozhraní .NET Framework na řetězce
Pokud chcete převést typ rozhraní .NET Framework na řetězec, použijte **ToString** metoda. **ToString** metoda vrátí řetězcovou reprezentaci předaný typ. Následující tabulka uvádí typy rozhraní .NET Framework, které vrací řetězec ve formátu, který se mapuje na specifikacích schématu XML (XSD).  
  
|Typ rozhraní .NET Framework|Typ řetězec vrácený|  
|-------------------------|--------------------------|  
|Boolean|"PRAVDA", "Nepravda"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Formát je rrrr-MM-ddTHH:mm:sszzzzzz a jeho podmnožin.|  
|Časový interval|Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` je trvání 10hours 2 roky, 10 měsíců, 15 dní, 30 minut a 20 sekund.|  
  
## <a name="see-also"></a>Viz také  
 [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Převádění řetězců na datové typy rozhraní .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
