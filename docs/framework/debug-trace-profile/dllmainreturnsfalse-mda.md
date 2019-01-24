---
title: dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c513ba06ac79eb3da229605120c4f59ab8d32665
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554540"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse – pomocník spravovaného ladění (MDA)
`dllMainReturnsFalse` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud spravovanou `DllMain` funkce uživatelské sestavení, volaná s důvodem DLL_PROCESS_ATTACH, vrátí hodnotu FALSE.  
  
## <a name="symptoms"></a>Příznaky  
 `DllMain` Funkce vrátila hodnotu FALSE, která udává, že ho nevykonala příkaz správně. To může způsobit problémy s neurčeném, protože `DllMain` funkce obvykle obsahují důležité inicializační kód.  
  
## <a name="cause"></a>Příčina  
 `DllMain` Volána s důvodem DLL_PROCESS_ATTACH inicializace knihovny DLL při zatížení. Pokud vrátí hodnotu FALSE, znamená to, že inicializace knihovny DLL se nezdařilo.  
  
## <a name="resolution"></a>Rozlišení  
 Analýza kódu `DllMain` funkce knihovny DLL se nezdařilo a určit příčinu selhání inicializace.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR. Pouze sestavy dat o vrácené hodnotě pro `DllMain`.  
  
## <a name="output"></a>Výstup  
 Zpráva, že `DllMain` funkci důvodem DLL_PROCESS_ATTACH, vrátila hodnotu FALSE. Všimněte si, že toto MDA aktivováno, pouze pokud `DllMain` je implementovaná ve spravovaném kódu.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
