---
title: "Provádění vlastních operací spojování"
description: "Postup provádění vlastních operací spojování."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a>Provádění vlastních operací spojování

Tento příklad ukazuje, jak provádět operace spojení, které nejsou možné pomocí `join` klauzule. Ve výrazu dotazu `join` klauzule je omezený na a optimalizováno pro equijoins, které jsou zdaleka nejběžnější typ operace spojení. Při provádění porovnávání, bude pravděpodobně vždy získáte nejlepší výkon pomocí `join` klauzule.  
  
 Ale `join` klauzuli nelze použít v následujících případech:  
  
-   Když spojení záleží na výrazu nerovnosti (jiných porovnávání).  
  
-   Když spojení záleží na více než jeden výraz rovnosti nebo nerovnosti.  
  
-   Pokud máte zavést proměnnou rozsahu dočasný pro pořadí (vnitřní) na pravé straně před provedením operace spojení.  
  
 Chcete-li provést spojení, které nejsou equijoins, můžete použít více `from` klauzule zavádět každý zdroj dat nezávisle. Potom použijte výraz predikátu v `where` klauzule pro proměnnou rozsahu pro každý zdroj. Výraz také může mít formu volání metody.  
  
> [!NOTE]
>  Nezaměňujte tento druh operace vlastní připojení s použitím více `from` klauzule pro přístup k vnitřní kolekce. Další informace najdete v tématu [klauzuli join](../language-reference/keywords/join-clause.md).  
  
## <a name="example"></a>Příklad  
 První metoda v následujícím příkladu ukazuje jednoduchý křížové spojení. Křížové spojení musí používat opatrně, protože může vést k velmi velké množství výsledků. Budou však může být užitečné v některých scénářích pro vytváření pořadí zdroje, kterými se spouštějí další dotazy.  
  
 Druhý metoda vytváří posloupnost všechny produkty, jejichž kategorie ID je uvedena v seznamu kategorií na levé straně. Všimněte si použití `let` klauzule a `Contains` metodu pro vytvoření dočasné pole. Také je možné vytvořit pole před dotaz a odstranění první `from` klauzule.  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu musí dotaz připojení dvě pořadí na základě shody klíče, které v případě pořadí vnitřní (vpravo), nelze získat před klauzuli join sám sebe. Pokud toto připojení nebyly provedeny s `join` klauzule, pak se `Split` by pak bylo metoda volána pro každý prvek. Použití více `from` klauzule umožňuje dotaz předejdete režií při volání metody opakovaných. Ale protože `join` je optimalizovaná, v tomto případě může být rychlejší než při použití více `from` klauzule. Výsledky se liší v závislosti především na tom, jak nákladné je volání metody.  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 [JOIN – klauzule](../language-reference/keywords/join-clause.md)  
 [Řazení výsledků klauzule join](order-the-results-of-a-join-clause.md)
