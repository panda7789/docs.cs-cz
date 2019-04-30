---
title: Interval obnovování zámku hostitele
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 91d83259c766120f7e3ffc9e49f1cf1b18c32a18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945610"
---
# <a name="host-lock-renewal-period"></a>Interval obnovování zámku hostitele
**Interval obnovování zámku hostitele** vlastnost Store Instance pracovního postupu SQL umožňuje určit časové období, ve kterém hostitele se tato možnost obnoví platnost zámku na instanci pracovního postupu. Zámek zůstává v platnosti pro interval obnovování zámku hostitele + 30 sekund. Pokud se nepovede obnovit zámek hostitele (jinými slovy, prodloužit zapůjčení) do během tohoto období vyprší platnost zámku a odemkne instanci poskytovatele trvalého chování. Hodnota této vlastnosti je typu TimeSpan ve formátu "hh: mm:". Minimální povolená hodnota je "00: 00:01" (1 sekundu). Výchozí hodnota této vlastnosti je "00: 00:30" (30 sekund).  
  
 Tato vlastnost je rozhodující pro scénáře, kde hostitele služby pracovního postupu nezdaří předtím, než ho odemknout instanci služby pracovního postupu, který ho vlastní. V tomto scénáři poskytovatele trvalého chování odebrat zámek na instanci pracovního postupu služby databáze stálost po vypršení platnosti zámek, takže můžete získat další hostitele služby pracovního postupu spuštěné na stejném počítači nebo jiný počítač v serverové farmě Zamknout a načíst do paměti pokračovat v jeho provádění od posledního trvalého stavu instance pracovního postupu služby.  
  
 Nastavení vyšší hodnoty této vlastnosti způsobí, že pracovní postup instance služby uzamčení databáze trvalosti delší dobu a proto zpoždění obnovení instance z posledního bodu trvalosti. Nastavení během krátkého intervalu k této vlastnosti způsobí, že se nové instance hostitele služby pracovního postupu ke sbírání instance služby pracovního postupu se nezdařilo rychle, ale způsobí, že nárůst v úloze pro hostitele služby pracovního postupu a databázi serveru SQL Server.  
  
 Store Instance pracovního postupu SQL spouští interní úlohy, která pravidelně probudí a instance s vypršenou platností zámky na nich zjistí. Při nalezení instance s vypršenou platností zámky, umístí instance v tabulce RunnableInstances tak, aby hostitele pracovního postupu můžete pokračovat a spustit tyto instance.
