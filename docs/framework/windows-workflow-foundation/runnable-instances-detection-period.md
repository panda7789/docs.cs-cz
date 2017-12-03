---
title: "Období detekce spustitelného instancí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18b016cdf51ec95ab8457ded2949b980fc66fad0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="runnable-instances-detection-period"></a>Období detekce spustitelného instancí
Ukládání Instance pracovního postupu SQL spustí interní úloh, která pravidelně probudí a zjistí spustitelného nebo activatable instancí v databázi trvalost. **Spustitelného období zjišťování instancí** vlastnost úložiště Instance pracovního postupu SQL určuje časové období, po jejímž uplynutí ukládání Instance pracovního postupu SQL spustí úlohu detekce ke zjištění všech spustitelného nebo activatable pracovního postupu instance v databázi trvalost předchozího cyklu zjišťování.  
  
 Nastavení kratší interval pro tuto vlastnost zkracuje dobu mezi vypršení platnosti časovač přidružený instanci pracovního postupu a signalizace událostí a následné načítání instance. Však také zvyšuje zatížení na hostiteli a nemusí být žádoucí ve scénářích, kde jsou výjimečných trvanlivý časovače nebo selhání hostitele. Typ vlastnosti je časový interval a hodnota vlastnosti odpovídá formátu: hh: mm:. Minimální hodnota této vlastnosti je 00:00:01. Výchozí hodnota pro vlastnost je 00:00:05.  
  
 Další informace najdete v zjišťování a aktivace instance pracovního postupu spustitelného a activatable [Instance aktivace](../../../docs/framework/windows-workflow-foundation/instance-activation.md).
