---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287815"
---
# <a name="converting-net-framework-types-to-strings"></a>Převádění typů rozhraní .NET Framework na řetězce
Pokud chcete převést .NET Framework typ na řetězec, použijte metodu **ToString** . Metoda **ToString** vrátí řetězcovou reprezentaci typu předaného. V následující tabulce jsou uvedeny typy .NET Framework, které vracejí řetězec ve formátu, který se mapuje na specifikace schématu XML (XSD).  
  
|Typ rozhraní .NET Framework|Vrácený typ řetězce|  
|-------------------------|--------------------------|  
|Logická hodnota|"pravda", "NEPRAVDA"|  
|Single. PositiveInfinity|SOUBORŮ|  
|Single. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|SOUBORŮ|  
|Double. NegativeInfinity|"-INF"|  
|DateTime|Formát je RRRR-MM-ddTHH: mm: sszzzzzz a jeho podmnožiny.|  
|Časový interval|Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` je doba 2 roky, 10 měsíců, 15 dní, 10hours, 30 minut a 20 sekund.|  
  
## <a name="see-also"></a>Viz také

- [Převod datových typů XML](conversion-of-xml-data-types.md)
- [Převádění řetězců na datové typy rozhraní .NET Framework](converting-strings-to-dotnet-data-types.md)
