---
title: Procedurální pracovní postupy
description: V prostředí Workflow Foundation používají procedurální pracovní postupy metody řízení toku podobné těm, které byly nalezeny v procedurálních jazycích.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 97664c1352928e7d05c2ed15fc118dd21474cfc3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421433"
---
# <a name="procedural-workflows"></a>Procedurální pracovní postupy
Procedurální pracovní postupy používají metody řízení toku podobné těm, které byly nalezeny v procedurálních jazycích. Tyto konstrukce zahrnují `While` a `If` . Tyto pracovní postupy mohou být volně tvořeny pomocí jiných aktivit řízení toku, jako jsou <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence> .  
  
## <a name="controlling-execution-flow"></a>Řízení toku spuštění  
 Knihovna aktivit pracovního postupu obsahuje aktivity pro modelování většiny metod řízení toku používaných v procedurálních jazycích. Tady jsou některé z nich:  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 Chcete-li používat aktivity řízení toku, přetáhněte je z panelu nástrojů **aktivity** do složené aktivity uvnitř okna návrháře.  
  
> [!NOTE]
> Pokud používáte funkce hostování Windows serveru AppFabric k hostování pracovních postupů ve webové farmě, technologie AppFabric přesune instance mezi různými servery AppFabric. To vyžaduje, aby se prostředky mohly sdílet mezi všemi uzly.  Žádná z výchozích aktivit pracovního postupu NET 4 neobsahuje žádné operace, které přistupují k místním prostředkům. Vzhledem k tomu, že technologie AppFabric nenabízí žádný mechanismus pro označení pracovního postupu jako nemovitého, nemůže vývojář vytvořit vlastní aktivity, které selžou při přesunu pracovního postupu.  
  
## <a name="see-also"></a>Viz také

- [Pracovní postupy vývojového diagramu](flowchart-workflows.md)
