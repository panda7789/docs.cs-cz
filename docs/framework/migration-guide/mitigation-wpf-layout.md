---
title: 'Omezení rizik: Rozložení WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c261a025548b2d22f6df3051dbcdb637723d4324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599474"
---
# <a name="mitigation-wpf-layout"></a>Omezení rizik: Rozložení WPF
Rozložení ovládacích prvků WPF může mírně změnit.  
  
## <a name="impact"></a>Dopad  
 V důsledku této změny:  
  
- Šířka nebo výška prvků může zvětšovat a zmenšovat podle maximálně jeden pixel.  
  
- Umístění objektu lze přesunout maximálně jeden pixel.  
  
- Elementy na střed lze vertikálně nebo horizontálně vypnout Centrum maximálně jeden pixel.  
  
 Ve výchozím nastavení je toto nové rozložení povoleny pouze pro aplikace, které cílí rozhraní .NET Framework 4.6.  
  
## <a name="mitigation"></a>Zmírnění  
 Vzhledem k tomu, že tato změna se obvykle Chcete-li odstranit výstřižek pravé nebo dolní ovládacích prvků WPF na vysokou dpi, aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6 můžete začít používat toto nové chování tak, že přidáte následující řádek, který `<runtime>` část souboru app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Aplikace, které cílí rozhraní .NET Framework 4.6, ale chcete ovládacích prvků WPF k vykreslení pomocí algoritmu předchozí rozložení můžete udělat tak, že přidáte následující řádek, který `<runtime>` část souboru app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
