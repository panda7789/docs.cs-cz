---
title: "Rozlišení přetížení funkce (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3a303ca917a9f6cfee42d11456a1f80b52ffd2ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="function-overload-resolution-entity-sql"></a>Rozlišení přetížení funkce (entita SQL)
Toto téma popisuje, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkce jsou vyřešeny.  
  
 Se stejným názvem, lze definovat více než jednu funkci, tak dlouho, dokud funkce mít jedinečné podpisy.  
  
 Pokud to tento případ, musí provést následující kritéria k určení, funkci, která odkazuje daném výrazu. Tato kritéria použijí v uvedeném pořadí. První kritérium, které se vztahují pouze k jedné funkce je vyřešen funkce.  
  
1.  **Parametr číslo**. Funkce má stejný počet parametrů zadaný ve výrazu.  
  
2.  **Přesná shoda podle typu**. Každý typ argumentu funkce přesně odpovídá typ parametru, nebo je literál null.  
  
3.  **Shoda podle dílčí**. Každý typ argumentu funkce přesně odpovídá nebo je typu dílčí parametr typu nebo argument je literál null. V případě, že několik funkcí se liší pouze v počet dílčí typ převody vyžadovaných, funkce se nejmenší počet převody dílčí typ je vyřešen funkce.  
  
4.  **Shoda podle dílčí nebo typu povýšení**. Každý typ argumentu funkce přesně odpovídá, je dílčí typ nebo můžete zvýšit na typ parametru nebo argument je literál null. Znovu, v případě, že několik funkcí liší pouze v počtu dílčí typ převody a reklamními nabídkami, funkce se nejmenší počet dílčí typ převody a reklamními nabídkami je vyřešen funkce.  
  
 Pokud žádná z těchto kritérií výsledek v jedné vybrat funkce, je výraz volání funkce nejednoznačný.  
  
 I v případě jedné funkce lze extrahovat pomocí těchto pravidel, argumenty stále nemusí odpovídat parametrům. V takovém případě je vyvolána chyba.  
  
 Pro uživatelsky definované funkce definici vložená funkce dotazu má přednost před i v případě, že funkce definované v modelu existuje podpisem, který představuje lepší shodu pro uživatelsky definované funkce.  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
