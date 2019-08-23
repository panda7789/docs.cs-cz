---
title: Procedurální pracovní postupy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956107"
---
# <a name="procedural-workflows"></a>Procedurální pracovní postupy
Procedurální pracovní postupy používají metody řízení toku podobné těm, které byly nalezeny v procedurálních jazycích. Tyto konstrukce zahrnují `While` a `If`. Tyto pracovní postupy mohou být volně tvořeny pomocí jiných aktivit řízení toku <xref:System.Activities.Statements.Flowchart> , <xref:System.Activities.Statements.Sequence>jako jsou a.  
  
## <a name="controlling-execution-flow"></a>Řízení toku spuštění  
 Knihovna aktivit pracovního postupu obsahuje aktivity pro modelování většiny metod řízení toku používaných v procedurálních jazycích. Zde jsou některé z nich:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Pracovní postupy vývojového diagramu](flowchart-workflows.md)
