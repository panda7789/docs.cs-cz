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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8f517b68695457c2819612bbd092b5ea03c5f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 [Vývojový diagram pracovních postupů](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
