---
title: "Výsledky dotazu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5ff674cbbe0a5d52a4bc4b4de55e0ae3c49395d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="query-results"></a>Výsledky dotazu
Po [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu je převést na strom příkazů a provést, výsledky dotazu jsou obvykle vrátí jako jednu z následujících:  
  
-   Kolekce nula nebo více objektů zadané entity nebo projekci komplexních typů v konceptuálním modelu.  
  
-   Typy CLR podporované v konceptuálním modelu.  
  
-   Vložené kolekce.  
  
-   Anonymní typy.  
  
 Pokud se má spustit dotaz na zdroji dat, jsou výsledky vyhodnocena do typy CLR a vrácen do klienta. Všechny materialization objektu provádí [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Všechny chyby, které jsou výsledkem nebylo možné mezi [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] a způsobí, že modulu CLR výjimky vyvolání během materialization objektu.  
  
 Pokud spuštění dotazu vrátí konceptuálního modelu primitivní typy, výsledky obsahovat typů CLR, které jsou samostatné a odpojená od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Ale pokud dotaz vrátí kolekci objektů zadané entity, reprezentována <xref:System.Data.Objects.ObjectQuery%601>, tyto typy jsou sledovány objektem do kontextu objektu. Všechny chování objektu (například podřízeného nebo nadřazeného kolekcí, sledování změn, polymorfismus a tak dále) jsou definované v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Tato funkce mohou být používány své kapacity, jak jsou definovány v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [práce s objekty](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Struktura typy vráceny z dotazů (například anonymní typy a komplexní typy s možnou hodnotou Null) můžou být `null` hodnotu. <xref:System.Data.Objects.DataClasses.EntityCollection%601> Vlastnost vrácenou entitu může být také z `null` hodnotu. To může být důsledkem projekce vlastnost kolekce entita, která je `null` hodnotu, jako je například volání <xref:System.Linq.Queryable.FirstOrDefault%2A> na <xref:System.Data.Objects.ObjectQuery%601> , nemá žádné elementy.  
  
 V některých situacích může zdát, že dotaz Generovat výsledku materializovaného během jejího provádění, ale dotaz bude proveden na serveru a objekt entity se nikdy vyžaduje v modulu CLR. To může způsobit problémy, pokud jsou v závislosti na vedlejší účinky materialization objektu.  
  
 Následující příklad obsahuje vlastní třídu, `MyContact`, s `LastName` vlastnost. Když `LastName` je vlastnost nastavena, `count` proměnné se zvýší. Pokud spustíte dvě následující dotazy, se zvýší první dotaz `count` při druhého dotazu není. Důvodem je, že v druhé dotazu `LastName` vlastnost se promítá z výsledků a `MyContact` třída je nikdy vytvořit, protože není potřeba provést dotaz na úložiště.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
