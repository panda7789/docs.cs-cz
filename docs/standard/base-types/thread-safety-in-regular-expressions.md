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
ms.openlocfilehash: fbcaaf4942f8af1d6c1de52ff5bc11317318f319
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290886"
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpečnost vlákna v regulárních výrazech
<xref:System.Text.RegularExpressions.Regex>Samotná třída je vláknově bezpečná a neměnná (jen pro čtení). To znamená, že objekty **Regex** lze vytvořit v jakémkoli vlákně a sdílet je mezi vlákny. metody porovnání mohou být volány z libovolného vlákna a nikdy nemění žádný globální stav.  
  
 Nicméně objekty výsledků (**Match** a **MatchCollection**) vrácené **výrazem Regex** by měly být použity v jednom vlákně. I když je mnoho z těchto objektů logicky neměnný, jejich implementace mohou zpozdit výpočet některých výsledků za účelem zvýšení výkonu, a v důsledku toho volající musí serializovat přístup.  
  
 Pokud je nutné sdílet objekty výsledků **regulárního výrazu** ve více vláknech, lze tyto objekty převést na instance bezpečné pro přístup z více vláken voláním jejich synchronizovaných metod. S výjimkou enumerátorů jsou všechny třídy regulárních výrazů bezpečné pro přístup z více vláken nebo mohou být převedeny na objekty bezpečné pro přístup z více vláken synchronizované metodou.  
  
 Enumerátory jsou jedinou výjimkou. Aplikace musí serializovat volání enumerátorů kolekcí. Pravidlem je, že pokud kolekci lze vytvořit ve více než jednom vlákně, je třeba synchronizovat metody enumerátoru v kořenovém objektu kolekce prochází enumerátorem.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy .NET](regular-expressions.md)
