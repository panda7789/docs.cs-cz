---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 3e08a2d11e815248d0fe73f804e9ef7edb7c04da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126115"
---
# <a name="mitigation-wpf-layout"></a>Omezení rizik: Rozložení WPF
Rozložení ovládacích prvků WPF se může mírně měnit.  
  
## <a name="impact"></a>Dopad  
 V důsledku této změny:  
  
- Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.  
  
- Umístění objektu lze přesunout o jeden pixel.  
  
- Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.  
  
 Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.  
  
## <a name="mitigation"></a>Zmírnění  
 Vzhledem k tomu, že tato změna je v úmyslu zabránit tomu, aby se vyloučilo oříznutí pravé nebo dolní části ovládacích prvků WPF s vysokou dpi, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou na toto nové chování přihlásit přidáním následujícího řádku do @no část __t_0_ souboru App. config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikace, které cílí na .NET Framework 4,6, ale chtějí, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` oddílu souboru App. config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6.md)
