---
title: Provádění vlastních operací spojování
description: Postup provádění vlastních operací spojování.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: df80f4382ad5fa96fcdc41b338cbb53a3d8e6cb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [join – klauzule](../language-reference/keywords/join-clause.md)  
 [Řazení výsledků klauzule join](order-the-results-of-a-join-clause.md)
