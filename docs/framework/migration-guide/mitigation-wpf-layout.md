---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457780"
---
# <a name="mitigation-wpf-layout"></a>Omezení rizik: Rozložení WPF
Rozložení ovládacích prvků WPF se může mírně změnit.  
  
## <a name="impact"></a>Dopad  
 V důsledku této změny:  
  
- Šířka nebo výška prvků může zvětšit nebo zmenšit maximálně o jeden pixel.  
  
- Umístění objektu se může pohybovat maximálně o jeden pixel.  
  
- Vystředěné prvky mohou být svisle nebo vodorovně mimo střed maximálně o jeden pixel.  
  
 Ve výchozím nastavení je toto nové rozložení povoleno pouze pro aplikace, které cílí na rozhraní .NET Framework 4.6.  
  
## <a name="mitigation"></a>Omezení rizik  
 Vzhledem k tomu, že tato změna má tendenci eliminovat oříznutí pravé nebo dolní části ovládacích prvků WPF při vysokých dpi, aplikace, které cílí na starší `<runtime>` verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6, se mohou přihlásit do tohoto nového chování přidáním následujícího řádku do části souboru app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikace, které cílí na rozhraní .NET Framework 4.6, ale chtějí, aby se `<runtime>` ovládací prvky WPF vykreslovali pomocí předchozího algoritmu rozložení, tak mohou provést přidáním následujícího řádku do části souboru app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
