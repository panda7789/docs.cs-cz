---
title: Agregační funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: b01c7dca675e79c61b87bcc1fb30455286db3118
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489960"
---
# <a name="aggregate-functions-entity-sql"></a>Agregační funkce (Entity SQL)
Agregace je konstrukce jazyka, který zestruční kolekce do skaláru jako součást operace skupiny. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] agregace přicházet ve dvou formách:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Kolekce funkcí, které může je použít kdekoli ve výrazu. To zahrnuje použití agregačních funkcí v projekce a predikátů, které fungují na kolekcích. Kolekce funkcí jsou preferovaný způsob určení agregace v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
- Skupina agregace ve výrazech dotazů, které mají klauzuli Group by. Stejně jako v jazyce Transact-SQL přijměte agregace skupiny DISTINCT a všechny jako modifikátory agregační vstupem.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Nejprve se pokusí o interpretovat výraz jako funkce kolekce a Pokud výraz v kontextu výrazu SELECT ji interpretuje jako agregace skupiny.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] definuje speciální agregační operátor volá [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Tento operátor umožňuje získat odkaz na seskupené vstupní sady. To umožňuje pokročilejší seskupení dotazů, kde lze použít výsledky v klauzuli GROUP BY v jiných míst než agregace skupiny nebo kolekce funkcí.  
  
## <a name="collection-functions"></a>Kolekce funkcí  
 Kolekce funkcí pracovat s kolekcí a vracet skalární hodnotu. Například pokud `orders` je kolekce všech `orders`, můžete vypočítat datum příjemce se následující výraz:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agregace skupiny  
 Agregace skupiny se počítá za výsledek skupiny definované v klauzuli GROUP BY. V klauzuli GROUP BY dělí data do skupin. Pro každou skupinu ve výsledku se použije agregační funkce a samostatné agregace se počítá pomocí elementů v každé skupině jako vstupy do agregačního výpočtu. Když klauzule GROUP BY se používá ve výrazu SELECT, seskupení pouze názvy výrazů, agregace nebo konstantní výrazy může být k dispozici v projekci s, nebo ORDER BY – klauzule.  
  
 Následující příklad vypočítá průměrné množství, řazení pro jednotlivé produkty.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Je možné mít ve výrazu vyberte skupinu agregační bez explicitní klauzule GROUP BY. Všechny prvky bude považována za jednu skupinu ekvivalentní případu pro určení seskupení založené na konstantu.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Výrazy v klauzuli GROUP BY vyhodnocují se pomocí stejného oboru rozlišení názvů, které se staly viditelnými pro výraz klauzule WHERE.  
  
## <a name="see-also"></a>Viz také:

- [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
