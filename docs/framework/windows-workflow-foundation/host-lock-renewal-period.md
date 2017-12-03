---
title: "Interval obnovování hostitele zámku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48a5d2e1d8c5381f322ea1b6ffc9022853683efc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="host-lock-renewal-period"></a>Interval obnovování hostitele zámku
**Interval obnovování hostitele zámku** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit časové období, ve kterém hostitele obnovuje jeho zámku na instanci pracovního postupu. Zámek zůstane platný pro interval obnovování hostitele zámku + 30 sekund. Hostitel selže-li obnovit zámek (jinými slovy, prodloužit zapůjčení) během tohoto období vyprší platnost zámek a poskytovateli trvalost odemkne instance. Hodnota této vlastnosti je typu časový interval ve formátu hh: mm". Minimální povolená hodnota je "00: 00:01" (1 sekunda). Výchozí hodnota této vlastnosti je "00: 00:30" (30 sekund).  
  
 Tato vlastnost je důležité ve scénářích, kde hostitele služby pracovního postupu před selže ho můžete odemknout instance služby pracovního postupu, který ho vlastní. V tomto scénáři zprostředkovatele trvalost odebrat zámek na instanci služby pracovního postupu v databázi trvalost po vypršení platnosti zámek, takže můžete získat jiného hostitele služby pracovního postupu spuštěné na stejném počítači nebo jiný počítač v serverové farmě Zamknout a načtení instance pracovního postupu služby do paměti obnovit jeho spuštění od jeho posledního trvalého stavu.  
  
 Vyšší hodnotu pro tuto vlastnost nastavíte pracovní postup instance služby se uzamkne v databázi trvalost delší dobu a proto zpozdí obnovení instance z posledního bodu trvalost. Nastavení krátký interval pro tuto vlastnost způsobí, že nová instance hostitele služby pracovního postupu a pokračovat tam, instance služby se nezdařilo pracovního postupu rychle, ale způsobí zvýšení zatížení pro hostitele služby pracovního postupu a databázi systému SQL Server.  
  
 Ukládání Instance pracovního postupu SQL spustí interní úloh, která pravidelně probudí a zjišťuje instance s vypršenou platností zámky na nich. Pokud najde instancí s vypršenou platností zámky, umístí instance v tabulce RunnableInstances, aby mohli vyzvednutí a spusťte tyto instance hostitele pracovního postupu.
