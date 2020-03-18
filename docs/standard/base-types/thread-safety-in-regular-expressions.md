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
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124802"
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpečnost vlákna v regulárních výrazech
Třída <xref:System.Text.RegularExpressions.Regex> sama o sobě je bezpečné pro přístup z více vláken a neměnné (jen pro čtení). To znamená, **že objekty Regex** lze vytvořit v libovolném vlákně a sdílet mezi podprocesy; odpovídající metody lze volat z libovolného vlákna a nikdy měnit žádný globální stav.  
  
 Však result objekty **(Match** a **MatchCollection**) vrácené **Regex** by měly být použity na jednom vlákně. Přestože mnoho z těchto objektů jsou logicky neměnné, jejich implementace může zpozdit výpočtu některých výsledků ke zlepšení výkonu a v důsledku toho volající musí serializovat přístup k nim.  
  
 Pokud je potřeba sdílet objekty **výsledků Regex** ve více vláknech, tyto objekty lze převést na instance bezpečné pro přístup z více vláken voláním jejich synchronizované metody. S výjimkou čítačů jsou všechny třídy regulárních výrazů bezpečné pro přístup z více vláken nebo mohou být synchronizovány na objekty bezpečné pro přístup z více vláken.  
  
 Výčty jsou jedinou výjimkou. Aplikace musí serializovat volání čítače výčtu kolekce. Pravidlo je, že pokud kolekce může být výčtu na více než jeden podproces současně, měli byste synchronizovat metody výčtu na kořenový objekt kolekce provázána čítače.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
