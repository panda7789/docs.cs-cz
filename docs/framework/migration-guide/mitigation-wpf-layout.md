---
title: 'Omezení rizik: Rozložení WPF'
description: Naučte se zmírnit problémy, které jsou výsledkem změny v rozložení ovládacích prvků WPF, jako je umístění objektu, který přesouvá jeden pixel.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: e4e4612f7b39eefbf0e76ac86c8eb644c257ba75
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475343"
---
# <a name="mitigation-wpf-layout"></a>Omezení rizik: Rozložení WPF
Rozložení ovládacích prvků WPF se může mírně měnit.  
  
## <a name="impact"></a>Dopad  
 V důsledku této změny:  
  
- Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.  
  
- Umístění objektu lze přesunout o jeden pixel.  
  
- Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.  
  
 Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.  
  
## <a name="mitigation"></a>Omezení rizik  
 Vzhledem k tomu, že tato změna je v úmyslu zabránit tomu, aby se vyloučilo oříznutí pravé nebo dolní části ovládacích prvků WPF s vysokou dpi, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou na toto nové chování zúčastnit přidáním následujícího řádku do `<runtime>` oddílu app.config souboru:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikace cílené na .NET Framework 4,6, ale chcete, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` části app.config souboru:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
