---
title: "Omezení rizik: Rozložení WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3ba5ac792169cc076f9621025f35444281cec6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-layout"></a>Omezení rizik: Rozložení WPF
Rozložení ovládacích prvků WPF můžou trochu změnit.  
  
## <a name="impact"></a>Dopad  
 V důsledku této změny:  
  
-   Šířky nebo výšky elementů může zvětšit nebo zmenšit o maximálně jeden bod.  
  
-   Umístění objektu můžete přesunout tak, že maximálně jeden pixel.  
  
-   Zarovnaný elementy lze vypnout center o maximálně jeden bod vodorovně nebo svisle.  
  
 Ve výchozím nastavení je toto nové rozložení povolená jenom pro aplikace, které cílí na rozhraní .NET Framework 4.6.  
  
## <a name="mitigation"></a>Zmírnění  
 Vzhledem k tomu, že tato změna se obvykle eliminovat výstřižek pravé nebo dolní části ovládacích prvků WPF v vysoké DPIs, aplikace, které cílí na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6 se můžete rozhodnout do této nové chování přidáním následující řádek na `<runtime>` v souboru app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikace, které cílí na rozhraní .NET Framework 4.6 ale ovládacích prvků WPF k vykreslení pomocí předchozí algoritmus rozložení, aby se to lze provést přidáním následující řádek do `<runtime>` v souboru app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
