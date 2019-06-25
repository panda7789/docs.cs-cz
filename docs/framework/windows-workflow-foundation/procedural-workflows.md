---
title: Procedurální pracovní postupy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 15ff155fb057c4c10663d383a8942108c6e4375c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348371"
---
# <a name="procedural-workflows"></a>Procedurální pracovní postupy
Procedurální pracovní postupy používající řízení toku metody podobné těm v jazycích procedury. Tyto konstrukce obsahují `While` a `If`. Tyto pracovní postupy mohou být složené volně, například pomocí další aktivity toku řízení <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Řízení toku provádění  
 Knihovna aktivit pracovního postupu má aktivity pro modelování Většina metod řízení toku procedury jazyků. Zde jsou některé z nich:  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 Použití aktivity toku řízení přetažení z **aktivity** nástrojů do složených aktivit uvnitř okna návrháře.  
  
> [!NOTE]
>  Pokud používáte funkce sady Windows Server AppFabric hostování pracovních postupů hostitele ve webové farmě, přesune AppFabric instance mezi různými servery AppFabric. To vyžaduje, že prostředky budou moct sdílet mezi všemi uzly.  Žádný výchozí aktivity pracovního postupu NET 4 neobsahuje žádné operace, které přístup k místním prostředkům. Protože AppFabric nenabízí každý použitý mechanizmus k označení pracovního postupu jako nemovitostí, vývojář nesmí vytvořit vlastní aktivity, které nesplní při přesunu pracovní postup.  
  
## <a name="see-also"></a>Viz také:

- [Pracovní postupy vývojového diagramu](flowchart-workflows.md)
