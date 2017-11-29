---
title: "Převádění typů rozhraní .NET Framework na řetězce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3abe140e62f112a15a1ad1b1b2a79c14364b26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Převod XML datových typů](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Převádění řetězců na rozhraní .NET Framework datové typy](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
