---
title: Výsledky dotazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 165fb1524daa781c29037bf1c9cb2b3013504177
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539746"
---
# <a name="query-results"></a>Výsledky dotazu
Po LINQ to Entities dotazu je převést na stromy příkazů a spuštěn, výsledky dotazu jsou obvykle vráceny jako jeden z následujících akcí:  
  
- Kolekce nulu nebo více objektů zadané entity nebo projekce komplexních typů v konceptuálním modelu.  
  
- Typy CLR podporované v konceptuálním modelu.  
  
- Vložené kolekce.  
  
- Anonymní typy.  
  
 Při spuštění dotazu na zdroji dat jsou výsledky vyhodnocena na typy CLR a vrácen do klienta. Všechny materializace objektů provádí [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Všechny chyby, které jsou výsledkem nemožností mapování mezi [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] a způsobí, že modul CLR výjimky, která je vyvolána během materializace objektů.  
  
 Pokud spuštění dotazu vrátí typy konceptuálních modelů primitivní, výsledky skládat z typů CLR, které jsou samostatné a odpojen od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Nicméně pokud dotaz vrací kolekce objektů zadané entity, reprezentovaný <xref:System.Data.Objects.ObjectQuery%601>, tyto typy jsou sledovány objektem kontextu objektu. Chování všech objektů (například kolekce podřízený/nadřazený prvek, sledování změn, polymorfismus a tak dále) jsou definované v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Tato funkce je možné v jeho kapacitě, jak jsou definovány v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [práce s objekty](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Typy struktury, které jsou vráceny z dotazů (třeba anonymní typy a komplexní typy s možnou hodnotou Null) mohou být `null` hodnotu. <xref:System.Data.Objects.DataClasses.EntityCollection%601> Vlastnosti vrácenou entitu mohou také být `null` hodnotu. To může být následek projekci vlastnost kolekce entity, která má `null` hodnotu, například volání <xref:System.Linq.Queryable.FirstOrDefault%2A> na <xref:System.Data.Objects.ObjectQuery%601> , který neobsahuje žádné prvky.  
  
 V určitých situacích dotazu se může zdát generovat materializovaná výsledek během svého provádění, ale dotazu se provede na serveru a objekt entity se nikdy materializace v CLR. To může způsobit potíže, pokud jsou v závislosti na vedlejší účinky materializace objektů.  
  
 Následující příklad obsahuje třídu vlastního `MyContact`, s `LastName` vlastnost. Když `LastName` je vlastnost nastavena, `count` proměnné se zvýší. Pokud spustíte dvě následující dotazy, se zvýší první dotaz `count` během druhého dotazu se tak nestane. Důvodem je, že v druhý dotaz `LastName` vlastnost je předpokládané ve výsledcích a `MyContact` třídy nikdy vytvořen, protože není to nutné k provedení dotazu ve storu.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
