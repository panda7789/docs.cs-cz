---
title: 'Postupy: Měření výkonu dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: f240b2c275305aec5699eb42406e0689925490a8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288183"
---
# <a name="how-to-measure-plinq-query-performance"></a>Postupy: Měření výkonu dotazu PLINQ

Tento příklad ukazuje, jak použít <xref:System.Diagnostics.Stopwatch> třídu k měření času, který je potřeba pro spuštění dotazu PLINQ.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je použita prázdná `foreach` smyčka ( `For Each` v Visual Basic) pro měření doby potřebné k provedení dotazu. Ve skutečném kódu smyčka obvykle obsahuje další kroky zpracování, které se přidávají do celkové doby provádění dotazu. Všimněte si, že Stopwatch není spuštěný, dokud není těsně před smyčkou, protože to je po zahájení provádění dotazu. Pokud potřebujete přesnější měření, můžete `ElapsedTicks` místo toho použít vlastnost `ElapsedMilliseconds` .  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Celková doba spuštění je užitečnou metrikou při experimentování s implementacemi dotazů, ale nikdy neříká celému článku. Chcete-li získat hlubší a širší pohled na interakci s vlákny dotazů mezi sebou a s jinými běžícími procesy, použijte [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
