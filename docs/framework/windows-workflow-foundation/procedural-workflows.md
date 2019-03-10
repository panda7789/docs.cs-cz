---
title: Procedurální pracovní postupy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: fcf50296a8ce3e7e2e0631057467af8a8efd9215
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715708"
---
# <a name="procedural-workflows"></a>Procedurální pracovní postupy
Procedurální pracovní postupy používající řízení toku metody podobné těm v jazycích procedury. Tyto konstrukce obsahují `While` a `If`. Tyto pracovní postupy mohou být složené volně, například pomocí další aktivity toku řízení <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Řízení toku provádění  
 Knihovna aktivit pracovního postupu má aktivity pro modelování Většina metod řízení toku procedury jazyků. Zde jsou některé z nich:  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Použití aktivity toku řízení přetažení z **aktivity** nástrojů do složených aktivit uvnitř okna návrháře.  
  
> [!NOTE]
>  Pokud se používá [!INCLUDE[dublin](../../../includes/dublin-md.md)] hostitele pracovní postupy ve webové farmě, AppFabric přesune instance mezi různými servery AppFabric. To vyžaduje, že prostředky budou moct sdílet mezi všemi uzly.  Žádný výchozí aktivity pracovního postupu NET 4 neobsahuje žádné operace, které přístup k místním prostředkům. Protože AppFabric nenabízí každý použitý mechanizmus k označení pracovního postupu jako nemovitostí, vývojář nesmí vytvořit vlastní aktivity, které nesplní při přesunu pracovní postup.  
  
## <a name="see-also"></a>Viz také:
- [Pracovní postupy vývojového diagramu](flowchart-workflows.md)
