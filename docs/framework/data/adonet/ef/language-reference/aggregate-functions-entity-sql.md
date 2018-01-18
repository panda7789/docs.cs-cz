---
title: "Agregační funkce (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1ed9a7532269a149f6f522e8fe9c6161e1aae27
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-functions-entity-sql"></a>Agregační funkce (entita SQL)
Agregace je jazyk konstruktor, který zestruční jako součást skupiny operace kolekci do skalární hodnota. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]agregace má ve dvou formách:  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Kolekce funkcí, které je možné použít kdekoli výrazu. To zahrnuje použití agregačních funkcí ve projekce a predikáty, které fungují u kolekcí. Funkce kolekce je preferovaným režimem zadávání agregací ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
-   Skupiny agregace ve výrazech dotazů, které mají klauzule GROUP BY. Jako v [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], skupiny agregace přijmout DISTINCT a všechny jako modifikátory agregační vstupu.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Nejprve se pokusí interpretovat výraz jako funkce kolekce a Pokud výraz v kontextu výrazu, vyberte ji interpretuje jako skupiny agregace.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]definuje speciální agregační operátor s názvem [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Tento operátor umožňuje získat odkaz na sadu seskupené vstupní. To umožňuje pokročilejší seskupení dotazů, kde lze v místech než agregační skupiny nebo kolekce funkce výsledky v klauzuli GROUP BY.  
  
## <a name="collection-functions"></a>Kolekce funkcí  
 Kolekce funkcí pracovat kolekce a vrátit skalární hodnotu. Například pokud `orders` je kolekce všech `orders`, můžete vypočítat nejdřívější datum expedice s následující výraz:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agreguje skupiny  
 Skupiny agregace jsou vypočteny přes výsledku skupinu podle definice v klauzuli GROUP BY. V klauzuli GROUP BY oddíly dat do skupin. Pro každou skupinu ve výsledku se použije agregační funkce a samostatné agregace se vypočítává pomocí elementů v každé skupině jako vstupy pro agregační výpočtu. Když klauzule GROUP BY se používá ve výrazu SELECT, pouze seskupování názvy výrazů, agregací nebo konstantní výrazy může být k dispozici v projekci, s, nebo klauzule ORDER.  
  
 Následující příklad vypočítá průměrné množství řazení pro každý produkt.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Je možné, že ve výrazu vyberte skupinu agregační bez explicitní klauzule GROUP BY. Všechny elementy bude považována za jednu skupinu ekvivalentní v případě zadání seskupení založené na konstanta.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Pomocí stejného oboru rozlišení názvů, který staly viditelnými pro výraz klauzule WHERE se vyhodnotí výrazy použitého v klauzuli GROUP BY.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
