---
title: Řešení přetížení funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034174"
---
# <a name="function-overload-resolution-entity-sql"></a>Řešení přetížení funkce (Entity SQL)
Toto téma popisuje, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkce jsou vyřešeny.  
  
 Se stejným názvem, lze definovat více než jednu funkci, za předpokladu funkce máte podpisů jedinečný.  
  
 Pokud je to tento případ, se musí určit funkci, která odkazuje výraz použít následující kritéria. Tato kritéria se použijí v uvedeném pořadí. První kritérium, které se vztahuje pouze na jedné funkce je vyřešení funkce.  
  
1. **Číslo parametru**. Funkce má stejný počet parametrů zadaných ve výrazu.  
  
2. **Přesná shoda podle typu**. Typ každého argumentu funkce přesně odpovídá typu parametru nebo je literál s hodnotou null.  
  
3. **Se vyhledala shoda podle podtyp**. Typ každého argumentu funkce přesně odpovídá nebo je podtyp typu parametru nebo argument je literál s hodnotou null. V případě, že několik funkce se liší pouze v čísla převody dílčí typ nejde, funkce s nejmenší počet převody dílčí typ je vyřešení funkce.  
  
4. **Se vyhledala shoda podle typu nebo podtypu povýšení**. Typ každého argumentu funkce přesně odpovídá, je dílčí typ nebo může být povýšen na typ parametru nebo argument je literál s hodnotou null. Znovu v události, ke které několik funkcí se liší pouze v počtu dílčí typ převody a propagačních akcí, funkcí s nejmenší počet dílčí typ převody a propagační akce je vyřešení funkce.  
  
 Pokud žádná z těchto kritérií výsledkem výběru jedné funkce je nejednoznačný výraz volání funkce.  
  
 I v případě jedné funkce může být extrahována pomocí těchto pravidel, argumenty stále nemusí odpovídat parametrům. V tomto případě je vyvolána chyba.  
  
 Pro uživatelsky definované funkce definice pro vloženou funkci dotaz má přednost před i v případě, že funkce definované v modelu existuje s podpisem, který představuje lepší shodu pro uživatelem definované funkce.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
