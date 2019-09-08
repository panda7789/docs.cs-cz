---
title: Zmírnění Rozložení WPF
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d266ad33110d2bda8f7911d89981c372624c3f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779067"
---
# <a name="mitigation-wpf-layout"></a>Zmírnění Rozložení WPF
Rozložení ovládacích prvků WPF se může mírně měnit.  
  
## <a name="impact"></a>Dopad  
 V důsledku této změny:  
  
- Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.  
  
- Umístění objektu lze přesunout o jeden pixel.  
  
- Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.  
  
 Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.  
  
## <a name="mitigation"></a>Zmírnění  
 Vzhledem k tomu, že tato změna je v úmyslu eliminovat v horních Dpich ovládací prvky WPF, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou k tomuto novému chování vyjádřit přidáním následujícího řádku do `<runtime>` oddílu souboru App. config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikace cílené na .NET Framework 4,6, ale chcete, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` oddílu souboru App. config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6.md)
