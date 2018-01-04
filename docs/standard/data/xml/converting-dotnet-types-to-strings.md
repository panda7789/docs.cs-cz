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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
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
