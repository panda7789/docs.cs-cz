---
title: "Procedurální pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10cf83264fbdc2ed3dc088c11865c630c0b8f4f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="procedural-workflows"></a>Procedurální pracovních postupů
Procedurální pracovní postupy používající řízení toku metody, které jsou podobné těm, které jsou součástí procedurální jazyky. Tyto konstrukce obsahují `While` a `If`. Tyto pracovní postupy můžete volně sestavit pomocí jiné aktivity toku řízení, jako třeba <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Řízení toku provádění  
 Knihovna aktivit pracovního postupu má aktivity pro modelování většinu metod řízení toku procedurální jazyků. Mezi ně patří:  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Pokud chcete používat aktivity toku řízení, přetažení z **aktivity** nástrojů do složených aktivit v okně návrháře.  
  
> [!NOTE]
>  Pokud se používá [!INCLUDE[dublin](../../../includes/dublin-md.md)] pracovní postupy hostitele ve webové farmě, AppFabric přesune mezi různými servery AppFabric instancí. To vyžaduje, aby mohly být sdílen mezi všemi uzly prostředky.  Žádný výchozí aktivity pracovního postupu NET 4 neobsahuje žádné operace, které přístup k místním prostředkům. Vzhledem k tomu, že AppFabric nenabízí žádné mechanismus označit jako nejširší pracovní postup, nesmí vývojář vytvořit vlastní aktivity, které nesplní, když je přesunut pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Pracovní postupy vývojového diagramu](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
