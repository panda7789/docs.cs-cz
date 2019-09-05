---
title: Agregační funkce (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: c79071e73763b56c0dde906499f3eef1d296ce0c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251340"
---
# <a name="aggregate-functions-entity-sql"></a>Agregační funkce (Entity SQL)
Agregace je jazyková konstrukce, která rozhustí kolekci na skalární jako součást operace skupiny. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]agregace se přidávají ve dvou formách:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)]funkce kolekce, které mohou být použity kdekoli ve výrazu. To zahrnuje použití agregačních funkcí v projekcích a predikátech, které fungují na kolekcích. Funkce kolekce jsou preferovaným režimem určení agregací v [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
- Agregace skupin ve výrazech dotazů, které mají klauzuli GROUP BY Podobně jako v jazyce Transact-SQL přijímají agregace skupin DISTINCT a ALL jako modifikátory do agregovaného vstupu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Nejprve se pokusí interpretovat výraz jako funkci kolekce a pokud je výraz v kontextu výrazu SELECT, je interpretován jako agregace skupiny.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]definuje speciální agregační operátor s názvem [GROUPPARTITION](grouppartition-entity-sql.md). Tento operátor vám umožní získat odkaz na seskupenou vstupní sadu. To umožňuje pokročilejší dotazování seskupení, kde výsledky klauzule GROUP BY lze použít na místech jiných než agregačních nebo agregačních funkcí.  
  
## <a name="collection-functions"></a>Funkce kolekce  
 Funkce kolekce pracuje na kolekcích a vrací skalární hodnotu. Například pokud `orders` je kolekce všech `orders`, můžete vypočítat nejbližší datum expedice následujícím výrazem:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agregace skupin  
 Agregace skupin se počítají na základě skupinového výsledku definovaného klauzulí GROUP BY. Klauzule GROUP BY seskupuje data do skupin. Pro každou skupinu ve výsledku se použije agregační funkce a samostatná agregace se vypočítává pomocí prvků v každé skupině jako vstupů do agregačního výpočtu. Pokud je ve výrazu SELECT použita klauzule GROUP BY, mohou být v klauzuli projekce, HAVING nebo ORDER BY přítomny pouze názvy výrazů seskupení, agregace nebo konstantní výrazy.  
  
 Následující příklad vypočítá průměrné množství objednaného pro každý produkt.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Je možné mít agregovanou skupinu bez explicitní klauzule GROUP BY ve výrazu SELECT. Všechny elementy budou považovány za jednu skupinu, která odpovídá případu zadání seskupení na základě konstanty.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Výrazy používané v klauzuli GROUP BY jsou vyhodnocovány pomocí stejného oboru překladu názvů, který by byl viditelný pro výraz klauzule WHERE.  
  
## <a name="see-also"></a>Viz také:

- [Funkce](functions-entity-sql.md)
