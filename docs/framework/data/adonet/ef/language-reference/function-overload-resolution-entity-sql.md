---
title: Řešení přetížení funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 1aeebc501487a6fc443df00c24beb2bc6aa5fc49
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250924"
---
# <a name="function-overload-resolution-entity-sql"></a>Řešení přetížení funkce (Entity SQL)
Toto téma popisuje, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jak jsou funkce vyřešeny.  
  
 Více než jedna funkce může být definována se stejným názvem, pokud funkce mají jedinečné podpisy.  
  
 V takovém případě je nutné použít následující kritéria k určení, na kterou funkci odkazuje daný výraz. Tato kritéria se aplikují v pořadí. První kritérium, které platí pouze pro jednu funkci, je vyřešená funkce.  
  
1. **Číslo parametru** Funkce má stejný počet parametrů, které jsou zadány ve výrazu.  
  
2. **Přesná shoda typu** Každý typ argumentu funkce přesně odpovídá typu parametru, nebo je literál null.  
  
3. **Shoda s podtypem** Každý typ argumentu funkce přesně odpovídá nebo je dílčí typ typu parametru, nebo je argumentem nulový literál. V případě, že se několik funkcí liší pouze v případě vyžadovaných převodů dílčího typu, funkce s nejmenším počtem převodů dílčího typu je vyřešená funkce.  
  
4. **Shoda s podtypem nebo povýšením typu**. Každý typ argumentu funkce přesně odpovídá, je dílčí typ, nebo může být povýšen na typ parametru, nebo je argumentem nulový literál. V případě, že se několik funkcí liší pouze v počtu převodů dílčích typů a propagačních akcí, funkce s nejmenším počtem převodů dílčích typů a propagační akce je vyřešená funkce.  
  
 Pokud žádný z těchto kritérií nevede k výběru jedné funkce, výraz volání funkce je nejednoznačný.  
  
 I když může být jedna funkce extrahována pomocí těchto pravidel, argumenty stále nemusí odpovídat parametrům. V tomto případě se vyvolá chyba.  
  
 V případě uživatelsky definovaných funkcí má definice vložené funkce dotazu přednost i v případě, že existuje funkce definovaná modelem s podpisem, který je lepší shodou uživatelsky definované funkce.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
- [Přehled Entity SQL](entity-sql-overview.md)
- [Funkce](functions-entity-sql.md)
