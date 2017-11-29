---
title: "Bezpečnost vlákna v regulárních výrazech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpečnost vlákna v regulárních výrazech
<xref:System.Text.RegularExpressions.Regex> Samotné třídy je vlákno bezpečné a neměnné (jen pro čtení). To znamená **Regex** objektů můžete vytvořit z libovolného vlákna a sdílet mezi vlákny; odpovídající metody lze volat z libovolného vlákna a nikdy alter žádný globální stav.  
  
 Objekty výsledků však (**shodu** a **MatchCollection**) vrácený **Regex** je třeba použít na jedno vlákno. I když některá z těchto objektů jsou logicky neměnné, jejich implementace by mohla zpozdit výpočty některých výsledků ke zlepšení výkonu a v důsledku toho musí volající serializovat přístup k nim.  
  
 Pokud je třeba sdílet **Regex** výsledek objektů na více vláken, tyto objekty lze převést na instancí vláken voláním jejich synchronizovaných metod. Všechny třídy regulárních výrazů s výjimkou výčty, jsou bezpečné pro přístup z více vláken nebo mohou být převedeny na objekty zabezpečenými synchronizované metodou.  
  
 Výčty jsou jedinou výjimkou. Aplikace musí serializovat volání čítačů kolekcí. Pravidlo je, pokud kolekce, mohou být současně uvedené na více než jedno vlákno, bude třeba synchronizovat metody enumerátor pro kořenový objekt kolekce procházené pomocí čítače.  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
