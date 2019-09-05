---
title: Výsledky dotazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: d43ec0cdf5b5bb03854dffc7132dddb4c9ae76fd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249264"
---
# <a name="query-results"></a>Výsledky dotazu
Až se LINQ to Entities dotaz převede na stromy příkazů a spustí se, výsledky dotazu se obvykle vrátí jako jedna z následujících:  
  
- Kolekce nula nebo více typových objektů entit nebo projekce komplexních typů v koncepčním modelu.  
  
- Typy CLR podporované koncepčním modelem.  
  
- Vložené kolekce.  
  
- Anonymní typy.  
  
 Při spuštění dotazu proti zdroji dat jsou výsledky vyhodnoceny do typů CLR a vráceny klientovi. Všechny materializování objektů provádí [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Všechny chyby, které jsou výsledkem neschopnosti mapování mezi [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] a CLR, způsobí, že budou výjimky vyvolány během materializace objektu.  
  
 Pokud spuštění dotazu vrátí primitivní typy konceptuálního modelu, výsledky se skládají z typů CLR, které jsou samostatné a odpojené od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Nicméně pokud dotaz vrátí kolekci typových objektů entit reprezentovaných <xref:System.Data.Objects.ObjectQuery%601>, tyto typy jsou sledovány kontextem objektu. Chování všech objektů (například podřízené/nadřazené kolekce, sledování změn, polymorfismus atd [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].) je definováno v. Tato funkce se dá použít v její kapacitě, jak je definováno [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]v. Další informace naleznete v tématu [práce s objekty](../working-with-objects.md).  
  
 Typy struktury vrácené dotazy (například anonymní typy a komplexní typy s možnou hodnotou null) můžou `null` mít hodnotu. Vlastnost vrácené entity může `null` mít také hodnotu. <xref:System.Data.Objects.DataClasses.EntityCollection%601> To může být způsobeno tím, že prochází vlastnost kolekce entity, která `null` má hodnotu, například volání <xref:System.Linq.Queryable.FirstOrDefault%2A> na objekt <xref:System.Data.Objects.ObjectQuery%601> , který nemá žádné prvky.  
  
 V některých situacích se může zobrazit dotaz, který během provádění vygeneruje materializující výsledek, ale dotaz se spustí na serveru a v modulu CLR nebude nikdy materializovat objekt entity. To může způsobit problémy, pokud závisíte na vedlejších účincích objektu materializace.  
  
 Následující příklad obsahuje vlastní třídu `MyContact` `LastName` s vlastností. Když je `count` vlastnost nastavena, je zvýšena proměnná. `LastName` Při spuštění dvou následujících dotazů se první dotaz zvýší `count` , zatímco druhý dotaz nebude. Důvodem je to, že ve druhém dotazu `LastName` se vlastnost prochází z výsledků `MyContact` a třída se nikdy nevytvoří, protože není nutné spouštět dotaz na Storu.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
