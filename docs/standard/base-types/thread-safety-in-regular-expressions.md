---
title: Bezpečnost vlákna v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046876"
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpečnost vlákna v regulárních výrazech
<xref:System.Text.RegularExpressions.Regex> Třídu je vlákno, byla v bezpečí a neměnné (jen pro čtení). To znamená **regulární výraz** objektů se dají vytvářet v libovolném vlákně a sdílet mezi vlákny; odpovídající metody lze volat z libovolného vlákna a nikdy měnit žádné globální stav.  
  
 Nicméně objekty výsledků (**shoda** a **MatchCollection**) vrácený **regulární výraz** byste neměli používat v jednom vlákně. I když mnohé z těchto objektů jsou logicky neměnné, jejich implementace mohly zpožďovat výpočtu některé výsledky pro zvýšení výkonu a v důsledku toho volající musí serializovat přístup k nim.  
  
 Pokud je potřeba sdílet **regulární výraz** výsledek objektů z více vláken, tyto objekty lze převést na instance bezpečným pro vlákno voláním jejich synchronizované metody. S výjimkou enumerátory všechny třídy regulárních výrazů jsou bezpečné pro vlákna nebo mohou být převedeny na bezpečné pro vlákna objekty synchronizované metody.  
  
 Enumerátory jsou jedinou výjimkou. Aplikace musí serializovat volání kolekce enumerátory. Pokud kolekce jsou současně uvedené na více než jedno vlákno, bude třeba synchronizovat enumerátor metody na kořenový objekt kolekce procházené pomocí čítače výčtu je pravidlo.  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)
