---
title: Interval detekce spustitelných instancí
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 9652dd811f64e5324219b8aa0700ab8219edeeb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937953"
---
# <a name="runnable-instances-detection-period"></a>Interval detekce spustitelných instancí
Store Instance pracovního postupu SQL spouští interní úlohy, která pravidelně probudí a zjistí spustitelných instancí aktivovatelné databáze trvalosti. **Období zjišťování spustitelných instancí** vlastnost Store Instance pracovního postupu SQL určuje časové období, po jejímž uplynutí Store Instance pracovního postupu SQL spustí úlohu detekce zjistit žádné spustitelné nebo aktivovatelné pracovního postupu instance databáze stálost po dokončení předchozího cyklu zjišťování.  
  
 Nastavení pro tuto vlastnost kratší interval zkracuje dobu mezi vypršení platnosti časovač přidružený k instanci pracovního postupu a signalizace události a následné načítání instance. Ale také zvyšuje zatížení na hostiteli a nemusí být žádoucí ve scénářích, kde se vyskytují jen vzácně trvalý časovačů a/nebo selhání hostitele. Typ vlastnosti je časový interval a hodnota vlastnosti má následující formát: hh: mm:. Minimální hodnota pro tuto vlastnost je 00:00:01. Výchozí hodnota pro vlastnost je 00:00:05.  
  
 Další informace o zjišťování a aktivace instance spustitelných a aktivovatelné pracovních postupů, najdete v tématu [aktivace Instance](instance-activation.md).
